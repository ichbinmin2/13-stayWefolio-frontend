# 13-stayWefolio

## 프로젝트 소개
> 숙박업소를 큐레이팅하고 예약할 수 있는 사이트인 stayfolio의 주요 기능을 구현하였습니다. 

</br>
 
## 프로젝트 참가자(Front + Back)

### FrontEnd
+ 신은선(Product Manager) / **민지연** / 김보라 / 서수연

### BackEnd
+ 김지훈

</br>

## 프로젝트 기간 
**20.10.19 ~ 20.10.30** 약 2주간 진행

</br>

## 팀 Repo 링크 가기
["stayWefolio" Repo 바로가기](https://github.com/wecode-bootcamp-korea/13-stayWefolio-frontend)

</br>

## 프로젝트 영상
[영상 보러가기](https://youtu.be/qz6dKgsI0Ds)
![staywefolioscreenshot](https://user-images.githubusercontent.com/66218824/97659783-34121300-1ab3-11eb-9c92-80319daab3cf.png)

</br>

## 기술스택
### FrontEnd
- React
- Javascript
- HTML, SASS
- CRA, npm
- git
- prettier
- ESLint

### BackEnd
- Python
- Django
- MySQL

### 추가 설치 라이브러리
- slick
- react-router
- node-sass
- react-daterangepicker
- google-map-react
- font-awesome

### 협업 도구
+ Slack
+ Git + GitHub 
+ Trello 를 이용한 일정관리 및 작업 현황 확인
![staywefoliotrello](https://user-images.githubusercontent.com/66218824/97659837-56a42c00-1ab3-11eb-9580-b9c7a41123ca.png)
+ Postman (API 관리)

</br>

## 주요 기능 소개

- slick slider 라이브러리를 이용한 슬라이더 기능
- 동적 라우팅을 이용한 페이지 이동 기능
- 로그인/회원가입 기능
- 달력 기능 
- 예약 사항에 따른 금액 계산 기능
- 예약 및 예약 확인 기능
- google map API를 이용한 지도 기능

</br>

## 구현 기능(민지연)

- Role : Team Member
- Position : Front-end
- Stack : React / Javascript / Sass / Router
- Works : 
 - 디자인을 바탕으로 Component 설계CSS를 이용한 디자인 구현
 - Component 구현과 관련 API 연결
 - 로그인 - 조건식에 따른 경고 메세지 구현, 로그인 활성화 반영
 - 회원가입 - 조건식에 따른 경고 메세지 구현, toggle 버튼을 이용한 펼치기/숨기기 기능 구현, 전체동의 checkbox 자동 반영
 - Booking main - API로 받은 이미지, 텍스트 데이터 반영
 - 예약페이지 약관동의 - contents data로 분리 및 관리, map methods를 사용하여 data 렌더

</br>

## 구현 기능 상세 소개(민지연)

### 회원 가입 페이지 

![1](https://user-images.githubusercontent.com/53133662/160774374-cb808453-23c7-4827-bfa8-25d53e924dfa.gif)

- 이메일, 이름, 비밀번호, 약관 동의를 통한 회원가입 페이지입니다.
- 이메일, 이름, 비밀번호는 조건식에 따른 경고 메세지를 구현했습니다.
- 모든 입력이 완료되고, 약관 동의가 전체 체크 되었을 때 회원 가입 버튼의 커서가 활성화되도록 하였습니다.
- toggle 버튼을 이용한 펼치기/숨기기 기능을 구현했습니다.
- `onChange`를 사용하여 해당 인풋 값을 입력하면 `value`가  `name` 값으로 업데이트 되고, 회원가입 버튼을 클릭하면 `body`에 각각의 `state`를 값을 담아 `post` 로 서버에 요청을 합니다.
- 응답 메세지가 "SUCCESS"일 경우에만 `history.push` 로 메인페이지로 다시 이동할 수 있습니다.

</br>

### 로그인 페이지

![2](https://user-images.githubusercontent.com/53133662/160774184-413585d9-74d8-42ba-a60f-db9be968d5c5.gif)

- 이메일, 비밀번호를 통한 로그인 페이지입니다.
- 이메일, 비밀번호는 조건식에 따른 경고 메세지를 구현했습니다.
- 모든 입력이 완료되었을 때 로그인 버튼의 커서가 활성화되도록 하였습니다.
- `onChange`를 사용하여 해당 인풋 값을 입력하면 `value`가  `name` 값으로 업데이트 되고, 로그인 버튼을 클릭하면 `body`에 각각의 `state`를 값을 담아 `post` 로 서버에 요청을 합니다.
- 결과값의 `TOKEN`을 로컬 스토리지에 `token`의 값으로 저장하고, 다시  `history.push` 로 메인페이지로 다시 이동할 수 있게 하였습니다.

</br>

### 부킹 페이지 

<img width="100%" src="https://user-images.githubusercontent.com/53133662/160774194-a69cbbe4-b0b8-4b60-a522-323f95d33199.gif" />

- 부킹 페이지의 이미지를 클릭하면 해당 정보의 상세 페이지를 확인할 수 있습니다.
- 부킹 페이지는 자동으로 부킹 페이지의 데이터를 요청하고 `map`을 통해 렌더됩니다. 동시에 `id` 값에 전체 데이터 안의 호텔 `id`를 지정하고 업데이트 하여 저장합니다.
- 해당 호텔 리스트 중에 특정 배너를 클릭하면 쿼리스트링을 사용한 `id`가 들어있는 `history.push` 로 동일한 `id`를 가진 호텔의 디테일 페이지로 이동합니다.

</br>

### 예약 페이지 : 약관 동의

![4](https://user-images.githubusercontent.com/53133662/160774215-397434eb-9fe8-4a4d-bd60-a7b4820ace93.gif)

- 예약 페이지의 약관동의 컴포넌트를 구현했습니다.
- toggle 버튼의 클릭 이벤트로 `state`를 업데이트하여 펼치기/숨기기 기능을 구현했습니다.
- 약관 자세히 보기의 `data`를 객체로 관리하고, `map`으로 데이터를 렌더하였습니다.

</br>

## 프로젝트 후기
[✍🏻 프로젝트 회고 보러가기!](https://velog.io/@ichbinmin2/첫번째팀프로젝트)

</br>

## Reference
이 프로젝트는 스테이폴리오 사이트를 참조하여 학습목적으로 만들었습니다.
실무수준의 프로젝트이지만 학습용으로 만들었기 때문에 이 코드를 활용하여 이득을 취하거나 무단 배포할 경우 법적으로 문제될 수 있습니다.
이 프로젝트에서 사용하고 있는 사진 대부분은 위코드에서 구매한 것이므로 해당 프로젝트 외부인이 사용할 수 없습니다.

</br>
