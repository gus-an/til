## `@Transactional` 어노테이션

### 오해
- 함수 단위로 Exception 발생 전까지 실행했던 모든 명령어를 rollback 하는 것으로 생각했음.

### 실행 결과
- DB 관련된 트랜잭션은 rollback 이 됨.
- Class 변수는 `static`으로 선언되어도 rollback 되지 않음.
