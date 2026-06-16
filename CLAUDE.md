# 파란수박 (Blue Watermelon) — Claude Code 인수인계 문서

> 이 파일은 Claude Code가 파란수박 프로젝트를 이어받을 때
> 반드시 먼저 읽어야 하는 전체 맥락 문서다.
> 모든 작업 전에 이 파일을 읽고 시작할 것.

---

## 1. 프로젝트 개요

**파란수박**은 1인 출판사다.
대표: 정동훈 (Denny) | 연락처: donghoon807@gmail.com
도메인: bluewatermelon.co.kr
GitHub: github.com/denny-cyber-beyond/bluewatermelon

---

## 2. 세계관 (가장 중요 — 모든 콘텐츠의 근거)

### 핵심 설정
- 외계인들이 지구 궤도 근처에서 오랫동안 지구를 관찰해왔다
- 지구인들이 우주 활동을 시작하자 **달 뒷면에 우주선을 집결·정박**시켰다
- 달 표면의 굴곡을 골프공처럼 활용한 전파 반사 기술로 지구와 통신
- 외계인들이 최초 착륙한 곳: **대한민국 전라남도 화순군 이양면 쌍봉리 쌍봉마을**
- 무등산 자락에서 수박을 발견하고 지구를 **"파란 수박"** 으로 명명
- 책이라는 형태의 기록 방식을 발견했으나, 특별한 사람만 책을 쓰는 현실에 아쉬움
- 그래서 **출판사를 세워 모든 지구인이 저자가 되게 하는 것**이 목표

### 팀 설정
- 외계인들이 포섭한 지구인들이 우주선에 탑승해 함께 일하고 있다
- 팀원 소개는 "외계인에게 포섭된 지구인" 형식으로 작성
- #001 정동훈(Denny): 공군 중사 출신, CEO/Keroro
  - 포섭 일화: 외계인이 도로로를 추천했으나 "도로로는 병장, 나는 중사"라며 케로로를 선택

### 섹션별 컨셉
| 섹션 | 한국어명 | 영어명 | 컨셉 |
|------|---------|--------|------|
| 세계관 | 보고서 | REPORT | 달 뒷면 본부에서 본 행성으로 보고 |
| 프로젝트 | 실험실 | LAB | 지구인 기록 실험들 |
| 팀 소개 | 파란수박본부 | B.W.H.Q | 포섭된 지구인들 |
| 문의 | 안녕하세요? | HELLO? | 항성 간 통신 시도 |

---

## 3. 브랜드 아이덴티티

### 컬러 시스템 (변경 불가)
| 이름 | 코드 | 의미 |
|------|------|------|
| 파아란파랑 | `#2B3EE8` | 외계인이 본 지구, 바다와 물 |
| 새초롬초록 | `#2DBD6E` | 수박 겉껍질, 세상의 새초롬함 |
| 속마음분홍 | `#FC5C7D` | 수박 과육, 모두의 따뜻한 속마음 (별똥별로 표현) |
| 심우주 | `#080810` | 배경 베이스 |
| 달뒷면 | `#ffffff` | 텍스트 베이스 |

### 로고 파일
- `9.png`: 라인+텍스트 세로 배치 로고 → 네비바용
- `1.png`: 파란 채움 심볼 → 파비콘용
- 심볼: 원+파동선 (우편 소인 모티프, 전파 송수신 상징)
- `1~11.png`: 컬러별 버전 전체

### 폰트
- 한국어 본문: Noto Serif KR
- UI/레이블: Space Grotesk
- fallback: Georgia, system-ui

---

## 4. 홈페이지 기술 스펙

### 배포 환경
- GitHub Pages: denny-cyber-beyond.github.io/bluewatermelon → bluewatermelon.co.kr
- DNS: 가비아 A레코드 4개 + CNAME www

### 파일 구조
```
bluewatermelon/          ← GitHub 루트 (모든 파일이 루트에 있어야 함)
├── index.html           ← 랜딩 페이지
├── report.html          ← 보고서
├── lab.html             ← 실험실
├── hq.html              ← 파란수박본부
├── contact.html         ← 안녕하세요?
├── member-001.html      ← 정동훈 개인 페이지 (준비중)
├── style.css            ← 공통 CSS (모든 페이지 공유)
├── 1.png ~ 11.png       ← 로고 시리즈
├── CNAME                ← bluewatermelon.co.kr
└── .claude/
    └── agents/          ← AI 에이전트 정의 파일들
```

