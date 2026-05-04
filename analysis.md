# 인쇄용 PDF 자동 조립 Python 모듈 개발 — 제안 분석 로그

> 생성일: 2026-05-04
> 공고 URL: https://www.wishket.com/project/154903/

## 1. 공고 파싱 결과

```yaml
job:
  title: "인쇄용 PDF 자동 조립 Python 모듈 개발"
  category: "개발 기타 (IT 서비스 구축)"
  budget_range: "700~900만원 (VAT 별도)"
  duration: "45일 (개발 4-6주 + 테스트 2주)"
  tech_stack: [Python 3.10+, fpdf2/ReportLab, Pillow, ImageMagick, Vercel Serverless]
  description: "POD 커스텀 아동 동화책(하드커버) 인쇄 규격 PDF 자동 생성 Python 모듈"
  requirements:
    - 표지(앞/뒤) + 내지 20페이지, 8.5×8.5인치, 300DPI, CMYK, 블리드 0.125인치
    - 표지 생성 (제목/아이 이름 자동 배치, 뒤 표지 로고+QR+저작권)
    - 내지 레이아웃 (풀블리드/마진, 텍스트 배치, OTF/TTF 폰트)
    - QR 코드 자동 삽입 (주문 고유 ID 기반)
    - sRGB→CMYK 변환 (ICC 프로파일 USWebCoatedSWOP)
    - POD API 연동 선택 (Printful/Blurb)
    - 단위 테스트, README, 샘플 데이터, pip install 가능 패키지
    - Vercel Serverless 호출 가능 구조
  client_questions:
    - "서버리스 환경(Vercel/AWS Lambda) 배포 경험이 있으십니까?"
    - "인쇄 규격 맞춤 + CMYK + 블리드 경험이 있으십니까?"
  deadline: "2026-05-18"
  start_date: "2026-06-15"
  job_post_url: "https://www.wishket.com/project/154903/"
  urls: []
  images: []
  notes:
    - "정부지원사업 — 견적서 발행 필요"
    - "선금 지급 가능"
    - "보증보험 발급 가능 필수"
    - "업력 1년 이상 필수"
```

## 2. URL/이미지 분석

공고 본문에 별도 참고 URL / 이미지 첨부 없음. URL은 위시켓 공고 URL 자체뿐이며, 추가 분석 대상이 없어 본 단계 생략.

분석에 영향을 준 외부 자료가 없으므로, 제안 내용은 공고 본문에 명시된 인쇄 규격(8.5×8.5인치 / 300 DPI / CMYK / 블리드 0.125인치 / ICC USWebCoatedSWOP)과 기능 요구사항(표지·내지·QR·POD API·서버리스)에 1:1로 매핑하여 작성함.

## 3. 실현 가능성 분석 (내부용)

- 프로젝트 유형: Python 모듈 개발 + 이미지 처리 + 외부 API 연동 (서버리스 호환) → **가능 (+10% 버퍼)**
- 기본 공수 분해 (AI 보조 없이):
  - 기획/설계 (PRD, API 설계, 인쇄 사양 정리): 3 M/D
  - PDF 빌더 코어 + 레이아웃 + 표지 + 폰트: 6 M/D
  - CMYK / ICC / 블리드 / PDF/X 메타데이터: 3.5 M/D
  - QR / 페이지번호 / 보조: 1.5 M/D
  - POD API 연동 (Printful/Blurb) + webhook: 2.5 M/D
  - 테스트 + Vercel 검증: 3 M/D
  - 문서 + 패키징 + 인계: 2.5 M/D
  - **합계 약 22 M/D**
- AI 절감률 50% 적용 → 약 11 M/D
- 버퍼 +10% → 약 12 M/D
- 달력 일수 변환 (× 7/5, 1인 순차) → 약 17일
- 클라이언트 예상 기간 vs 산정 기간: 45일 vs 17일 (산정이 충분히 짧음)
- 판정: 클라이언트 기간 안에서 충분히 수행 가능. 제안 기간을 17일로 잡으면 신뢰도가 떨어지므로 **30일** 제안(정부지원사업 안정성·검수 일정·POD 변경 대응 버퍼 확보).

## 4. 포트폴리오 매칭

