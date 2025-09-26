# 🌊 SnapTide

사진 기반 **소셜 플랫폼 (SNS)** 으로, 사용자가 사진을 공유하고 댓글을 통해 소통할 수 있는 풀스택 웹 애플리케이션입니다.  
Spring Boot 기반 REST API 서버와 React(TypeScript) 클라이언트로 구성되었습니다.

## 🛠️ 기술 스택

### Backend
- Java 17
- Spring Boot 3.x
- Spring Data JPA
- Spring Security (JWT 기반 인증)
- Spring Validation
- Swagger (springdoc-openapi)
- MySQL / H2
- Maven

### Frontend
- React 18+
- TypeScript
- React Router
- Bootstrap / Tailwind CSS
- Fetch API
- JWT 인증

### Infra / Tools
- Docker / Docker Compose
- GitHub Actions (CI/CD)
- IntelliJ, VSCode

## 🚀 주요 기능

| 구분 | 기능 |
|------|------|
| 회원 관리 | 회원 가입, 로그인, 권한(Role) 관리 |
| 인증 처리 | JWT 토큰 기반 인증/인가, 세션 유지 |
| 피드 관리 | 피드 등록, 수정, 삭제, 조회, 페이징 처리 |
| 리뷰 관리 | 피드·사진에 대한 리뷰 CRUD |
| 사진 업로드 | Multipart 파일 업로드 및 URL 반환 |
| UI/UX | 반응형 디자인, 사진 목록·검색·필터링 |
| 예외 처리 | ControllerAdvice 기반 전역 예외 처리 |

## 🧱 ERD 다이어그램

```text
Members (회원)
 ├── id (PK)
 ├── email
 ├── password
 ├── nickname
 └── roles (ManyToMany) ──▶ MembersRole

Feeds (피드)
 ├── id (PK)
 ├── title
 ├── content
 ├── member_id (FK) ──▶ Members

Reviews (리뷰)
 ├── id (PK)
 ├── content
 ├── member_id (FK) ──▶ Members
 └── feed_id (FK) ──▶ Feeds

Photos (사진)
 ├── id (PK)
 ├── uuid
 ├── fileName
 ├── uploadPath
 └── review_id (nullable, FK) ──▶ Reviews
````

## 📂 프로젝트 구조

```plaintext
snapTide/
├── backend/                 # Spring Boot API 서버
│   ├── src/
│   ├── target/snapTide-api.jar
│   ├── Dockerfile
│   └── pom.xml
│
├── frontend/                # React 클라이언트
│   ├── src/pages/
│   │   ├── Login.tsx
│   │   ├── Join.tsx
│   │   ├── List.tsx
│   │   ├── Read.tsx
│   │   ├── Modify.tsx
│   │   └── Register.tsx
│   ├── Dockerfile
│   └── package.json
│
├── docker-compose.yml
└── README.md
```
## 📘 Swagger & 라우팅

* **Swagger UI**

  ```
  http://localhost:8080/swagger-ui/index.html
  ```

* **Frontend 주요 라우팅**

  | 경로                   | 설명          |
  | -------------------- | ----------- |
  | `/feeds/list`        | 피드 리스트 및 검색 |
  | `/feeds/register`    | 새 피드 작성     |
  | `/feeds/read?fno=1`  | 피드 상세 보기    |
  | `/feeds/modify/:fno` | 피드 수정       |
  | `/login`             | 사용자 로그인     |
  | `/join`              | 회원가입        |


## ⚙️ 실행 방법

### 1. Docker Compose 실행 (권장)

```bash
docker-compose up --build
```

* API 서버: [http://localhost:8080](http://localhost:8080)
* Frontend: [http://localhost:3000](http://localhost:3000)

### 2. 수동 실행

#### Backend

```bash
cd backend
./mvnw spring-boot:run
```

#### Frontend

```bash
cd frontend
npm install
npm start
```

## 📸 주요 화면 (UI 캡처)

| 기능                | 화면 1                               | 화면 2                                     | 화면 3                                   |
| ----------------- | ---------------------------------- | ---------------------------------------- | -------------------------------------- |
| **회원 인증**         | ![로그인](./그림19.png)<br/>로그인 페이지     | ![로그인 성공](./그림20.png)<br/>로그인 성공 → 메인 이동 | ![유효성 검사](./그림21.png)<br/>유효성 검사       |
| **피드 등록 & 목록**    | ![등록 페이지](./그림25.png)<br/>게시글 등록   | ![등록 완료](./그림26.png)<br/>이미지 없는 등록       | ![다중 등록](./그림34.png)<br/>다중 이미지 등록     |
| **피드 조회 & 수정/삭제** | ![상세 보기](./그림28.png)<br/>게시글 상세    | ![수정](./그림29.png)<br/>게시글 수정             | ![삭제](./그림30.png)<br/>게시글 삭제           |
| **검색 & 필터링**      | ![카테고리](./그림31.png)<br/>카테고리 필터링   | ![검색](./그림32.png)<br/>키워드 검색             | ![검색 결과](./그림33.png)<br/>검색 결과         |
| **피드 상세 & 수정 완료** | ![상세](./그림36.png)<br/>READ 화면      | ![수정 완료](./그림35.png)<br/>수정 완료           | ![다중 이미지 상세](./그림27.png)<br/>이미지 없는 등록 |
| **반응형 페이지**       | ![반응형](./그림41.png)<br/>991px 이하 화면 | ![리스트](./그림24.png)<br/>피드 리스트 & 페이징      | ![리스트 확장](./그림39.png)<br/>기능 확장        |


## 🙌 기여 방법

1. 이슈 확인 및 브랜치 생성
2. 기능 개발 후 PR 작성
3. 코드 리뷰 및 Merge 진행

