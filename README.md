# 광주 프로젝트

> **Spring Boot**를 기반으로 한 웹 애플리케이션으로, **주소 검색**, **음식 및 관광 정보**를 제공합니다.

---

## 🛠️ 프로젝트 구조

```
gwangju/
│
├── src/main/java/com/yohaeng/gwangju│   
│   ├── controller       # 컨트롤러 (로그인, 음식, 관광 정보 등)
│   ├── mapper           # MyBatis 매퍼 인터페이스
│   ├── model            # 도메인 모델 및 DTO
│   │   └── service      # 서비스 관련 DTO
│   ├── service          # 비즈니스 로직 서비스
│
├── src/main/resources
│   ├── static           # 정적 리소스 (CSS, JS, 이미지 등)
│   ├── templates        # Thymeleaf 템플릿 (로그인, 회원가입 등)
│   ├── mybatis/mapper   # MyBatis XML 매퍼 파일
│   └── application.properties  # 애플리케이션 설정 파일
│
└── src/test/java/com/yohaeng/gwangju
    └── GwangjuApplicationTests.java  # 유닛 테스트
```

---

## ✨ 주요 기능


- **주소 검색 및 관리:**
  - Kakao API를 사용한 주소 검색 기능 제공
- **음식 및 관광 정보 제공:**
  - 광주 지역의 음식점과 관광지 정보 제공


---

## ⚙️ 데이터베이스 스키마