매칭 기준: Python 모듈 / 외부 API 다수 연동 / 자동 문서 생성 / 규제·정합성 검증 / 패키지 납품.

| 순위 | 프로젝트 | 매칭 점수 (자체) | 근거 |
|---|---|---|---|
| 1 | P2P 크라우드펀딩 플랫폼 | ★★★★★ | 동일 언어(Python/Django), 외부 API 15+ 연동, 자동화 크론잡, 규제 환경 → POD API + 정부지원사업 정산 절차에 직접 활용 |
| 2 | AI Agent (모듈 프레임워크) | ★★★★ | 134+ 스킬을 단일 인터페이스 모듈로 패키징한 경험, 입출력 스키마·테스트·어댑터 패턴 → pip install 가능 모듈 납품과 동일 구조 |
| 3 | VC 펀드 관리 플랫폼 (Series-B) | ★★★★ | "정해진 규격의 문서를 자동 출력"하는 도메인(VICS 양식 PDF 5종 자동 출력), 외부 API + webhook 처리 |

## 5. 최종 제안 요약

- **지원 금액**: 7,650,000원 (VAT 별도) — 클라이언트 예산 상한 900만원의 85%
- **지원 기간**: 30일 — 클라이언트 45일 대비 단축, 정부지원사업 안정성 확보 + 마일스톤 검수 일정 여유
- **핵심 제안 포인트**:
  1. 인쇄 규격(8.5×8.5/300DPI/CMYK/블리드/ICC) 정합성을 1순위로 하는 `PrintSpec` 추상화 설계 — 사이즈·POD 업체 변경 시 설정값 교체로 대응
  2. Pillow + LittleCMS 기반 sRGB→CMYK 색관리 파이프라인 + ICC 프로파일(USWebCoatedSWOP) 명시 적용
  3. 외부 바이너리 의존 없는 순수 Python 라이브러리 위주 구성 → Vercel Serverless 단일 wheel 배포 보장
  4. pytest + 샘플 데이터 + Vercel 호출 예제 + README 풀 패키지 납품
  5. 정부지원사업 견적서 / 보증보험 / 마일스톤 검수 / 1개월 무상 하자보수 운영
- **클라이언트 사전 검증 질문**: 모두 "예" — 서버리스(Vercel/AWS Lambda) 배포 경험 + 인쇄 규격(CMYK/블리드/ICC) 경험 모두 충족

## 6. 최종 산출물 (8단계 출력 전문)

### 6-1. 제안서 사이트 URL

```
https://proposal-router.claude-ai-b27.workers.dev/proposal-pod-pdf-builder/
```

### 6-2. 지원 금액

```
7,650,000원
```

### 6-3. 지원 기간

```
30일
```

### 6-4. 클라이언트 질문 답변

**Q: 서버리스 환경(Vercel/AWS Lambda) 배포 경험이 있으십니까?**

예, 다수 보유하고 있습니다.

- Vercel Serverless Functions / AWS Lambda 환경에서 Python 및 Node.js 모듈을 배포·운영한 경험이 있습니다.
- 콜드스타트 시간, 메모리 한도(Vercel 1024MB / Lambda 기본 한도), 실행 시간 한도, 파일 시스템 제약(/tmp 사용 등)을 고려한 패키지 설계에 익숙합니다.
- 본 프로젝트에서도 외부 바이너리(ImageMagick) 의존을 최소화하고 순수 Python 라이브러리(Pillow, fpdf2/ReportLab, qrcode) 위주로 구성하여 단일 wheel 패키지로 Vercel Serverless에서 안정 호출되도록 설계할 예정입니다. 콜드스타트·메모리·실행시간 측정 결과를 문서화하여 인계해 드립니다.

**Q: 인쇄 규격 맞춤 + CMYK + 블리드 경험이 있으십니까?**

예, 보유하고 있습니다.

