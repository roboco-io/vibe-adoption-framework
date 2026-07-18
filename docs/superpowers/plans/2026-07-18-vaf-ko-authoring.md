# VAF 한국어 본문(VAF-ko.md) 집필 계획

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking. 이 계획은 사용자 심층인터뷰 체크포인트를 포함하므로 서브에이전트 위임이 아닌 인라인 실행을 전제로 한다.

**Goal:** 설계 문서(`docs/superpowers/specs/2026-07-18-vaf-design.md`)에 따라 VAF 한국어 본문 `VAF-ko.md`와 `README.md`를 완성한다.

**Architecture:** 단일 마크다운 문서를 목차 순서대로 태스크화한다. 각 태스크는 "세부 결정 인터뷰(필요 시) → 집필 → 검증 체크리스트 → 커밋" 사이클을 따른다. Perspective 6개는 각각 capability 목록을 인터뷰로 확정한 뒤 집필한다.

**Tech Stack:** 마크다운, mermaid 다이어그램, git

## Global Constraints

설계 문서 9장(서술 톤 가이드)을 모든 태스크에 적용한다:

- Prescriptive 권고: "~를 수립하라", "~를 고려하라" 형태의 행동 지시. 단순 개념 설명 금지
- 컨설팅적 유연함: 조직 맥락을 존중하는 조동사("고려하라", "평가하라") 사용
- 아웃컴 지향: 각 권고를 기대 효과와 연결
- 일반성 유지: 특정 산업·규모 비종속. 사례는 익명·일반화("로보코의 컨설팅 경험에서 도출한 패턴")
- 도구 중립: 개념은 중립 용어(에이전트, 규칙 파일, 스킬, 훅), 예시는 구체(Claude Code, AGENTS.md 등)
- 관통 원리 3개(에이전트=인력 레버리지, 오너십 원칙, 인지부채 관리)가 모든 perspective 서술에 반영되어야 함
- 용어 표기: perspective/capability/domain 등 프레임워크 용어는 한국어(영어) 병기 후 한국어 사용
- 각 태스크 종료 시 `git add VAF-ko.md && git commit` (메시지에 Co-Authored-By: Claude Fable 5 <noreply@anthropic.com> 포함)

**공통 검증 체크리스트** (각 집필 스텝 후 실행):

1. 톤 가이드 5개 항목 준수 여부를 섹션 전체에 대해 확인
2. 설계 문서의 해당 장과 내용 일치 확인 (임의 확장·누락 금지)
3. 이미 집필된 앞 장과 용어·개념 일관성 확인

---

### Task 1: README.md와 VAF-ko.md 골격 생성

**Files:**
- Create: `README.md`
- Create: `VAF-ko.md`

**Interfaces:**
- Produces: VAF-ko.md의 7개 장 헤딩 구조. 이후 모든 태스크가 이 골격의 해당 장을 채운다

- [ ] **Step 1: README.md 작성**

내용: 프로젝트 한 줄 소개(기존 기업의 바이브 코딩 도입을 위한 프레임워크), 문서 링크(VAF-ko.md, 추후 en/ja), 로보코 소개 한 줄, 라이선스 표기는 미정이므로 생략

- [ ] **Step 2: VAF-ko.md 골격 작성**

문서 제목 + 설계 문서 7장의 목차를 `##` 헤딩으로 생성:

```markdown
# Vibe Adoption Framework (VAF)

## 1. 개요 (Executive Summary)
## 2. 대전제와 관통 원리
## 3. 프레임워크 구조와 Value Chain
## 4. Transformation Domain
## 5. Perspective와 Capability
## 6. 도입 여정
## 7. 부록: 실행 키트
```

- [ ] **Step 3: 커밋**

```bash
git add README.md VAF-ko.md
git commit -m "docs: README와 VAF-ko.md 골격 추가"
```

### Task 2: 1장 개요 + 2장 대전제와 관통 원리

**Files:**
- Modify: `VAF-ko.md` (1장, 2장)

