# Jenkinsfile 문법 (groovy)

## environment

- 환경변수를 넣기 위해서는 `pipeline { }` 아래에 혹은 `stage { }` 아래에 `environment { }` 를 설정한다.
- 사용할 때는 스트링 안에 escape 문자 `$`와 함께 환경변수명을 적는다.

```groovy
pipeline {
  environment { 
    FOO='foo'
  }
  stages {
    environment {
      BAR='bar'
    steps { 
      echo "$FOO $BAR"
    }
  }
}
```

<br>

- 환경변수를 `''` 처럼 빈값으로 설정하면, 읽어올 때 값이 존재하지 않는 에러가 발생한다.

```log
groovy.lang.MissingPropertyException: No such property: CURRENT_DEPLOY for class: groovy.lang.Binding
```


## string

- `sh`, `echo` 명령어를 사용할 때, `' '` 대신 `" "` 를 사용해야 escape 문자 `$`에 대한 오류가 안난다.

```
sh "docker build -t $ACR_SERVER/$ACR_REPO:build$env.BUILD_NUMBER ."
```

- `$` 표시를 escape 문자로 사용하지 않을 경우에 escape 문자 `\`를 사용한다.

```
sh "docker rmi -f \$(docker images -q $ACR_SERVER/$ACR_REPO | head -n 1)"
```

## if/else

- `if` 문 안에 스트링 이용이 가능하다.

```groovy
script{
    if ("$FOO"=="$BAR") {

    } else {

    }
}
```

## try/catch

- 스크립트 실행 중에 Stderr 가 발생하면 보통 배포 과정이 종료된다. 계속 진행하기 위해서는 `try` `catch` 문을 사용하면 된다.
- 아래 코드는 스크립트 성공 여부에 따라 환경변수의 값을 설정하는 부분이다.
```groovy
script {
    try {
        DEPLOY = sh (
            script: "kubectl get deployment myDeployment --no-headers -o custom-columns=':metadata.name'",
            returnStdout: true
        ).trim()
    } catch (err) {
        echo "[ERROR MESSAGE]" + err.getMessage()
    }
}
```