### CSS 핵심 변수 (style.css)
```css
:root {
  --black:  #080810;
  --blue:   #2B3EE8;
  --green:  #2DBD6E;
  --pink:   #FC5C7D;
  --white:  #ffffff;
  --dim:    #16162A;
  --border: rgba(255,255,255,0.08);
  --serif: 'Noto Serif KR', Georgia, serif;
  --sans:  'Space Grotesk', system-ui, sans-serif;
}
```

### 공통 컴포넌트 (모든 페이지 동일)
**네비 (.site-nav)**
```html
<nav class="site-nav" id="site-nav">
  <a href="index.html" class="nav-logo">
    <img src="9.png" alt="파란수박" onerror="...">
  </a>
  <ul class="nav-links">
    <li><a href="report.html" data-ko="보고서" data-en="REPORT">보고서</a></li>
    <li><a href="lab.html" data-ko="실험실" data-en="LAB">실험실</a></li>
    <li><a href="hq.html" data-ko="파란수박본부" data-en="B.W.H.Q">파란수박본부</a></li>
    <li><a href="contact.html" data-ko="안녕하세요?" data-en="HELLO?">안녕하세요?</a></li>
  </ul>
  <div class="nav-lang" id="nav-lang" onclick="toggleLang()">EN</div>
</nav>
```
**푸터 (.site-footer)**: 3단 그리드 — 브랜드/페이지링크/연락처
**한/영 전환**: `data-ko` / `data-en` 속성으로 전환, `toggleLang()` 함수

### 랜딩 페이지 핵심 구조
- 배경: Canvas 별 파티클 (z-index:1)
- CSS 지구: 화면 하단 절반 배치 (z-index:2, pointer-events:none)
- 히어로 카피: `position:absolute; top:50%; left:50%; transform:translate(-50%,-50%)` (z-index:10)
- 별똥별: Canvas에서 직접 그림 (CSS ::after 사용 금지 — 방향이 틀어짐)
  - 방향: 오른쪽 위 → 왼쪽 아래 대각선 (angle: PI * 0.6~0.7)
  - 색상: #FC5C7D (속마음분홍)
  - 꼬리: 머리에서 진행 반대 방향으로 그라디언트

**메인 카피**
```
우리는
[바뀌는 텍스트]보다
당신이 쓰는 책이 궁금해
```
바뀌는 텍스트 목록: 100억 자산가 / 5선 국회의원 / 대기업 대표 / 1천만 인플루언서 / 유명 연예인 / 노벨상 수상자

**통계 바** (히어로 하단): 진행 중인 프로젝트 2 / 잠재적 지구인 저자 ∞ / 달 뒷면 본부 1

### 디자인 원칙
- 텍스트는 흰색 기본 (`#ffffff`), 회색 최소화
- 네비 링크: 최소 16px
- 섹션 레이블: 최소 16px
- 본문: 최소 18px
- 레퍼런스: satreci.com, nearthlab.com, naraspace.com (다크, 풀스크린, 한영 혼용 타이포)
- **애니메이션으로 나타나는 요소(`opacity:0` + animation)는 반드시 `prefers-reduced-motion` fallback을 둘 것**
  (없으면 '동작 줄이기' OS 설정에서 영구히 안 보임 — 과거 히어로 카피 미표시 원인)

### 현재 미해결 이슈
1. ~~**랜딩 히어로 카피 안 보임**~~ → 해결됨
   - 1차 원인: hero-content position/z-index (→ `position:absolute; top:50%`로 고정)
   - 2차 원인(실제): `prefers-reduced-motion` 환경에서 애니메이션이 죽어 `opacity:0` 고착
     → 히어로 요소에 reduced-motion fallback(`opacity:1`) 추가로 해결
2. **로고(9.png) 표시 불안정**: 네비바에서 간헐적으로 안 보임
   - onerror로 텍스트 fallback 추가되어 있음

---

## 5. 페이지별 콘텐츠

### index.html (랜딩)
- 별 파티클 + 속마음분홍 별똥별 + CSS 지구
- 메인 카피 타이핑 애니메이션
- 하단 통계 바
- 단일 CTA: "파란수박 알아보기 →" → report.html (텍스트 링크 스타일)

### report.html (보고서)
4챕터 구조:
1. 우리는 오래전부터 지구 곁에 있었다 (달 뒷면 본부 설치)
2. 파란 수박을 발견하다 (화순군 쌍봉마을, 수박 명명)
3. 책이라는 가장 오래된 기록 (출판의 의미)
4. 그래서 우리는 출판사를 만들었다
+ 브랜드 아이덴티티 섹션 (로고 설명 + 3색 의미)

