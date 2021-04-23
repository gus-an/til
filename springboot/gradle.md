- `build.gradle`에 추가만 하더라도 작동하는 코드가 있다.
  - `implementation 'org.springframework.boot:spring-boot-starter-security'` 관련 코드는 다 지웠는데도 스프링 실행할 때 security 관련 옵션이 작동한다.
  ```
  2021-04-23 09:02:04.495  INFO 29442 --- [  restartedMain] o.s.s.concurrent.ThreadPoolTaskExecutor  : Initializing ExecutorService 'applicationTaskExecutor'
  2021-04-23 09:02:04.711  INFO 29442 --- [  restartedMain] .s.s.UserDetailsServiceAutoConfiguration : 

  Using generated security password: bc6fdb81-7f03-4eea-96a7-900749020708

  2021-04-23 09:02:04.847  INFO 29442 --- [  restartedMain] o.s.s.web.DefaultSecurityFilterChain     : Will secure any request with [org.springframework.security.web.context.request.async.WebAsyncManagerIntegrationFilter@226f73a7, org.springframework.security.web.context.SecurityContextPersistenceFilter@2f068145, org.springframework.security.web.header.HeaderWriterFilter@5d409b9f, org.springframework.security.web.csrf.CsrfFilter@5700be70, org.springframework.security.web.authentication.logout.LogoutFilter@6a2eeadc, org.springframework.security.web.authentication.UsernamePasswordAuthenticationFilter@14dda6ad, org.springframework.security.web.authentication.ui.DefaultLoginPageGeneratingFilter@1baf9443, org.springframework.security.web.authentication.ui.DefaultLogoutPageGeneratingFilter@6f64e529, org.springframework.security.web.authentication.www.BasicAuthenticationFilter@66704fb1, org.springframework.security.web.savedrequest.RequestCacheAwareFilter@ca2d1d7, org.springframework.security.web.servletapi.SecurityContextHolderAwareRequestFilter@26ea9406, org.springframework.security.web.authentication.AnonymousAuthenticationFilter@b8d22b3, org.springframework.security.web.session.SessionManagementFilter@6b31cc74, org.springframework.security.web.access.ExceptionTranslationFilter@9730f16, org.springframework.security.web.access.intercept.FilterSecurityInterceptor@4f75abea]
  ```
  - `implementation` 때문일까?
