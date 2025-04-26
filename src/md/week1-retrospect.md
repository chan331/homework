# 1,2주차 회고

---

# Git 핵심 원리와 명령어 정리

## 🧠 Git의 기본 핵심 원리

- Git은 **로컬(Local)** 저장소와 **원격(Remote)** 저장소를 분리해서 관리한다.
- 로컬 브랜치는 원격 저장소의 특정 브랜치와 **tracking(upstream)** 관계를 맺을 수 있다.
- Git은 기본적으로 `push`, `pull` 시  
  - **로컬 브랜치 이름**과  
  - **연결된 remote 브랜치 이름**이 **같아야 자동으로 동작**하도록 (`push.default = simple`) 설정돼 있다.
- 이름이 다르면 Git은 기본적으로 혼란스러워하고 수동 명령을 요구한다.

---

### 1. 강사의 레포를 clone한 후

```bash
git clone https://github.com/seulbinim/ssam-html-css.git learn-html-css
cd learn-html-css
```
- 원래 remote 이름은 `origin`이지만,
- **강사의 레포를 명확히 구분**하기 위해 remote 이름을 `main`으로 변경함.

```bash
git remote rename origin main
```

---

### 2. 내 개인 GitHub 레포를 remote로 추가

```bash
git remote add study https://github.com/chan331/learn-html-css.git
```
- 내 개인 저장소를 **study**라는 이름의 remote로 추가.

---

### 3. 로컬에서 내 작업용 브랜치 생성

```bash
git switch -c study
```
- `study`라는 로컬 브랜치를 생성하고, 여기에 개인 작업을 저장하려고 함.

---

### 4. 내 로컬 브랜치를 내 개인 레포(원격)에 연결하고 push

```bash
git push -u study study:main
```
- 로컬 `study` 브랜치를 → remote `study` 저장소의 `main` 브랜치로 push.
- 그리고 `-u` 옵션으로 **upstream** 관계를 설정.
- 단, 로컬 브랜치(`study`)와 remote 브랜치(`main`) 이름이 **달라서** Git이 혼란을 가질 수 있는 상태가 됨.

---

### 5. 강사의 레포에 업데이트가 생겼을 때

```bash
git switch main
git pull
```
- `main` 브랜치로 이동하여 강사의 최신 코드를 pull 받음.

---

### 6. 강사의 업데이트를 내 개인 레포에 반영하고 싶을 때

```bash
git switch study
git merge main
git push
```
- `study` 브랜치로 이동
- `main` 브랜치의 변경 사항을 merge
- `git push`로 내 개인 원격 레포에 반영하려 했으나,
- **"브랜치 이름이 다르다"** 는 이유로 에러 발생

---

### 7. 에러 메시지 발생

```text
fatal: The upstream branch of your current branch does not match the name of your current branch.
```
- 이유: 로컬 브랜치 이름(`study`)과 연결된 원격 브랜치 이름(`main`)이 다르기 때문
- Git 기본 설정(`push.default=simple`) 때문에 자동 push가 막힘.

---

### 8. 이 문제를 해결하는 방법

#### 명시적으로 push
```bash
git push study HEAD:main
```
- 현재 브랜치(`study`)를 remote `study` 저장소의 `main` 브랜치로 push.

#### 또는 push default 설정 변경
```bash
git config --global push.default upstream
```
- 이후부터는 단순히 `git push`만 해도 자동으로 연결된 remote 브랜치로 push됨.

---

## ✅ Git 설정 및 명령어 핵심 요약

| 상황 | 사용한 명령어 | 설명 |
|------|---------------|------|
| remote 이름 변경 | `git remote rename origin main` | 강사의 레포를 명확히 구분 |
| remote 추가 | `git remote add study <URL>` | 내 개인 레포 추가 |
| 브랜치 생성 | `git switch -c study` | 작업용 브랜치 생성 |
| upstream 설정 및 push | `git push -u study study:main` | 로컬 study → remote main 연결 |
| 최신 코드 pull | `git pull` (on main) | 강사의 업데이트 가져오기 |
| 강사코드 merge 후 push | `git merge main` + `git push` | 내 작업 반영 |
| 브랜치 이름 불일치 시 해결 | `git push study HEAD:main` | 명시적 push |
| 브랜치 기본 연결 변경 | `git config --global push.default upstream` | 추적 설정 기반 push 허용 |

---

# 📖 마무리

- **Git은 기본적으로 로컬과 원격을 명확히 분리하고 관리한다.**
- **upstream 설정은 로컬 브랜치와 remote 브랜치 간 연결 고리다.**
- **push 시 브랜치 이름이 다르면 기본 설정(simple)에서는 에러가 날 수 있다.**
- **상황에 따라 명시적 push를 하거나, 기본 전략을 바꿔야 한다.**

---