### lab.html (실험실)
- 제목: "파란수박 프로젝트 기획."
- BW-01: 프로젝트 풍영정 (#오천만권짜리시리즈 #너도나도모두작가 #외계인이들려주는)
- BW-02: 프로젝트 쿵쿵따 (#쿵쿵따리쿵쿵따 #쿵쓰쿵쓰 #철인3종팀경기)
- 모두 "준비 중" 상태

### hq.html (파란수박본부)
- #001 정동훈 / Denny / CEO·Keroro
- 종: 호모 사피엔스 (라고 주장) / 서식지: 파란수박
- 포섭 일화: 공군 중사, 도로로→케로로 에피소드
- 카드 클릭 시 member-001.html로 이동
- 빈 카드: "다음 포섭 대상 모집 중" → contact.html 연결

### contact.html (안녕하세요?)
- 이메일: donghoon807@gmail.com
- 컨셉: 항성 간 통신 (달 표면 굴곡 전파 반사 기술)
- "신호 발송하기 →" 버튼

### member-001.html
- 정동훈 개인 페이지 (현재 준비중 플레이스홀더)
- 나중에 사진 + 개인 스토리 추가 예정

---

## 6. 행정 현황 (2026.06.16 기준)

| 항목 | 상태 | 상세 |
|------|------|------|
| 출판사 신고 | ✅ 완료 | 제2026-000045호, 서울 노원구 |
| 사업자등록 | ⏳ 처리중 | 처리기한 6/18, 면세, 출판업+SW개발 |
| 발행자번호 | ⏳ 접수 | seoji.nl.go.kr 신청완료 |
| 도메인 | ✅ 완료 | bluewatermelon.co.kr (가비아) |
| GitHub Pages | ✅ 운영중 | 자동 배포 |

### 사업자 등록 정보
- 업태: 정보통신업
- 종목: 출판업 (581000) + 응용SW개발 (722000)
- 과세유형: 면세
- 사업장: 서울 노원구 동일로241길 53 (자택)

### 사업자등록증 나오면 할 것
1. 사업자 통장 개설
2. 부크크(bookk.co.kr) 출판사 계정 등록
3. 발행자번호 승인 후 더 베테랑 ISBN 신청

---

## 7. 출판 프로젝트

### 더 베테랑 (7월 출간 목표)
- 부제: 세계 군 창업 백과
- 완성 섹션: 3.1 (Kalashnikov/Shield AI), 3.3 (SOPMOD/True Anomaly), 7.1, 7.3
- 미완성: 3.2 (Wiz/Unit 8200)
- 디자이너 외주: 표지+내지 PDF (부크크 규격 맞춤)
- 유통: 부크크 → 교보/알라딘/YES24 동시

### BW-01: 프로젝트 풍영정
- 모든 지구인이 글을 쓰는 프로젝트
- 준비 중

### BW-02: 프로젝트 쿵쿵따
- 모두가 함께 글을 쓰는 프로젝트
- 준비 중

---

## 8. 에이전트 역할 분담

`.claude/agents/` 에 정의됨. 작업 성격에 맞는 에이전트를 호출한다.

| 에이전트 | 파일 | 담당 |
|---------|------|------|
| 웹 에이전트 | web-agent.md | HTML/CSS 수정, 홈페이지 개선 |
| 출판 에이전트 | publishing-agent.md | 원고 교정, ISBN, 부크크 |
| 마케팅 에이전트 | marketing-agent.md | 홍보, 이메일, SNS |
| 대필 에이전트 | ghostwriting-agent.md | AI 인터뷰, 원고화 |
| 행정 에이전트 | admin-agent.md | 사업자, 세무, 행정 |

---

## 9. 작업 규칙

### 코드 수정 시
1. 수정 전 현재 파일 내용 확인 (view 툴 사용)
2. 변경사항 최소화 — 필요한 부분만 수정
3. 작업 완료 후 변경 파일 목록과 변경사항 한국어로 요약
4. 수정 후 자동으로 commit → push (GitHub Pages 라이브 즉시 배포)

### 글쓰기 시
- 이오덕 「우리글 바로쓰기」 원칙 적용
- `~의` 구문 최대한 제거
- 간결하고 담백한 문장
- hook-first (첫 문장에 핵심)

### 절대 바꾸지 말 것
- 세계관 설정 (외계인, 달 뒷면, 파란수박 명명 스토리)
- 컬러 코드 (파아란파랑 #2B3EE8, 새초롬초록 #2DBD6E, 속마음분홍 #FC5C7D)
- 섹션 이름 (보고서/실험실/파란수박본부/안녕하세요?)
- 이메일 (donghoon807@gmail.com)
