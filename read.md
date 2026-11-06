# Git과 GitHub 실습 노트

이 저장소는 브랜치 생성, 커밋, 병합, 충돌 해결, 원격 저장소, 이슈와 Pull Request 흐름을 연습하기 위한 공간입니다.

## 기본 용어

- **저장소(repository)**: 파일과 변경 이력을 함께 관리하는 공간입니다. 로컬 저장소와 GitHub 원격 저장소가 있습니다.
- **커밋(commit)**: 변경 내용을 기록한 스냅샷입니다. 짧고 설명적인 메시지를 남깁니다.
- **브랜치(branch)**: 기존 작업을 보존하면서 독립적으로 변경할 수 있는 작업 줄기입니다.
- **원격(remote)**: GitHub 저장소를 가리키는 이름입니다. 보통 `origin`을 사용합니다.
- **Pull Request(PR)**: 한 브랜치의 변경을 다른 브랜치에 합치기 위해 검토와 병합을 요청하는 기능입니다.
- **이슈(issue)**: 작업, 질문, 버그를 기록하고 논의하는 GitHub 항목입니다.

## 자주 쓰는 명령

```bash
git status
git switch -c feat/my-change
git add read.md exercise.md
git commit -m "Add Git practice notes"
git push -u origin feat/my-change
```

`git fetch`는 원격 변경 정보를 가져오고, `git pull`은 가져온 뒤 현재 브랜치에 반영합니다. `git push`는 로컬 커밋을 원격으로 보냅니다.

## 병합 충돌

같은 파일의 겹치는 부분을 두 브랜치가 다르게 수정하면 충돌이 생길 수 있습니다. 충돌 표시는 다음 형태입니다.

```text
<<<<<<< HEAD
현재 브랜치의 내용
=======
합칠 브랜치의 내용
>>>>>>> branch-name
```

원하는 최종 내용을 직접 편집하고 충돌 표식을 제거한 다음, 변경을 스테이징하고 커밋합니다.

## 이 저장소에서 연습한 흐름

`dev`, `fix`, `feat/login`, `feat/awesome1`, `feat/awesome2`, `release` 등의 브랜치로 작업을 나누고 병합 이력을 확인할 수 있습니다. 이전 `release` 변경은 PR #1로 `main`에 병합됐습니다. GitHub CLI(`gh`)로 저장소와 이슈, PR을 관리할 수도 있습니다.

별도 `ai_issue` 저장소를 만들고 `origin`을 연결했으며, 그 저장소에 `배포됨` 이슈(#1)를 만들었습니다. 저장소 이름, 공개 범위, 이슈 제목을 지정해 GitHub CLI를 사용하는 흐름도 실습했습니다.

## PR 절차

1. 작업 브랜치에서 변경하고 커밋합니다.
2. 브랜치를 원격에 푸시합니다.
3. GitHub에서 base를 `main`, compare를 작업 브랜치로 선택해 PR을 엽니다.
4. 변경 사항을 검토하고 병합합니다.

`release`는 여기서 브랜치 이름입니다. GitHub Release(배포 버전)는 태그와 릴리스 노트를 묶는 별도의 기능입니다.
