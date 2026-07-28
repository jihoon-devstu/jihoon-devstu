<div align="center">

# 안녕하세요, 백엔드 개발자 구지훈입니다 👋

### "Why"와 "How"를 끊임없이 생각하는 개발자

동작하는 코드에서 멈추지 않고 **성능 · 동시성 · 장애 상황**까지 파고듭니다.<br/>
문제를 정의하고, 트레이드오프를 따져 해결하고, 그 과정을 기록합니다.

<br/>

[![Portfolio](https://img.shields.io/badge/🔗_웹_포트폴리오_방문하기-portfolio--jihoon--dev.vercel.app-2563EB?style=for-the-badge&logoColor=white)](https://portfolio-jihoon-dev.vercel.app/)

[![Email](https://img.shields.io/badge/Email-wlsgksvheh%40gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:wlsgksvheh@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-jihoon--devstu-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/jihoon-devstu)

</div>

<br/>

## 🙋 About Me

- 🛒 개발 전, **4년 4개월간 커머스를 판매자·운영자로 직접 겪었습니다** — 스마트스토어 2곳 운영, 마케팅까지. 도메인이 무엇이든 *그 서비스를 쓰는 사람의 맥락부터 이해하고 개발하는 것*이 저의 출발점입니다.
- 🔍 "왜 이 기술인가"를 먼저 묻습니다 — 대안과 트레이드오프를 비교하고, 결정의 근거를 **문서로** 남깁니다.
- 🤝 기록으로 협업합니다 — 코드 리뷰로 경계 케이스를 지적하고, 규칙 변경은 문서 PR로만. (팀 프로젝트 PR 100건 운영)
- 🌱 현재 **청년취업사관학교 새싹(SeSAC) 영등포캠퍼스**에서 AWS와 AI를 활용한 MSA 기반 웹 서비스 개발 과정을 수강 중입니다. `(~2026.11)`

<br/>

## 💪 무엇을 증명했나

| 역량 | 내용 | 어디서 |
|---|---|---|
| **동시성 제어 · 성능** | Redis Lua Script 원자 연산, DB 비관적 락, In-memory Queue + Batch Insert. K6 동시 입찰 검증 **2,079개 항목 전체 통과** | Fantry |
| **인증 · 보안 설계** | Spring Security 필터 체인, JWT 이중 토큰(RT 로테이션 + Grace Period, jti 블랙리스트, 강제 로그아웃 마커) | Ddasoom |
| **데이터 모델링 · 쿼리 최적화** | 3단계 정규화 카테고리 설계, N+1 진단 → JOIN + 중첩 resultMap 개선 (쿼리 1+2N → 1) | intelliMarket |
| **장애를 전제로 한 설계** | Redis 장애 시 DB Fallback Mode + 자가 치유(Self-Healing) 구조 | Fantry |

<br/>

## 🚀 Projects

> 🔎 아래는 요약입니다. 각 프로젝트의 **문제 → 원인 → 해결 → 결과** 전 과정과 화면·다이어그램은<br/>
> **[웹 포트폴리오 →](https://portfolio-jihoon-dev.vercel.app/)** 에서 확인할 수 있습니다.

### 🏆 Fantry — 실시간 중고 경매 플랫폼 `2025.09 – 2025.10`
> 실시간 경매 시스템 총괄 (Full Stack 5인) — **대표 프로젝트**

WebSocket(STOMP) 실시간 입찰 위에 **Redis Lua Script로 락 없는 원자적 동시성 제어**를 구현하고, Redis 장애 시 **DB 비관적 락으로 전환 후 스스로 복구하는 Fallback 구조**까지 설계했습니다. 입찰 기록은 In-memory Queue + 2초 주기 Batch Insert로 쓰기 부하를 분리했습니다.

[![Backend](https://img.shields.io/badge/Backend-Repository-181717?style=flat-square&logo=github)](https://github.com/SinsegeaBackend-8th-Team4/fantry-backend)
[![Frontend](https://img.shields.io/badge/Frontend-Repository-181717?style=flat-square&logo=github)](https://github.com/SinsegeaBackend-8th-Team4/fantry-frontend)

`Java 21` `Spring Boot` `JPA` `MySQL` `Redis · Lua` `WebSocket · STOMP` `Vue 3`

---

### 🐾 Ddasoom (따숨) — 유기동물 임시보호 플랫폼 `2026.06 – 2026.07`
> 팀장 · 회원/보안/공통모듈 담당 (5인, SeSAC 첫 미니 프로젝트)

토큰이 탈취되면? 제재된 회원의 기존 세션은? 여러 탭이 동시에 재발급하면? — **경계 상황을 먼저 정의하고 트레이드오프를 문서로 남기며** 인증 인프라를 설계했습니다. 팀 전체가 쓰는 공통 규격(응답·예외·페이징)도 함께 만들었습니다.

[![Backend](https://img.shields.io/badge/Backend-Repository-181717?style=flat-square&logo=github)](https://github.com/SeSac-3/ddasoom-backend)
[![Frontend](https://img.shields.io/badge/Frontend-Repository-181717?style=flat-square&logo=github)](https://github.com/SeSac-3/ddasoom-frontend)

`Java 21` `Spring Boot 3.5` `Spring Security` `JWT · OAuth2` `QueryDSL` `MySQL` `Redis` `React 19`

---

### 🛍️ intelliMarket — 스마트스토어 모티브 쇼핑몰 `2025.07 – 2025.08`
> 스토어 어드민 상품/주문 관리 · 카테고리 구조 설계 (4인, 첫 팀 프로젝트)

**루트-탑-서브 3단계 정규화 카테고리 + 스토어 N:M 매핑**을 설계하고, 중첩 select로 인한 **N+1 문제를 4-테이블 JOIN + 중첩 resultMap으로 개선**했습니다. 프레임워크의 자동 설정 없이 웹 백엔드의 뼈대를 익힌 학습 단계의 결과물입니다.

[![Repository](https://img.shields.io/badge/GitHub-Repository-181717?style=flat-square&logo=github)](https://github.com/hye000ne/intellimarket)

`Java 8` `Spring MVC (Legacy)` `MyBatis` `MySQL` `JSP · JSTL`

<br/>

## 🛠️ Tech Stack

**Backend**

![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring%20Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white)
![JPA](https://img.shields.io/badge/Spring%20Data%20JPA-6DB33F?style=flat-square&logo=spring&logoColor=white)
![MyBatis](https://img.shields.io/badge/MyBatis-DC382D?style=flat-square)
![QueryDSL](https://img.shields.io/badge/QueryDSL-4479A1?style=flat-square)

**Database · Infra**

![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Oracle](https://img.shields.io/badge/Oracle-F80000?style=flat-square&logo=oracle&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![WebSocket](https://img.shields.io/badge/WebSocket%20·%20STOMP-010101?style=flat-square)
![Flyway](https://img.shields.io/badge/Flyway-CC0200?style=flat-square&logo=flyway&logoColor=white)

**Frontend · Tools**

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Vue.js](https://img.shields.io/badge/Vue%203-4FC08D?style=flat-square&logo=vuedotjs&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=flat-square&logo=swagger&logoColor=black)
![Notion](https://img.shields.io/badge/Notion-000000?style=flat-square&logo=notion&logoColor=white)

<br/>

## 📜 Education & Certificates

| 구분 | 내용 | 시기 |
|---|---|---|
| 교육 | 청년취업사관학교 새싹(SeSAC) 영등포캠퍼스 8기 — AWS·AI 활용 MSA 웹 서비스 개발 | 2026.05 – 2026.11 `진행 중` |
| 교육 | Java 기반 백엔드 개발자 양성 과정 — **최우수 팀 수료** 🏅 | 2025.04 – 2025.10 |
| 자격증 | SQLD (SQL 개발자) | 2026.06 |
| 자격증 | 정보처리기사 — 필기 합격 · 실기 진행 중 | 2026 |
| 자격증 | JLPT N1 | 2019.08 |

<br/>

<div align="center">

## 📌 더 깊게 보고 싶다면

**트러블슈팅 · 트레이드오프 · 한계와 다음 단계까지, 모든 문제 해결 과정을 기록했습니다.**

### 👉 [웹 포트폴리오 방문하기](https://portfolio-jihoon-dev.vercel.app/) 👈

[![Portfolio](https://img.shields.io/badge/portfolio--jihoon--dev.vercel.app-2563EB?style=for-the-badge&logo=googlechrome&logoColor=white)](https://portfolio-jihoon-dev.vercel.app/)

</div>