**Interfaces:**
- Produces: 관통 원리 3개와 핵심 개념 2개(하네스 엔지니어링, 취향/비취향 구분)의 공식 정의 문구. 이후 모든 장이 이 정의를 재사용한다

- [ ] **Step 1: 1장 개요 집필**

포함 내용: VAF 한 문단 정의(로보코의 컨설팅 경험 기반), 왜 지금인가(에이전트 역량의 변곡점), 기대 아웃컴(리드타임 단축, 품질 향상, 개발 비용 구조 변화), 프레임워크 3축 한 문단 예고. 분량: 경영진이 이 장만 읽어도 되는 수준(1~1.5페이지)

- [ ] **Step 2: 2장 대전제와 관통 원리 집필**

포함 내용: 대전제(바이브 코딩은 기존 SW 개발 베스트 프랙티스·안티패턴을 계승한다) → 관통 원리 3개 각각 정의+함의 → 이름 붙은 핵심 개념 2개 정의(하네스 엔지니어링: 사람이 하던 리뷰·가드레일을 AI가 대신하는 체계 / 취향·비취향 구분: 비취향(보안·가드레일·코딩 규약)은 저장소와 함께 강제, 취향(문서화 레벨 등)은 극히 제한적 허용). 인지부채는 기술부채와의 대비로 설명

- [ ] **Step 3: 공통 검증 체크리스트 실행**

- [ ] **Step 4: 커밋**

```bash
git add VAF-ko.md
git commit -m "docs: VAF 1장 개요, 2장 대전제와 관통 원리"
```

### Task 3: 3장 프레임워크 구조와 Value Chain + 4장 Transformation Domain

**Files:**
- Modify: `VAF-ko.md` (3장, 4장)

**Interfaces:**
- Consumes: 2장의 관통 원리·핵심 개념 정의
- Produces: 3축 구조 다이어그램, Domain 4개의 공식 명칭과 AsIs→ToBe 정의. 5장(perspective 매핑), 6장(여정 단계)이 참조

- [ ] **Step 1: 3장 집필**

포함 내용: 3축(6 perspective / 여정 4단계 / domain 4개) 소개, mermaid 다이어그램으로 Value Chain 표현(에이전트 역량 → 도입(capability) → Domain 전환 → 비즈니스 아웃컴), 각 축의 역할 설명과 Knowledge의 perspective/domain 축 구분 명시

- [ ] **Step 2: 4장 집필**

설계 문서 6장의 Domain 4개(코드 생산/품질 보증/지식/조직과 역할)를 각각 소절로: AsIs→ToBe 서술, 전환을 뒷받침하는 perspective 매핑, 전환이 만드는 아웃컴

- [ ] **Step 3: 공통 검증 체크리스트 실행**

- [ ] **Step 4: 커밋**

```bash
git add VAF-ko.md
git commit -m "docs: VAF 3장 프레임워크 구조, 4장 Transformation Domain"
```

### Task 4: 5장 Perspective 1~3 (사람·조직 관점)

**Files:**
- Modify: `VAF-ko.md` (5장 전반부)

**Interfaces:**
- Consumes: 2장 관통 원리 정의, 설계 문서 4장의 capability 초안
- Produces: Strategy / People & Ownership / Governance & Guardrails의 확정 capability 목록과 정의. 7장 어세스먼트 체크리스트가 참조

- [ ] **Step 1: 심층인터뷰로 capability 확정**

AskUserQuestion으로 perspective 3개 각각의 capability 목록(설계 문서 초안 기반 4~6개)을 제안하고 추가·삭제·명칭을 확정받는다

- [ ] **Step 2: 5장 도입부 + Perspective 1~3 집필**

각 perspective 구조: 정의(핵심 질문) → 이해관계자 → capability별 소절(정의, prescriptive 권고 2~4개, 기대 아웃컴, 안티패턴 1개 이상)

- [ ] **Step 3: 공통 검증 체크리스트 실행**

- [ ] **Step 4: 커밋**

