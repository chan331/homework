# 마크다운(Markdown) 문법과 활용법 정리 

## 1. 마크다운 문서란?

> **마크다운(Markdown)** 은 경량 마크업 언어로,  
> 문서 작성 시 간결하고 직관적인 문법으로 구조화된 글을 작성할 수 있도록 돕습니다.  
> 주로 README 파일, 블로그 포스트, 기술 문서 등에서 널리 사용됩니다.

- **간단한 문법**만으로
- **HTML 같은 복잡한 코드 없이** 문서 작성 가능
- **GitHub, Notion, Vercel** 등 다양한 플랫폼에서 표준 지원

**주요 특징**
- 텍스트 중심, 가독성 높은 문서 작성
- 쉽고 빠른 작성법
- 다양한 변환(HTML, PDF 등) 가능

---

## 2. 기본 문법

### 2.1 제목(Heading)

> **제목은 문서의 뼈대입니다. 문서 구조를 명확하게 나누는 데 사용합니다.**

```markdown
# 대제목 (문서의 주제)
## 중제목 (큰 단락의 제목)
### 소제목 (세부 주제)
#### 소소제목 (자세한 설명)
```

**결과**

# 대제목 (문서의 주제)
## 중제목 (큰 단락의 제목)
### 소제목 (세부 주제)
#### 소소제목 (자세한 설명)

---

### 2.2 문단(Paragraph)

> **빈 줄**로 문단을 구분합니다. 줄바꿈을 하고 싶다면 두 칸 이상의 공백 후 줄바꿈합니다.

```markdown
첫 번째 문단입니다. (여기서는 바로 이어서 쓰면 한 문단)

두 번째 문단입니다. (중간에 빈 줄 하나를 넣어야 새로운 문단)
```

---

### 2.3 강조(Emphasis)

> **중요한 단어나 문장을 강조**할 때 사용합니다.

```markdown
*기울어진 글씨*  
_이것도 기울임_

**굵게 강조한 글씨**  
__이것도 굵게__

~~취소된 내용 표시~~
```

**결과**

*기울어진 글씨*  
_이것도 기울임_

**굵게 강조한 글씨**  
__이것도 굵게__

~~취소된 내용 표시~~

---

### 2.4 목록(List)

> **정리된 정보를 나열**할 때 사용합니다.

- 순서 없는 목록 예시

```markdown
- 사과
- 바나나
  - 덜 익은 바나나
- 체리
```

**결과**

- 사과
- 바나나
  - 덜 익은 바나나
- 체리

- 순서 있는 목록 예시

```markdown
1. 시작
2. 진행
3. 종료
```

**결과**

1. 시작
2. 진행
3. 종료

---

### 2.5 링크(Links)

> 다른 사이트나 문서로 이동할 때 사용합니다.

```markdown
[Google로 이동](https://www.google.com)
[내부 링크로 이동](#-마크다운-문서란?)
```

**결과**

