# 재밌는 사이트 모음

깃 · 깃허브 특강 팀 프로젝트용 예제 저장소입니다.

## 이 저장소는 무엇인가요

우리 팀이 각자 추천하는 사이트를 모아두는 링크 모음 사이트입니다.

- **홈**(`index.html`) — 추천 사이트가 카드로 나열됩니다
- **상세 페이지**(`sites/*.html`) — 그 사이트가 어떤 곳인지 소개하고, 원래 사이트로 가는 링크를 둡니다

## 파일 구조

```
.
├── index.html            홈 — 카드 목록 (팀원 모두가 고칩니다)
├── style.css             공통 스타일 (아무도 고치지 않습니다)
└── sites/
    └── neal-fun.html     상세 페이지 예시 — 이 파일을 복사해서 쓰세요
```

## 브랜치 전략

| 브랜치 | 역할 | 규칙 |
| --- | --- | --- |
| `main` | 완성본 · 배포용 | **직접 push 금지.** PR로만 반영, force push · 삭제 불가 |
| `develop` | 기본 작업 브랜치 | 모든 `feature` PR 의 base |
| `feature/<이슈번호>` | 작업 하나 | 이슈 1개 = 브랜치 1개, 머지 후 삭제 |

```
feature/12 ──► develop ──► main
```

## 이름 규칙

| 대상 | 형식 | 예시 |
| --- | --- | --- |
| 이슈 제목 | `[태그] 요약` | `[Feature] neal.fun 상세 페이지 추가` |
| 브랜치 | `feature/<이슈번호>` | `feature/12` |
| PR 제목 | `[태그] 요약 #이슈번호` | `[Feature] neal.fun 상세 페이지 추가 #12` |
| 커밋 메시지 | `type: 요약` | `feat: neal.fun 상세 페이지 추가` |

- 태그는 **`[Feature]` · `[Bug]` · `[Task]`** 세 가지입니다. 이슈와 PR 의 태그를 똑같이 맞춥니다.
- 커밋 `type` 은 `feat` · `fix` · `docs` · `style` · `refactor` · `chore` 를 씁니다.

## 작업 흐름 — 이슈를 먼저 만듭니다

**코드부터 건드리지 않습니다. 언제나 이슈 → 브랜치 → PR 순서입니다.**

### 1. 이슈 생성

저장소 상단 `Issues` → `New issue` → 템플릿(기능 추가 / 버그 리포트 / 작업) 선택.
제목의 `[Feature] ` 는 템플릿에 이미 들어 있으니 뒤에 요약만 이어서 씁니다.
만들고 나면 이슈 번호(예: `#12`)가 생깁니다.

### 2. 이슈 번호로 브랜치 만들기

`develop` 에서 분기합니다.

```bash
git switch develop
git pull origin develop
git switch -c feature/12
```

### 3. 작업하고 커밋 · 푸시

```bash
git add .
git commit -m "feat: neal.fun 상세 페이지 추가"
git push -u origin feature/12
```

### 4. PR 보내기

- **base: `develop`** ← compare: `feature/12`  (base 가 `main` 으로 잡혀 있으면 `develop` 으로 바꿔주세요)
- 제목: `[Feature] neal.fun 상세 페이지 추가 #12`
- 본문의 `Closes #` 뒤에 이슈 번호를 적습니다 → `Closes #12`

### 5. 머지하고 정리

머지한 뒤 GitHub 의 `Delete branch` 버튼으로 원격 브랜치를 지우고, 로컬도 정리합니다.

```bash
git switch develop
git pull origin develop
git branch -d feature/12
```

> `Closes #12` 는 **기본 브랜치(`main`)로 머지될 때** 이슈를 자동으로 닫습니다.
> `develop` 머지 단계에서는 안 닫히니, 작업이 끝났으면 이슈를 직접 닫아주세요.

## 내 사이트를 추가하는 방법

1. 위 **작업 흐름** 대로 이슈를 만들고 `feature/<이슈번호>` 브랜치를 팝니다
2. `sites/neal-fun.html` 을 복사해 `sites/<사이트이름>.html` 로 저장하고 내용을 채웁니다
3. `index.html` 의 카드 블록(`▼▼▼ 카드 하나 시작` ~ `▲▲▲ 카드 하나 끝`)을 복사해
   목록 아래에 붙이고, 링크·제목·소개·이모지·색을 내 것으로 바꿉니다
4. 커밋하고 푸시한 뒤 `develop` 으로 풀 리퀘스트를 보냅니다

## 주의

- `index.html` 은 팀원 모두가 같은 자리를 고칩니다. **충돌이 나는 것이 정상입니다.**
- HTML 을 실제로 구현하는 과제가 아닙니다. 파일을 만들고 링크를 연결하는 것까지가 범위입니다.
- `main` 은 보호되어 있어 직접 push 가 거부됩니다. 반드시 PR 로 보내세요.
