# ☕ CoffeeTech - 커피 소비/섭취 관리 시스템

> "당신의 커피 습관을 스마트하게 관리하세요"
> 커피 소비량 및 지출 확인, 섭취량 조절, 출석 체크를 통한 커피 지급 시스템

![Java](https://img.shields.io/badge/Java-99.6%25-orange)
![Build Tool](https://img.shields.io/badge/Build-Gradle-02303A)
![Framework](https://img.shields.io/badge/Framework-Spring%20Boot-6DB33F)
![Database](https://img.shields.io/badge/Database-MariaDB-003545)
![License](https://img.shields.io/badge/License-MIT-blue)

---

## 📋 목차

* [🎯 프로젝트 개요](#-프로젝트-개요)
* [✨ 주요 기능](#-주요-기능)
* [✅ 구현 현황](#-구현-현황)
* [🏗️ 서비스 아키텍처](#️-서비스-아키텍처)
* [🧩 ERD 요약](#-erd-요약)
* [📌 대표 API (샘플 8개)](#-대표-api-샘플-8개)
* [📁 프로젝트 구조](#-프로젝트-구조)
* [🛠️ 기술 스택](#️-기술-스택)
* [💻 실행 방법](#-실행-방법)
* [🤝 기여하기](#-기여하기)
* [📄 라이선스](#-라이선스)

---

## 🎯 프로젝트 개요

**CoffeeTech**는 커피 애호가들을 위한 스마트 커피 관리 플랫폼입니다.

* ☕ 매일의 커피 섭취 기록
* 💰 커피 지출액 추적 및 통계
* 📊 일간/월간 평균 섭취량 및 지출 분석
* ✅ 출석 체크로 포인트 적립
* 🎁 적립 포인트로 커피 상품 구매

---

## ✨ 주요 기능

### 👤 사용자 관리

* 회원가입 / 로그인 (JWT)
* 프로필 관리 (정보 수정, 프로필 사진 업로드)
* 포인트 조회 및 내역 조회

### ☕ 커피 섭취 관리

* 일일 섭취 기록 (시간대별 로그)
* 섭취량 분석 (오늘/어제 비교, 최근 7일 평균, 월 평균)
* 섭취 목표 설정 및 진도 추적
* 기록 수정/삭제

### 💸 지출 관리

* 일일 지출 기록
* 지출 통계 (오늘/어제 비교, 최근 7일 평균, 월 평균)
* 지출 카테고리 (카페/편의점/온라인 등)
* 기록 수정/삭제

### ✅ 출석 체크 & 포인트

* 일일 출석 체크 (1일 1회)
* 출석 포인트 자동 적립
* 연속 출석 보너스
* 월간 출석 달력
* 포인트 적립/사용 내역

### 🎁 커피 스토어

* 상품 목록 조회
* 포인트로 구매
* 구매 내역 조회
* 쿠폰/할인 (확장 가능)

---

## ✅ 구현 현황

| 기능 영역 | 기능                | 상태 |
| ----- | ----------------- | -- |
| 인증/계정 | 회원가입              | ✅  |
| 인증/계정 | 로그인(JWT 발급)       | ✅  |
| 인증/계정 | JWT 인증 필터/권한 체크   | ✅  |
| 사용자   | 프로필 조회/수정         | ✅  |
| 사용자   | 프로필 이미지 업로드       | 🚧 |
| 포인트   | 포인트 잔액 조회         | ✅  |
| 포인트   | 포인트 적립/사용 내역 조회   | 🚧 |
| 커피 섭취 | 섭취 기록 생성/조회       | ✅  |
| 커피 섭취 | 섭취 기록 수정/삭제       | ✅  |
| 커피 섭취 | 섭취 통계(오늘/7일/월 평균) | ✅  |
| 지출    | 지출 기록 생성/조회       | ✅  |
| 지출    | 지출 기록 수정/삭제       | ✅  |
| 지출    | 지출 통계(오늘/7일/월 평균) | ✅  |
| 출석    | 일일 출석 체크(1일 1회)   | ✅  |
| 출석    | 출석 달력(월간)         | 🚧 |
| 출석    | 연속 출석 보너스         | 🚧 |
| 스토어   | 상품 목록 조회          | 🚧 |
| 스토어   | 포인트로 구매           | 🚧 |
| 스토어   | 구매 내역 조회          | 🚧 |
| 분석    | 개인 대시보드(요약 지표)    | 🚧 |
| 분석    | 인사이트/추천           | 🚧 |

---

## 🏗️ 서비스 아키텍처

```text
[Client(Web/Mobile)]
        |
      REST
        |
[Spring Boot API]
 - Controller
 - Service
 - Repository(JPA)
        |
     MariaDB
```

---

## 🧩 ERD 요약

### 핵심 테이블

* `users` : 사용자 계정/프로필/포인트 잔액
* `coffee_records` : 커피 섭취 기록(시간, 용량, 카테고리 등)
* `expense_records` : 지출 기록(금액, 결제처/카테고리 등)
* `checkin_history` : 출석 체크 기록(날짜 단위)
* `point_history` : 포인트 적립/사용 내역(타입, 증감)
* `products` : 스토어 상품(이름, 가격(포인트), 재고 등)
* `orders` : 구매 주문(상품, 수량, 사용 포인트, 상태 등)

### 관계 요약

```text
users (1) --- (N) coffee_records
users (1) --- (N) expense_records
users (1) --- (N) checkin_history
users (1) --- (N) point_history
users (1) --- (N) orders
products (1) --- (N) orders
```

### ERD에서 자주 쓰는 제약(권장)

* `checkin_history`: (`user_id`, `checkin_date`) UNIQUE → 1일 1회 출석 보장
* `point_history`: `amount`(증감), `type`(EARN/USE), `reason`(출석/구매 등)
* `orders`: `status`(PAID/CANCELED 등), `created_at`

---

## 📌 대표 API (샘플 8개)

URL은 예시입니다. 실제 컨트롤러 매핑에 맞게 경로만 바꾸면 됩니다.
인증 필요 API는 `Authorization: Bearer {token}` 헤더를 사용합니다.

### 1) 회원가입

* **POST** `/api/auth/signup`

```json
{
  "email": "test@coffeetech.com",
  "password": "password1234",
  "nickname": "jiin"
}
```

### 2) 로그인(JWT 발급)

* **POST** `/api/auth/login`

```json
{
  "email": "test@coffeetech.com",
  "password": "password1234"
}
```

* **Response 예시**

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIs..."
}
```

### 3) 내 프로필 조회

* **GET** `/api/users/me`
* Header: `Authorization: Bearer {token}`

### 4) 커피 섭취 기록 생성

* **POST** `/api/coffee/records`
* Header: `Authorization: Bearer {token}`

```json
{
  "drankAt": "2026-02-09T09:30:00",
  "amountMl": 355,
  "type": "AMERICANO",
  "memo": "출근길"
}
```

### 5) 커피 섭취 기록 조회(일자)

* **GET** `/api/coffee/records?date=2026-02-09`
* Header: `Authorization: Bearer {token}`

### 6) 지출 기록 생성

* **POST** `/api/expenses/records`
* Header: `Authorization: Bearer {token}`

```json
{
  "spentAt": "2026-02-09T10:00:00",
  "amount": 4800,
  "category": "CAFE",
  "storeName": "스타벅스"
}
```

### 7) 출석 체크

* **POST** `/api/checkin`

* Header: `Authorization: Bearer {token}`

* **Response 예시**

```json
{
  "checkinDate": "2026-02-09",
  "earnedPoint": 10,
  "message": "출석 체크 완료"
}
```

### 8) 포인트로 상품 구매

* **POST** `/api/store/orders`
* Header: `Authorization: Bearer {token}`

```json
{
  "productId": 1,
  "quantity": 1
}
```

---

## 📁 프로젝트 구조

```text
Baby-hackathon-backend/
 ├─ src/main/java/coffeetech/
 │  ├─ controller/
 │  ├─ service/
 │  ├─ repository/
 │  ├─ entity/
 │  ├─ dto/
 │  └─ security/
 ├─ src/main/resources/
 │  ├─ application.yml
 │  ├─ application-dev.yml
 │  └─ application-prod.yml
 └─ build.gradle
```

---

## 🛠️ 기술 스택

| 분류    | 기술                    |
| ----- | --------------------- |
| 언어    | Java 11+              |
| 프레임워크 | Spring Boot 2.x       |
| ORM   | JPA/Hibernate         |
| DB    | MariaDB               |
| 보안    | Spring Security + JWT |
| 빌드    | Gradle                |

---

## 💻 실행 방법

### 1) DB 준비 (MariaDB)

* DB: `coffeetech_db`

### 2) 설정 값(예시 키 이름)

아래 값이 필요합니다(로컬/배포 환경에 맞게 설정).

* `SPRING_DATASOURCE_URL`
* `SPRING_DATASOURCE_USERNAME`
* `SPRING_DATASOURCE_PASSWORD`
* `JWT_SECRET`

### 3) 실행

```bash
./gradlew bootRun
```

---

## 🤝 기여하기

* Issue 생성 → Branch 생성 → PR 요청
* 커밋 메시지 예시

```text
feat(checkin): 연속 출석 보너스 구현
```

---

## 📄 라이선스

MIT License (LICENSE 참고)

---

마지막 업데이트: 2026-02-09
버전: 1.0.0
