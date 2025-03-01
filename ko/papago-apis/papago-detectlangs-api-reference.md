# 언어 감지 API 레퍼런스

- [언어 감지](#언어-감지)
- [오류 코드](#오류-코드)

## 언어 감지

### 설명

입력된 텍스트가 어떤 언어로 된 텍스트인지 감지해 해당하는 언어의 언어 코드를 반환합니다.

### 요청 URL

```sh
https://openapi.naver.com/v1/papago/detectLangs
```

### 프로토콜

HTTPS

### HTTP 메서드

POST

### 파라미터

|파라미터|타입|필수 여부|설명|
|---|---|:-:|----|
|query|string|Y|어떤 언어인지 확인할 텍스트|

### 참고 사항

API를 요청할 때 다음 예와 같이 HTTP 요청 헤더에 [클라이언트 아이디와 클라이언트 시크릿](https://developers.naver.com/docs/common/openapiguide/appregister.md#클라이언트-아이디와-클라이언트-시크릿-확인)을 추가해야 합니다.

```sh
POST /v1/papago/detectLangs HTTP/1.1
> Host: openapi.naver.com
> User-Agent: curl/7.49.1
> Accept: */*
> Content-Type: application/x-www-form-urlencoded; charset=UTF-8
> X-Naver-Client-Id: {애플리케이션 등록 시 발급받은 클라이언트 아이디 값}
> X-Naver-Client-Secret: {애플리케이션 등록 시 발급받은 클라이언트 시크릿 값}
> Content-Length: 51
>
```

### 요청 예

```sh
curl "https://openapi.naver.com/v1/papago/detectLangs" \
    -d "query=만나서 반갑습니다." \
    -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
    -H "X-Naver-Client-Id: {애플리케이션 등록 시 발급받은 클라이언트 아이디 값}" \
    -H "X-Naver-Client-Secret: {애플리케이션 등록 시 발급받은 클라이언트 시크릿 값}" -v
```

### 응답

응답에 성공하면 결괏값을 JSON 형식으로 반환합니다.

|속성|타입|필수 여부|설명|
|---|---|:-:|----|
|langCode|string|Y|감지한 언에 해당하는 언어 코드.<br />1. `ko`: 한국어<br />2. `ja`: 일본어<br />3. `zh-CN`: 중국어 간체<br />4. `zh-TW`: 중국어 번체<br />5. `hi`: 힌디어<br />6. `en`: 영어<br />7. `es`: 스페인어<br />8. `fr`: 프랑스어<br />9. `de`: 독일어<br />10. `pt`: 포르투갈어<br />11. `vi`: 베트남어<br />12. `id`: 인도네시아어<br />13. `fa`: 페르시아어<br />14. `ar`: 아랍어<br />15. `mm`: 미얀마어<br />16. `th`: 태국어<br />17. `ru`: 러시아어<br />18. `it`: 이탈리아어<br />19. `unk`: 알 수 없음<br />|

### 응답 예

```json
{ "langCode" : "ko" }
```

## 오류 코드

|오류 코드|HTTP 상태 코드|오류 메세지|
|---|---|----|
|LD01|400|Empty text (text가 없습니다)|
|LD99|500|Internal server errors|
 
<div class="note"><p><strong>Internal server errors</strong></p>
<p>반환 받은 오류 메시지가 <strong>Internal server errors</strong>면 "<a href="https://developers.naver.com/forum" target="_blank">개발자 포럼</a>"에 오류를 신고해 주십시오.</p>
</div>

<div class="note"><p><strong>403 오류</strong></p>
<p>개발자 센터에 등록한 애플리케이션에서 언어 감지를 사용하도록 설정하지 않았다면 'API 권한 없음'을 의미하는 403 오류가 발생할 수 있습니다. 403 오류가 발생했다면 네이버 개발자 센터의 <strong><a href="https://developers.naver.com/apps/#/list" target="_blank">Application &gt; 내 애플리케이션</a></strong> 메뉴에서 오류가 발생한 애플리케이션의 <strong>API 설정</strong> 탭을 클릭한 다음 <strong>Papago 언어감지</strong>가 선택돼 있는지 확인해 보십시오.</p>
</div>

<div class="info"><p><strong>참고</strong></p>
<p>네이버 오픈API 공통 오류 코드는 "<a href="https://developers.naver.com/docs/common/openapiguide/" target="_blank">API 공통 가이드</a>"의 '<a href="https://developers.naver.com/docs/common/openapiguide/errorcode.md" target="_blank">오류 코드</a>'를 참고하십시오.</p>
</div>