```sql


CREATE TABLE `tour_dong` (
  `id` int PRIMARY KEY NOT NULL AUTO_INCREMENT, -- 게시물 넘버
  `title` varchar(100) DEFAULT null, -- 게시물 제목
  `zipcode` int DEFAULT null, -- 우편번호
  `addr1` varchar(50) NOT NULL, -- 주소
  `addr2` varchar(50) NOT NULL, -- 행정동
  `home` varchar(250) DEFAULT null, -- 홈페이지
  `first_image` varchar(100) DEFAULT null, -- 게시물의 이미지
  `isimage` int DEFAULT '0', -- 이미지 여부 (0: 없음, 1: 있음)
  `tel` varchar(50) DEFAULT null, -- 전화번호
  `description` text, -- 게시물 설명
  `areacode` int DEFAULT null, -- 대한민국 지역코드
  `book_tour` varchar(2) DEFAULT null, -- 예약 가능 여부
  `cat1` varchar(30) DEFAULT null, -- 카테고리 코드 1
  `cat2` varchar(30) DEFAULT null, -- 카테고리 코드 2
  `cat3` varchar(30) DEFAULT null, -- 카테고리 코드 3
  `contentid` int DEFAULT null, -- 게시물 고유 아이디
  `mapx` double DEFAULT null, -- 지도상의 x좌표
  `mapy` double DEFAULT null, -- 지도상의 y좌표
  `mlevel` int DEFAULT null, -- 지도 줌 레벨
  `modifiedtime` varchar(30) DEFAULT null, -- 수정된 날짜
  `sigungucode` int DEFAULT null, -- 구코드
  `category` int DEFAULT null -- 게시물 유형
);

CREATE TABLE `tour` (
  `id` int PRIMARY KEY NOT NULL AUTO_INCREMENT, -- 게시물 넘버
  `title` varchar(100) DEFAULT null, -- 게시물 제목
  `zipcode` int DEFAULT null, -- 우편번호
  `addr1` varchar(50) NOT NULL, -- 주소
  `addr2` varchar(50) NOT NULL, -- 행정동
  `home` varchar(250) DEFAULT null, -- 홈페이지
  `first_image` varchar(100) DEFAULT null, -- 게시물의 이미지
  `isimage` int DEFAULT '0', -- 이미지 여부
  `tel` varchar(50) DEFAULT null, -- 전화번호
  `description` text, -- 게시물 설명
  `areacode` int DEFAULT null, -- 지역코드
  `book_tour` varchar(2) DEFAULT null, -- 예약 가능 여부
  `cat1` varchar(30) DEFAULT null, -- 카테고리 코드 1
  `cat2` varchar(30) DEFAULT null, -- 카테고리 코드 2
  `cat3` varchar(30) DEFAULT null, -- 카테고리 코드 3
  `contentid` int DEFAULT null, -- 고유 아이디
  `mapx` double DEFAULT null, -- 지도상의 x좌표
  `mapy` double DEFAULT null, -- 지도상의 y좌표
  `mlevel` int DEFAULT null, -- 줌 레벨
  `modifiedtime` varchar(30) DEFAULT null, -- 수정된 날짜
  `sigungucode` int DEFAULT null, -- 구코드
  `category` int DEFAULT null -- 게시물 유형
);


CREATE TABLE `food` (
  `id` int PRIMARY KEY NOT NULL AUTO_INCREMENT, -- 게시물 넘버
  `title` varchar(100) NOT NULL, -- 음식점 이름
  `addr1` varchar(100) DEFAULT null, -- 주소
  `addr2` varchar(10) DEFAULT null, -- 행정동
  `image` varchar(1000) DEFAULT null, -- 음식점 이미지
  `tel` varchar(30) DEFAULT null, -- 전화번호
  `rating` double DEFAULT null, -- 평점
  `review_cnt` int DEFAULT null, -- 리뷰 수
  `cat1` varchar(30) DEFAULT null, -- 카테고리 코드 1
  `cat2` varchar(30) DEFAULT null, -- 카테고리 코드 2
  `cat3` varchar(30) DEFAULT null, -- 카테고리 코드 3
  `mapx` double DEFAULT null, -- 지도상의 x좌표
  `mapy` double DEFAULT null, -- 지도상의 y좌표
  `sigungucode` int DEFAULT null, -- 구코드
  `category` int DEFAULT null -- 게시물 유형
);



-- delete_old_users 이벤트: 논리적으로 삭제된 사용자를 30일 후에 물리적으로 삭제하는 이벤트
C

---

## ⚙️ 설치 및 설정

1. **레포지토리 클론:**

   ```bash
   git clone https://github.com/your-username/TeamProject.git
   cd TeamProject
   ```

2. **의존성 설치:**

   ```bash
   ./gradlew build
   ```

3. **애플리케이션 실행:**

   ```bash
   ./gradlew bootRun
   ```

4. **웹 애플리케이션 접속:**

   브라우저에서 다음 주소로 접속하세요:  
   `http://localhost:8080/main`

---

## 🚀 사용 기술

- **백엔드:** Spring Boot 3.x, MyBatis, Spring Security
- **프론트엔드:** Thymeleaf, HTML5, CSS, JavaScript
- **데이터베이스:** MySQL-
- **API 통합:** Kakao 주소 검색 API, 구글맵 API

---

## 🧪 테스트

다음 명령어로 유닛 테스트를 실행할 수 있습니다:

```bash
./gradlew test
```

---

## 🛡️ 라이선스

이 프로젝트는 [MIT 라이선스](LICENSE)를 따릅니다.

---

## 🤝 기여 방법

1. 레포지토리 포크
2. 새로운 브랜치 생성: `git checkout -b feature-branch`
3. 변경 사항 커밋: `git commit -m 'Add new feature'`
4. 브랜치에 푸시: `git push origin feature-branch`
5. 풀 리퀘스트 생성

---



## 📧 문의

문의사항이 있으시면 아래 이메일로 연락 주세요:  
📧 **dlsdusk@gmail.com**

---

## 📑 참고 사항

- 애플리케이션 실행 전에 MySQL이 실행 중인지 확인하세요.
- `application.properties` 파일에서 데이터베이스 자격 증명을 업데이트하세요.
- **Google**, **Kakao**,맵이용에 필요한 API 키를 설정하세요.