- [Google로 이동](https://www.google.com)
- [내부 링크로 이동](#1.-마크다운-문서란?)

---

## 2.6 이미지(Images)

### 기본 이미지 삽입

```markdown
![대체 텍스트](이미지 URL)
```

- `[]` : 이미지가 로드되지 않을 때 표시할 **대체 텍스트** (HTML의 `alt` 속성)
- `()` : 실제 **이미지 URL 주소** (HTML의 `src` 속성)

---

### 이미지에 링크 걸기

> 이미지를 클릭했을 때 다른 페이지로 이동하게 만들 수 있다.

```markdown
[![대체 텍스트](이미지 URL)](이동할 링크 URL)
```

**예시**

```markdown
[![GitHub](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)](https://github.com)
```

**결과**  
[![GitHub](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)](https://github.com)

> 클릭하면 GitHub 홈페이지로 이동!

---

### 마크다운에서 이미지 크기 조절 (HTML 사용)

> 마크다운 자체는 **이미지 크기 조절 기능이 없음**. 대신 **HTML `<img>` 태그**를 사용해야 한다.

```html
<img src="이미지 URL" alt="대체 텍스트" width="200"/>
```

**예시**

```html
<img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" alt="GitHub Logo" width="100">
```

**결과**  
<img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" alt="GitHub Logo" width="100">

---

### 로컬 이미지 삽입

> 프로젝트 폴더 안에 있는 이미지를 삽입할 수도 있다.

```markdown
![대체 텍스트](./images/example.png)
```

※ `./images/example.png` 는 **현재 문서와 상대 경로**로 연결하는 방식이다.

---

## ✅ 이미지 삽입 요약

| 방법 | 문법 | 특징 |
|:----|:----|:----|
| 기본 삽입 | `![텍스트](URL)` | 가장 기본적인 삽입 |
| 링크 삽입 | `[![텍스트](URL)](링크)` | 클릭 시 다른 곳으로 이동 |
| 크기 조절 | `<img src="" width="숫자">` | HTML 태그 사용 |
| 로컬 이미지 | `![텍스트](./폴더/파일명)` | 프로젝트 내부 이미지 삽입 |

---

### 2.7 코드(Code)

> 코드를 설명하거나 공유할 때 사용합니다.

- 인라인 코드 (한 줄 안에 넣을 때)

```markdown
`console.log('hello')`
```
**결과**  
`console.log('hello')`

`(백틱)으로 양옆을 감싸는 경우 한 줄 짜리 코드 블록이 생성

---

- 여러 줄 코드 블록

```javascript
```function greet() {
  console.log("Hello, Markdown!");
}```

```

**결과**

```javascript
function greet() {
  console.log("Hello, Markdown!");
}
```

---

### 2.8 인용문(Blockquote)

> 인용하거나 주의사항을 강조할 때 유용합니다.

```markdown
> 이 문장은 인용구입니다.
> 
> - 참고 사항
> - 주의 사항
```

**결과**

> 이 문장은 인용구입니다.
> 
> - 참고 사항
> - 주의 사항

---

### 2.9 수평선(Horizontal Rule)

> 문단과 문단을 확실히 구분할 때 사용합니다.

```markdown
---
```

**결과**

---

---

## 🚀 3. 심화 문법

### 3.1 표(Table)

> 정보를 구조적으로 정리할 때 사용합니다.

```markdown
| 이름 | 역할 | 비고 |
|:---|:---:|---:|
| 홍길동 | 개발자 | Backend |
| 김영희 | 디자이너 | Frontend |
```

**결과**

| 이름 | 역할 | 비고 |
|:----|:----:|----:|
| 홍길동 | 개발자 | Backend |
| 김영희 | 디자이너 | Frontend |

---

### 3.2 체크박스(Checklist)

> 할 일 목록이나 계획을 표시할 때 유용합니다.

```markdown
- [x] 마크다운 기본 학습
- [x] 예시 문서 작성
- [ ] 과제 제출
- [ ] 복습하기
```

**결과**

- [x] 마크다운 기본 학습
- [x] 예시 문서 작성
- [ ] 과제 제출
- [ ] 복습하기

---

### 3.3 주석(Comment)

> **문서 내부 기록**이나 **협업시 비공개 메모**를 남길 수 있습니다. 렌더링되지 않습니다.

```markdown
<!-- 리뷰어님, 여기 부분 다시 점검해주세요 -->
```

---

# 🎨 ModernMate

> Next.js 15 기반 최신 웹 프로젝트  
> TypeScript, Supabase, Vercel을 활용한 실전형 풀스택 프론트엔드 템플릿입니다.

---

## 🚀 주요 기능

- 🖥️ 최신 Next.js 15(App Router) 아키텍처 적용
- 🛠️ Supabase 연동을 통한 인증 및 데이터 관리
- 🎯 TypeScript로 타입 안정성 강화
- ☁️ Vercel을 통한 간편한 배포
- 💬 다국어(i18n) 지원 설계
- 📱 반응형(Responsive) UI 최적화

---

## 🛠️ 기술 스택

| 구분        | 사용 기술 |
|:------------|:----------|
| Frontend    | Next.js 15, React 19, TypeScript, Tailwind CSS |
| Backend(API) | Supabase |
| Deploy      | Vercel |
| 상태 관리    | React Query(TanStack Query), Zustand |
| 기타         | ESLint, Prettier, Husky, Commitlint |

---

## 📷 스크린샷

> (예시용 스크린샷)

![화면 예시](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)

---

## 📦 설치 및 실행 방법

1. 프로젝트 클론

```bash
git clone https://github.com/facebook/react.git
```

2. 의존성 패키지 설치

```bash
npm install
```

3. 환경 변수 설정

```bash
cp .env.example .env.local
```
`.env.local` 파일을 수정하여 Supabase 설정 및 기타 API 키를 입력합니다.

4. 개발 서버 실행

```bash
npm run dev
```

5. 접속

브라우저에서 `http://www.naver.com` 접속

---

## 🗂️ 프로젝트 구조

```bash
/src
  /app         # Next.js App Router 구조
  /components  # 공통 컴포넌트
  /hooks       # 커스텀 훅
  /libs        # API 클라이언트 (ex. Supabase Client)
  /stores      # Zustand 상태 관리
  /types       # 타입 정의
  /utils       # 유틸리티 함수
/public
  /assets      # 이미지, 아이콘
```

---

## 🧩 주요 사용 라이브러리

- **Next.js 15** - 앱 라우터 기반 최적화된 React 프레임워크
- **Supabase** - 인증 및 데이터베이스 백엔드 서비스
- **Tailwind CSS** - 유틸리티 퍼스트 CSS 프레임워크
- **Zustand** - 가벼운 전역 상태 관리 라이브러리
- **TanStack Query** - 서버 상태를 효율적으로 관리하는 라이브러리

---

## 🌍 배포

본 프로젝트는 [Vercel](https://www.naver.com)을 통해 배포되었습니다.

👉 [배포된 사이트 바로가기](https://www.naver.com)

---

## 🤝 기여 방법

Pull Request 환영합니다!  
이슈를 등록하거나 포크 후 PR을 보내주세요.

1. 이슈를 통해 수정사항 제안
2. 포크 후 새로운 브랜치 생성 (`feature/기능명`)
3. 수정사항 커밋 및 푸시
4. PR 생성

---

## 📄 라이선스

MIT 라이선스 하에 오픈소스 프로젝트로 제공됩니다.  
자세한 내용은 [LICENSE](./LICENSE) 파일을 참고하세요.

---

## 🙏 감사 인사

- [Next.js 공식 문서](https://nextjs.org/docs)
- [Supabase 공식 문서](https://supabase.com/docs)
- [Tailwind CSS 공식 문서](https://tailwindcss.com/docs)

---

