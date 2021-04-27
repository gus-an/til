# Jenkinsfile 문법 (groovy)

## environment

- 환경변수를 넣기 위해서는 `pipeline { }` 아래에 혹은 `stage { }` 아래에 `environment { }` 를 설정한다.
- 사용할 때는 스트링 안에 escape 문자 `$`와 함께 환경변수명을 적는다.

## string

1. `sh`, `echo` 명령어를 사용할 때, `' '` 대신 `" "` 를 사용해야 escape 문자 `$`에 대한 오류가 안난다.

```
sh "docker build -t $ACR_SERVER/$ACR_REPO:build$env.BUILD_NUMBER ."
```

3. `$` 표시를 escape 문자로 사용하지 않을 경우에 escape 문자 `\`를 사용한다.

```
sh "docker rmi -f \$(docker images -q $ACR_SERVER/$ACR_REPO | head -n 1)"
```
