# Swagger
Swagger 는 API Spec 문서를 자동화 해주는 라이브러리로 
지정한 URL들을 HTML화면으로 확인할 수 있게 해주는 프로젝트

# Swagger 설정하기
## 1. build.gradle에 의존성 추가
```
    implementation('io.springfox:springfox-swagger2:2.6.1')
    implementation('io.springfox:springfox-swagger-ui:2.6.1')
```
## 2. 프로젝트에 Swagger Config 설정 및 Bean등록
```javascript
  @Configuration
  @EnableSwagger2
  public class SwaggerConfig {

      @Bean
      public Docket api() {
          return new Docket(DocumentationType.SWAGGER_2)
                  .select()
                  .apis(RequestHandlerSelectors.any()) // 현재 RequestMapping으로 할당된 모든 URL 리스트를 추출
                  .paths(PathSelectors.ant("/api/**")) // 그중 /api/** 인 URL들만 필터링
                  .build();
      }
  }
```

 * RequestHandlerSelectors
   * any()
   * none()
   * withMethodAnnotaion()
   * withClassAnnotation()
   * basePackage()
   
## 3. Swagger 확인

localhost:8080/swagger-ui.html