- 고정 양식(VICS 규제 5종 등)의 자동 PDF 출력 프로젝트를 수행하면서 PDF/X 호환 메타데이터, 트림박스 / 블리드박스 / 안전영역 처리 경험이 있습니다.
- Pillow + LittleCMS 기반 sRGB→CMYK 변환 파이프라인 구성 경험이 있으며, 본 프로젝트 요구 ICC 프로파일(USWebCoatedSWOP)을 명시적으로 적용하여 모니터-인쇄 간 색차를 최소화합니다.
- 8.5×8.5인치 / 300 DPI / 블리드 0.125인치(사방) 사양을 단일 `PrintSpec` 객체로 추상화하여, 사이즈 변경(추후 사이즈 변동 가능 명시)이나 POD 업체 변경(Printful↔Blurb) 시 코드 수정 없이 설정값 교체로 대응 가능한 구조로 설계합니다.

### 6-5. 지원 내용 (위시켓 폼 "지원 내용" 필드 입력 본문)

```
안녕하세요, 인쇄용 PDF 자동 조립 Python 모듈 개발 프로젝트에 지원합니다.

본 프로젝트에 대한 상세 제안서(견적서, 공수계산서, PRD, 일정, 포트폴리오)를 별도 페이지로 준비하였습니다. 아래 링크에서 확인해 주시면 감사하겠습니다.
▶ 제안서 상세 페이지: https://proposal-router.claude-ai-b27.workers.dev/proposal-pod-pdf-builder/
▶ 위시켓 포트폴리오: https://www.wishket.com/partners/p/blueverse1/

---

<프로젝트 진행 제안>

■ 프로젝트 분석
- 8.5×8.5인치 / 300 DPI / CMYK / 블리드 0.125인치 / 표지+내지 20페이지 / 하드커버 무선제본 사양을 모두 충족하는 인쇄용 PDF를 자동 생성하는 Python 모듈 개발
- 핵심 도메인: 인쇄 규격 정합성(PDF/X 호환), sRGB→CMYK 색관리(ICC USWebCoatedSWOP), 표지·내지 자동 조립, OTF/TTF 폰트 임베딩, QR 코드 동적 삽입, POD API 연동(Printful/Blurb), Vercel Serverless 호출 가능 구조
- 정부지원사업 정산 요건(견적서 발행, 보증보험 발급, 마일스톤 검수)을 충족하도록 일정·산출물 표준화

■ 작업 일정

[Phase 1] Day 1–4 — 기획 / 설계
- PRD, 모듈 인터페이스 설계, 인쇄 규격 사양서, POD 업체 1차 결정

[Phase 2] Day 5–12 — 코어 모듈 개발
- PDF 빌더, 내지 레이아웃 엔진(풀블리드/마진/텍스트박스), 표지 자동 조립, OTF/TTF 폰트 임베딩, 1차 샘플 PDF

[Phase 3] Day 13–20 — 색공간 / QR / POD API
- sRGB→CMYK 변환, ICC 프로파일(USWebCoatedSWOP) 적용, 블리드·트림박스, QR 자동 삽입, Printful/Blurb 연동(선택), webhook 샘플

[Phase 4] Day 21–26 — 테스트 / 서버리스 / 문서
- pytest 단위 테스트, Vercel Serverless 호출 검증, 콜드스타트·메모리 측정, README·API 문서·샘플 데이터, pip install 가능 패키지 빌드

[Phase 5] Day 27–30 — 검수 / 인계 / 하자보수 시작
- 최종 검수 반영, 패키지 인계, 인계 미팅, 1개월 무상 하자 보수 시작

■ 마일스톤 및 산출물
- M1 (Day 4): 설계 검토 — PRD·인쇄 규격 사양서 승인
- M2 (Day 12): 1차 샘플 PDF — 표지+내지 20페이지 sRGB PDF 시연
- M3 (Day 20): 인쇄 규격 충족 — CMYK+ICC+블리드+QR 검수, POD 데모
- M4 (Day 26): 통합 검수 — 테스트·Vercel 호출·문서 검토 통과
- M5 (Day 30): 최종 인수 — 패키지 인계, 잔금 청구 / 하자 보수 시작

■ 미팅 시 협의 필요 사항
- 인쇄 규격 최종 확정 (8.5×8.5인치 외 다른 사이즈 가능성)
- POD 업체 선정 (Printful / Blurb 중 1개 또는 양쪽 어댑터 모두 구현 여부)
- ICC 프로파일 (USWebCoatedSWOP 외 인쇄소 지정 프로파일 여부)
- 폰트 라이선스 (OTF/TTF 발주처 보유 여부, 임베딩 권한)
- 전체 서비스 아키텍처 자료 공유 (Vercel 함수 호출 방식, 입출력 포맷 최종 확정)
- 정부지원사업 정산 일정 및 마일스톤 검수 양식

---

<유사 프로젝트 진행 경험>

▶ P2P 크라우드펀딩 플랫폼 (약 2개월)
- 프로젝트 유형: 핀테크 / P2P 대출 / 외부 API 다수 연동
- 핵심 기능: P2P 분할 투자, NICE KYC(CheckPlus, SafeKey, NPAC), 가상계좌 자동화(Seyfert/PayGate), 4종 대출 유형, 3 크론잡 운영 자동화, 15+ 외부 API 통합
- 유사점: 동일 언어(Python/Django) 기반 모듈·자동화 개발, 외부 API 다수 연동(POD API 안정 연동에 직결), 규제 환경에서의 산출물 표준화 경험을 정부지원사업 정산 절차에 그대로 활용 가능
- 기술 스택: Python, Django, MySQL, AWS S3

▶ AI Agent (모듈 기반 자동화 프레임워크) (진행 중)
- 프로젝트 유형: AI / 자동화 / 모듈 프레임워크
- 핵심 기능: 134+ 스킬 모듈, 12 품질 게이트, MCP / 외부 도구 통합, 표준 입출력·검증 스키마
- 유사점: "단일 모듈 = 단일 책임" 패키지 설계 철학과 입출력 스키마 검증·테스트 자동화·어댑터 패턴 운영 경험으로, pip install 가능 Python 모듈 납품과 POD 업체 변경 대응 구조에 직결
- 기술 스택: TypeScript, Python, MCP, PostgreSQL

▶ VC 펀드 관리 플랫폼 (약 14개월)
- 프로젝트 유형: 핀테크 / VC / 자동 문서 생성
- 핵심 기능: AI 투자 보고서 자동 생성(ChatGPT 연동), VICS 규제 5종 양식 PDF 자동 출력, NICE KYC, 외부 API 다수 연동, 실시간 공동편집, 200~300+ API 엔드포인트
- 유사점: "정해진 규격의 문서를 자동으로 조립·출력"하는 도메인 경험(VICS 양식 자동 출력)을 인쇄 규격 PDF 자동 조립에 그대로 활용 + webhook 처리·외부 API 연동 패턴 동일
- 기술 스택: Next.js, NestJS, MySQL, AWS

---

<사용 기술과 툴>

▶ 개발 기술
- 언어: Python 3.10+
- PDF 라이브러리: fpdf2 / ReportLab (협의 가능)
- 이미지 / 색관리: Pillow, LittleCMS, ICC 프로파일(USWebCoatedSWOP)
- QR 코드: qrcode
- 검증 / 테스트: Pydantic, pytest
- POD 연동: Printful / Blurb API + webhook
- 실행 환경: Vercel Serverless / AWS Lambda 호환

▶ 개발 도구 및 인프라
- 버전 관리: GitHub
- CI/CD: GitHub Actions (선택)
- 클라우드: Vercel Serverless (발주처 환경) / AWS Lambda 호환
- 패키징: pip install 가능 wheel / sdist

▶ 커뮤니케이션
- 일일 진행 공유: Slack 또는 카카오톡
- 주간 미팅: Zoom / Google Meet
- 문서 공유: Notion 또는 Google Docs
- 이슈 트래킹: GitHub Issues
```

### 6-6. 관련 포트폴리오 추천

1. **P2P 크라우드펀딩 플랫폼** — Python/Django 기반 외부 API 15+ 연동·자동화 운영 경험으로 POD API 연동·정부지원사업 정산 적합성 확보
2. **AI Agent (모듈 프레임워크)** — 134+ 스킬을 단일 인터페이스 모듈로 패키징한 경험으로 pip install 가능 Python 모듈 납품 구조에 직결
3. **VC 펀드 관리 플랫폼 (Series-B)** — VICS 규제 양식 자동 PDF 출력 + 외부 API + webhook 처리 경험으로 인쇄 규격 PDF 자동 조립과 POD 연동에 직결
