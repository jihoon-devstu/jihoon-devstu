<div align="center">

# 안녕하세요, 백엔드 개발자 구지훈입니다 👋

### "Why"와 "How"를 끊임없이 생각하는 개발자

AI가 코드를 쓰는 시간이 늘수록 구조를 이해하고 설계하는 능력이 중요하다고 봅니다.<br/>
AI 활용 능력과 설계 능력을 함께 키우는 백엔드 개발자를 목표로 합니다.

<br/>

[![Portfolio](https://img.shields.io/badge/🔗_웹_포트폴리오_방문하기-portfolio--jihoon--dev.vercel.app-2563EB?style=for-the-badge&logoColor=white)](https://portfolio-jihoon-dev.vercel.app/)

[![Email](https://img.shields.io/badge/Email-wlsgksvheh%40gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:wlsgksvheh@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-jihoon--devstu-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/jihoon-devstu)

</div>

<br/>

## 🙋 About Me

- 🔍 **Why** — 왜 이 기술이 필요한지, 대안은 무엇인지, 무엇을 감수하는지 따져 보고 선택합니다.
- 🤝 **How** — 노션 · 코드리뷰 · 컨벤션 문서로 기록하며 협업합니다. 결정은 근거와 함께 문서로 남깁니다.
- 🤖 **AI** — AI가 작성한 코드도 직접 읽고 검증한 뒤 책임집니다. 정확하게 지시하려면 구조를 알아야 하기에 도메인 · 서비스 · 인프라 구조를 이해하는 데 시간을 씁니다.
- 🌱 **청년취업사관학교 새싹(SeSAC) 영등포캠퍼스 8기**에서 MSA 기반 웹 서비스 개발 과정을 수강 중입니다. `(~2026.11)`

<br/>

## 💪 해 본 것

| 역량 | 내용 | 어디서 |
|---|---|---|
| **클라우드 인프라 · 운영** | Terraform으로 VPC · EKS · SNS/SQS · Lambda 구성, 클러스터 매일 08:00 생성 · 22:00 삭제 자동화, IRSA로 파드별 최소 권한 | 곳간 |
| **분산 환경의 정합성** | 아웃박스 · eventId 멱등 · 발생 시각 비교로 이벤트 유실 · 중복 · 순서 문제 처리, 결제 취소는 선기록 → PG 호출 → 확정 · 대조 | 곳간 |
| **측정 기반 개선** | k6 7개 시나리오로 동시성 버그 4개 발견 → 수정 → 재측정, 채팅 왕복 p95 1.95s → 87ms | 곳간 |
| **동시성 제어** | Redis Lua Script로 입찰 조회 · 검증 · 갱신을 원자적으로, Redis 예외 시 DB 비관적 락으로 전환 | Fantry |
| **인증 · 보안 설계** | AT 메모리 · RT HttpOnly 쿠키 + Redis, jti 블랙리스트 + 회원 단위 강제 로그아웃 마커 | Ddasoom |

<br/>

## 🚀 Projects

### 🏆 곳간 (GOTGAN) — MSA 멀티 스토어 오픈마켓 `2026.10 – 2026.11`
> AWS 인프라 · 결제 · 정산 · 관리자 · 채팅 담당 (3인, SeSAC 최종 프로젝트) — **대표 프로젝트**

작은 가게가 입점해 정산받기까지의 흐름을 **Spring Boot 마이크로서비스 10개**로 만들어 **Terraform으로 구성한 AWS EKS**에 배포했습니다. 돈이 걸린 흐름은 "모든 단계가 실패할 수 있다"를 전제로 설계했고, 기능 완성 뒤에는 QA와 부하테스트를 맡아 **측정 → 수정 → 재측정**으로 버그와 설정 문제를 찾았습니다. 가이드 문서와 목업을 직접 만들어 팀의 기준으로 삼았고, AI 작업 규칙과 문서를 컨텍스트로 AI와 함께 구현하되 결과는 테스트 · 품질 게이트 · 리뷰로 검증했습니다.

[![Backend](https://img.shields.io/badge/Backend-Repository-181717?style=flat-square&logo=github)](https://github.com/sesac-final-1/gotgan-backend)
[![Frontend](https://img.shields.io/badge/Frontend-Repository-181717?style=flat-square&logo=github)](https://github.com/sesac-final-1/gotgan-frontend)
[![Infra](https://img.shields.io/badge/Infra-Repository-181717?style=flat-square&logo=github)](https://github.com/sesac-final-1/gotgan-config)
[![Guide](https://img.shields.io/badge/가이드_문서-gotganguide-2563EB?style=flat-square)](https://gotganguide.vercel.app/)

`Java 21` `Spring Boot 4.1` `Spring Cloud Gateway` `Resilience4j` `MySQL` `Redis` `Keycloak` `AWS EKS · Lambda · SNS/SQS` `Terraform` `Argo CD` `k6`

---

### 🔨 Fantry — 실시간 중고 경매 플랫폼 `2025.09 – 2025.10`
> 실시간 경매 시스템 총괄 (Full Stack 5인)

WebSocket(STOMP) 실시간 입찰 위에 **Redis Lua Script로 조회 · 검증 · 갱신을 하나의 원자적 연산**으로 처리했습니다. Redis 호출에서 예외가 나면 **DB 비관적 락으로 전환**하고, 다음 요청에서 재동기화에 성공하면 Redis 입찰로 돌아오도록 설계했습니다. 입찰 기록은 In-memory Queue에 모아 2초 주기로 저장합니다.

[![Backend](https://img.shields.io/badge/Backend-Repository-181717?style=flat-square&logo=github)](https://github.com/SinsegeaBackend-8th-Team4/fantry-backend)
[![Frontend](https://img.shields.io/badge/Frontend-Repository-181717?style=flat-square&logo=github)](https://github.com/SinsegeaBackend-8th-Team4/fantry-frontend)

`Java 21` `Spring Boot` `JPA` `MySQL` `Redis · Lua` `WebSocket · STOMP` `Vue 3`

---

### 🐾 Ddasoom (따숨) — 유기동물 임시보호 플랫폼 `2026.06 – 2026.07`
> 팀장 · 회원/보안/공통모듈 담당 (5인, SeSAC 미니 프로젝트)

토큰을 어디에 둘 것인가, 제재한 회원을 즉시 막을 수 있는가 — **선택지와 감수한 것을 문서로 남기며** Spring Security 인증 인프라를 설계했습니다. 팀 전체가 쓰는 공통 규격(응답 · 예외 · 페이징)과 컨벤션 문서도 함께 만들었습니다.

[![Backend](https://img.shields.io/badge/Backend-Repository-181717?style=flat-square&logo=github)](https://github.com/SeSac-3/ddasoom-backend)
[![Frontend](https://img.shields.io/badge/Frontend-Repository-181717?style=flat-square&logo=github)](https://github.com/SeSac-3/ddasoom-frontend)

`Java 21` `Spring Boot 3.5` `Spring Security` `JWT · OAuth2` `QueryDSL` `MySQL` `Redis` `React 19`

---

### 🛍️ intelliMarket — 스마트스토어 모티브 쇼핑몰 `2025.07 – 2025.08`
> 스토어 어드민 상품/주문 관리 · 카테고리 구조 설계 (4인, 첫 팀 프로젝트)

**루트-탑-서브 3단계 카테고리 + 스토어 N:M 매핑**을 설계하고, 카테고리 트리 조회의 연쇄 조회(N+1)를 **4-테이블 JOIN + 중첩 resultMap**으로 바꿨습니다. 요청이 화면이 되기까지의 웹 백엔드 뼈대를 익힌 학습 단계의 결과물입니다.

[![Repository](https://img.shields.io/badge/GitHub-Repository-181717?style=flat-square&logo=github)](https://github.com/hye000ne/intellimarket)

`Java 8` `Spring MVC (Legacy)` `MyBatis` `MySQL` `JSP · JSTL`

<br/>

## 🛠️ Tech Stack

**Backend · MSA**

![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring%20Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white)
![JPA](https://img.shields.io/badge/Spring%20Data%20JPA-6DB33F?style=flat-square&logo=spring&logoColor=white)
![QueryDSL](https://img.shields.io/badge/QueryDSL-4479A1?style=flat-square)
![MyBatis](https://img.shields.io/badge/MyBatis-DC382D?style=flat-square)
![Spring Cloud Gateway](https://img.shields.io/badge/Spring%20Cloud%20Gateway-6DB33F?style=flat-square&logo=spring&logoColor=white)
![Resilience4j](https://img.shields.io/badge/Resilience4j-1E293B?style=flat-square)
![Keycloak](https://img.shields.io/badge/Keycloak-4D4D4D?style=flat-square&logo=keycloak&logoColor=white)

**Database · Messaging**

![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Oracle](https://img.shields.io/badge/Oracle-F80000?style=flat-square&logo=oracle&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?style=flat-square&logo=amazondynamodb&logoColor=white)
![SNS · SQS](https://img.shields.io/badge/SNS%20·%20SQS-FF4F8B?style=flat-square&logo=amazonsqs&logoColor=white)
![Flyway](https://img.shields.io/badge/Flyway-CC0200?style=flat-square&logo=flyway&logoColor=white)

**Cloud · DevOps**

![AWS](https://img.shields.io/badge/AWS%20(EKS%20·%20Lambda%20·%20S3)-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-844FBA?style=flat-square&logo=terraform&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-0F1689?style=flat-square&logo=helm&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Argo CD](https://img.shields.io/badge/Argo%20CD-EF7B4D?style=flat-square&logo=argo&logoColor=white)

**Observability · Test**

![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana%20·%20Loki-F46800?style=flat-square&logo=grafana&logoColor=white)
![Zipkin](https://img.shields.io/badge/Zipkin-FE7139?style=flat-square)
![k6](https://img.shields.io/badge/k6-7D64FF?style=flat-square&logo=k6&logoColor=white)
![SonarQube Cloud](https://img.shields.io/badge/SonarQube%20Cloud-126ED3?style=flat-square&logo=sonarqubecloud&logoColor=white)

**Frontend · Tools**

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![Vue.js](https://img.shields.io/badge/Vue%203-4FC08D?style=flat-square&logo=vuedotjs&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
![Claude Code](https://img.shields.io/badge/Claude%20Code-D97757?style=flat-square&logo=claude&logoColor=white)
![Notion](https://img.shields.io/badge/Notion-000000?style=flat-square&logo=notion&logoColor=white)

<br/>

## 📜 Education & Certificates

| 구분 | 내용 | 시기 |
|---|---|---|
| 교육 | 청년취업사관학교 새싹(SeSAC) 영등포캠퍼스 8기 — MSA 기반 웹 서비스 개발 | 2026.05 – 2026.11 `진행 중` |
| 교육 | Java 기반 백엔드 개발자 양성 과정 — **최우수 팀 수료** 🏅 | 2025.04 – 2025.10 |
| 자격증 | SQLD (SQL 개발자) | 2026.06 |
| 자격증 | JLPT N1 | 2019.08 |

<br/>

<div align="center">

## 📌 더 깊게 보고 싶다면

**설계 결정 · 트러블슈팅 · 부하테스트 수치 · 남은 한계까지 프로젝트별로 정리했습니다.**

### 👉 [웹 포트폴리오 방문하기](https://portfolio-jihoon-dev.vercel.app/) 👈

[![Portfolio](https://img.shields.io/badge/portfolio--jihoon--dev.vercel.app-2563EB?style=for-the-badge&logo=googlechrome&logoColor=white)](https://portfolio-jihoon-dev.vercel.app/)

</div>
