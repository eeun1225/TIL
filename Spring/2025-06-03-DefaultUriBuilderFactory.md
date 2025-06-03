# 📚 DefaultUriBuilderFactory (2025.06.03)
___

## 🌟 오늘 배운 내용
- DefaultUriBuilderFactory
- DefaultUriBuilderFactory의 주요 기능
- 인코딩 모드 종류
- 중복 인코딩 방지
<br/>


## 🔎 요약 정리

___

### ✅ DefaultUriBuilderFactory

- Spring WebClient에서 URI를 더 유연하고 깔끔하게 만들 수 있게 도와주는 URI 생성 도구
- 주로 base URL 설정이나 공통 prefix 구성이 필요할 때 사용된다.
- `WebClient`의 기본 URI 경로를 설정한다.
- 나머지 path, query parameter 등을 builder 방식으로 조립할 수 있게 도와준다.


### ✅ 주요 기능

- `setBaseUri(String)` : 기본 URI를 지정한다.
- `setEncodingMode()` : 쿼리 파라미터 등 인코딩 방식 지정한다.
- `expand(...)` : `{}` 형태로 placeholder를 주고 값으로 치환한다.
- `path()` + `queryParam()` :  URI 경로와 쿼리 파라미터를 builder로 조립한다.



### ✅ 인코딩 모드 종류

- `TEMPLATE_AND_VALUES` : URI 템플릿을 먼저 인코딩하고 URI 변수를 적용할 때 인코딩 한다.
- `VALUES_ONLY` : URI 템플릿을 인코딩하지 않고 URI 변수를 템플릿에 적용하기 전에 엄격히 인코딩한다.
- `URI_COMPONENT` : URI 변수를 적용한 후에 URI 컴포넌트를 인코딩한다.
- `NONE` : 인코딩을 적용하지 않는다.

```java
// 인스턴스 생성
DefaultUriBuilderFactory factory = new DefaultUriBuilderFactory(BASE_URL);

// 인스턴스를 활용하여 인코딩 Mode를 설정
factory.setEncodingMode(DefaultUriBuilderFactory.EncodingMode.VALUES_ONLY);
```


### ✅ 중복 인코딩 방지

Spring Web의 `UriBuilder`, `WebClient`, `RestTemplate` 등에서 queryParam() 같은 메서드를 사용할 때, 입력 값에 `%`가 포함되어 있으면 Spring은 "이건 이미 인코딩된 값일 수도 있다"고 판단해서 자동 인코딩을 생략해준다.