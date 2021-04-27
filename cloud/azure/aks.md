# Azure Kubernetes Service

# k8s 명령어

1. 배포된 deployment 의 이미지 변경
```
kubectl set image deployment/was_deployment was_pod=myacr.azurecr.io/was:latest
```
  - `deployment/was_deployment`: deployment명 명시
  - `was_pod`: 이미지를 변경할 pod명
  - `myacr.azurecr.io`: 도커 허브처럼 쓸 수 있는 Azure Container Registry
  - `was:latest`: 레포지토리 명과 태그
  - 태그명이 현재 배포되어있는 태그와 같으면 본 명령어는 수행(update)되지 않는다.