```bash
git add VAF-ko.md
git commit -m "docs: VAF 5장 Perspective 1~3 (Strategy, People & Ownership, Governance & Guardrails)"
```

### Task 5: 5장 Perspective 4~6 (에이전트 기술 관점)

**Files:**
- Modify: `VAF-ko.md` (5장 후반부)

**Interfaces:**
- Consumes: Task 4와 동일 구조
- Produces: Agent Environment / Knowledge / Harness Engineering의 확정 capability 목록과 정의

- [ ] **Step 1: 심층인터뷰로 capability 확정** (Task 4 Step 1과 동일 방식)

- [ ] **Step 2: Perspective 4~6 집필** (Task 4 Step 2와 동일 구조)

- [ ] **Step 3: 공통 검증 체크리스트 실행**

- [ ] **Step 4: 커밋**

```bash
git add VAF-ko.md
git commit -m "docs: VAF 5장 Perspective 4~6 (Agent Environment, Knowledge, Harness Engineering)"
```

### Task 6: 6장 도입 여정

**Files:**
- Modify: `VAF-ko.md` (6장)

**Interfaces:**
- Consumes: 5장의 확정 capability 목록(단계별 활동에서 참조), 4장 Domain 정의
- Produces: 단계별 산출물·완료 기준 목록. 7장 워크숍 가이드가 참조

- [ ] **Step 1: 심층인터뷰로 단계별 세부 확인**

AskUserQuestion으로 확인: 각 단계의 완료 기준, 파일럿 선정 기준(로보코 컨설팅에서 쓰는 기준), 전환 단계의 성과 지표 후보

- [ ] **Step 2: 6장 집필**

준비→진단→파일럿→전환 각 단계를 소절로: 목표, 핵심 활동(설계 문서 5장 기반), 산출물, 완료 기준, 관련 capability 참조. 반복 사이클임을 도식(mermaid)으로 표현. "진단보다 환경 준비가 먼저"인 이유를 강조

- [ ] **Step 3: 공통 검증 체크리스트 실행**

- [ ] **Step 4: 커밋**

```bash
git add VAF-ko.md
git commit -m "docs: VAF 6장 도입 여정"
```

### Task 7: 7장 부록 실행 키트

**Files:**
- Modify: `VAF-ko.md` (7장)

**Interfaces:**
- Consumes: 5장 확정 capability 전체(어세스먼트 항목), 6장 단계 정의(워크숍 가이드)

- [ ] **Step 1: 어세스먼트 체크리스트 작성**

5장의 모든 capability에 대해 성숙도 3단계(부재/부분/정착) 판별 질문 각 1개 이상. 표 형식

- [ ] **Step 2: 심층인터뷰 질문지 작성**

진단 단계용 질문지: 비즈니스 현안, IT 현안, SDLC 현황(AsIs), 지식 관리 현황 영역별 질문 목록

- [ ] **Step 3: 워크숍 가이드 + 용어집 작성**

진단 워크숍·파일럿 착수 워크숍의 목적/참석자/아젠다/산출물. 용어집: 본문 등장 프레임워크 용어 전체(한/영 병기)

- [ ] **Step 4: 공통 검증 체크리스트 실행**

- [ ] **Step 5: 커밋**

```bash
git add VAF-ko.md
git commit -m "docs: VAF 7장 부록 실행 키트"
```

### Task 8: 전체 정합성 리뷰와 마무리

**Files:**
- Modify: `VAF-ko.md`, `README.md`

- [ ] **Step 1: 전체 통독 리뷰**

체크: 용어 일관성(용어집과 대조), 장 간 상호참조 정확성, 관통 원리가 5장 전체에 실제 반영되었는지, mermaid 렌더링 확인, 목차와 실제 헤딩 일치

- [ ] **Step 2: README.md에 완성된 문서 요약 반영**

- [ ] **Step 3: 사용자 최종 리뷰 요청** — 승인 시 커밋

```bash
git add VAF-ko.md README.md
git commit -m "docs: VAF 한국어 본문 완성 및 정합성 리뷰 반영"
```
