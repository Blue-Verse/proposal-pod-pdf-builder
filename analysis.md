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

- **지원 금액**: 8,100,000원 (VAT 별도) — 클라이언트 예산 상한 900만원의 90%
- **지원 기간**: 30일 — 클라이언트 45일 대비 단축, 정부지원사업 안정성 확보 + 마일스톤 검수 일정 여유
- **핵심 제안 포인트**:
  1. 인쇄 규격(8.5×8.5/300DPI/CMYK/블리드/ICC) 정합성을 1순위로 하는 `PrintSpec` 추상화 설계 — 사이즈·POD 업체 변경 시 설정값 교체로 대응
  2. Pillow + LittleCMS 기반 sRGB→CMYK 색관리 파이프라인 + ICC 프로파일(USWebCoatedSWOP) 명시 적용
  3. 외부 바이너리 의존 없는 순수 Python 라이브러리 위주 구성 → Vercel Serverless 단일 wheel 배포 보장
  4. pytest + 샘플 데이터 + Vercel 호출 예제 + README 풀 패키지 납품
  5. 정부지원사업 견적서 / 보증보험 / 마일스톤 검수 / 1개월 무상 하자보수 운영
- **클라이언트 사전 검증 질문**: 모두 "예" — 서버리스(Vercel/AWS Lambda) 배포 경험 + 인쇄 규격(CMYK/블리드/ICC) 경험 모두 충족

## 6. 최종 산출물 (8단계 출력 전문)

(8단계 완료 후 추가 예정)
