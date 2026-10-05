# 곽도윤 · Server Engineer

세상에 새로운 가치를 만들 수 있는 서비스의 개발을 지향하는
서버 개발자 곽도윤입니다.

<br>

## 📫 Contact

- Email: kdoing2002@gmail.com
- Blog: [velog.io/@hairyung2002](https://velog.io/@hairyung2002/posts)
- LinkedIn: [in/hairyung2002](https://www.linkedin.com/in/hairyung2002/)

## 🚀 Featured Projects

### Dirvana — 동국대학교 2025 가을축제 사이트
`BE 파트 리더 · FE` `2025.09` `DRF · React · AWS EC2 / CloudFront / WAF`

- **문제** 오픈 당일 `/api/like/`에 초당 100회, `/api/game/success/`에 초당 200회 이상의 비정상 POST가 몰려 서비스 응답 불능
- **판단** DRF Throttle은 Gunicorn Worker가 요청을 받은 *뒤에* 검사하므로 리소스 점유를 막지 못함 → 방어 위치를 애플리케이션이 아닌 서비스 앞단으로 옮김
- **구조** `CloudFront → WAF → ALB → EC2(Private)`로 전환하고 Security Group을 CloudFront 대역만 허용해 Origin 직접 접근 차단. WAF Rate-Based Rule 임계값은 GA의 정상 트래픽 패턴을 기준으로 산출
- **결과** 2일차 해외 IP 재공격을 Edge에서 차단, 3일 누적 활성 사용자 10,000+ / 최대 DAU 8,000
- **회고** 사후 DB 로그 재분석으로 실제 다운 원인이 SQLite의 단일 Write Lock이었음을 확인 → 다음 축제(2026 봄)에서 MySQL로 전환

[BE Repo](https://github.com/LikeLion-at-DGU/2025_fall_festival_BE) · [FE Repo](https://github.com/LikeLion-at-DGU/2025_fall_festival_front)

---

### Wilson — 치매 당사자·보호자를 함께 케어하는 음성 AI 플랫폼
`PM · Backend · APP` `2026.06 ~` `Spring Boot · gRPC · Kafka · Redis · React Native · Expo`

- **문제** 실시간 음성 대화와 수 초가 걸리는 치매 징후 분석(BERT)이 같은 경로에 있으면 대화가 끊김
- **판단** REST 대신 **gRPC 스트리밍**을 제안 — 음성을 바이너리 그대로 전달해 파싱 오버헤드를 없애고, 응답을 형태소 단위로 스트리밍해 체감 대기시간을 줄임. 무거운 분석은 메시지 큐로 분리 (AI 팀원과 공동 설계)
- **개발 방식** CLAUDE.md로 TDD(Red-Green-Refactor)와 완료 정의(Done Definition)를 규칙화해 AI 코딩 도구를 통제된 방식으로 활용
- **현재** 개발 약 80% 진행 중 · 2026 글로벌 피우다프로젝트 선정

---

### PromptPlace — AI 프롬프트 마켓플레이스
`Frontend` `2025.07 ~ 운영 중` `React · TypeScript · TanStack Query · PortOne`

- **담당** 결제(PortOne) · 판매자 정산 · 관리자 대시보드 등 커머스 핵심 흐름의 FE 전담
- **문제** 결제창이 열리기도 전에 서버 결제 검증 요청이 먼저 나가는 현상 — 로컬에선 정상, 운영에서만 매번 재현
- **해결** 결제 요청 → SDK 완료 → 서버 검증의 실행 순서를 콜백 기반 Promise 체이닝으로 구조적으로 보장해 이후 안정 운영
- **이어진 것** "로컬 테스트 통과 ≠ 운영 안정성"이라는 경험이 PyCon 발표 주제로 이어짐

[Service](https://www.promptplace.kr) · [FE Repo](https://github.com/PromptPlace/PromtPlace-FE)

<br>

## 📂 All Projects

| 프로젝트 | 기간 | 역할 | 한 줄 요약 |
|---|---|---|---|
| **2026 가을축제 사주 소개팅** | 26.09 | PO / BE | 사주 결과·궁합 공유와 소개팅 신청을 분리한 축제 한정 매칭 서비스 (Spring Boot · PostgreSQL) |
| **Wilson** | 26.06 ~ | PM · BE · App | gRPC + MQ로 실시간 대화와 AI 분석을 분리한 음성 돌봄 플랫폼 |
| **Nexo** | 26.05 ~ | PO · 소프트웨어 엔지니어 | Nginx의 무중단 배포 문제를 해결하고 쉬운 설정을 돕는 플랫폼 |
| **2026 봄축제 사이트** | 26.03 | BE | 가을축제 장애 경험을 반영해 DB를 MySQL로 전환 |
| **ConnecTeamed** | 25.12 ~ 26.02 | FE | 쉽게 익힐 수 있는 팀 협업 툴 |
| **PortPolis** | 25.11 | Full-stack | 개인 맞춤형 포트폴리오 작성 플랫폼 (React · Express) |
| **동데이** | 25.10 ~ 25.11 | 팀 리더 · PM | 공연장 15곳 컨택·3곳 파일럿 검증 후 타당성 판단으로 자발적 종료 · 데모데이 대상 |
| **Dirvana** | 25.09 | BE 리더 · FE | 실제 공격 대응 및 CloudFront + WAF 방어 구조 설계 |
| **Walking City** | 25.08 | Full-stack | Bedrock RAG 기반 산책 코스 추천 · K-HTML 해커톤 우수상 |
| **Badang** | 25.07 ~ 25.08 | BE | 리뷰 기반 AI 소상공인 컨설팅 플랫폼 |
| **PromptPlace** | 25.07 ~ | Full-stack | 결제·정산이 있는 AI 프롬프트 마켓플레이스 (운영 중) |
| **EdgeMesh** | 진행 중 | 1인 개발 | epoll + rwlock 기반 C 프록시 엔진과 라우팅 관리 콘솔 |

<br>

## 📋 이력

**🎓 학력**
- 동국대학교 컴퓨터정보통신공학부 정보통신공학전공 · 경영학과 복수전공 (2028.02 졸업 예정)

**🏃 활동**

| 기간 | 활동 |
|---|---|
| 2026.09 ~ | 공공 AX 서포터즈 1기 |
| 2026.05 ~ | ASBG in DGU 1st General Member |
| 2026.01 ~ | 멋쟁이사자처럼 14기 백엔드 트랙장 |
| 2025.08 ~ 2026.02 | UMC 9th Web 파트 중앙운영진 수료 |
| 2025.03 ~ 2025.12 | 멋쟁이사자처럼 13기 백엔드 트랙 수료 |
| 2025.03 ~ 2025.08 | UMC 8th Web 파트 수료 |
| 2022.09 ~ 2023.02 | 교내 중앙봉사동아리 '길' 회장 |
| 2022.09 ~ 2023.02 | 교내 중앙봉사동아리 '길' 회장 |

**🏆 수상 · 🎤 발표**
- 2026.08 PyCon Seoul 2026 세션 발표 — *Green CI / Red Production*
- 2025.11 교내 창업동아리 데모데이 대상 (동데이)
- 2025.08 K-HTML 해커톤 우수상 (Walking City)

<br>

## 🛠 Tech Stack

## Languages

<p>
<img src="https://img.shields.io/badge/C-A8B9CC?style=for-the-badge&logo=C&logoColor=white"/>
<img src="https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=java&logoColor=white"/>
<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=Python&logoColor=white"/>
<img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black"/>
<img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white"/>
</p>

## Backend

<p>
<img src="https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white"/>
<img src="https://img.shields.io/badge/Django_DRF-092E20?style=for-the-badge&logo=django&logoColor=white"/>
<img src="https://img.shields.io/badge/Node.js_Express-339933?style=for-the-badge&logo=nodedotjs&logoColor=white"/>
</p>

## Frontend

<p>
<img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=React&logoColor=black"/>
<img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white"/>
<img src="https://img.shields.io/badge/Redux-593D88?style=for-the-badge&logo=redux&logoColor=white"/>
<img src="https://img.shields.io/badge/Zustand-764ABC?style=for-the-badge&logo=react&logoColor=white"/>
</p>

## Cloud & DevOps

<p>
<img src="https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white"/>
<img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
<img src="https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white"/>
</p>

<div align="center">
  <a href="https://github.com/hairyung2002">
    <img src="https://github-readme-streak-stats.herokuapp.com/?user=hairyung2002&theme=tokyonight" alt="GitHub Streak" height="170" />
  </a>
  &nbsp;&nbsp;
  <a href="https://solved.ac/profile/hairyung2002">
    <img src="http://mazassumnida.wtf/api/v2/generate_badge?boj=hairyung2002" alt="Solved.ac Badge" height="170" />
  </a>
</div>
