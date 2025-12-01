# Git 되돌리기 (Undo)

## 1. Git Reset: 과거 상태로 강제 이동
HEAD 포인터를 과거의 특정 시점으로 이동시킵니다. 옵션에 따라 작업 내역을 살릴지, 완전히 지울지 결정합니다.

Hard: 작업 내용까지 깔끔하게 날려버리기 (2단계 전으로)
```bash
git reset --hard HEAD~2

```
## 2. Mixed: 커밋은 취소하되, 작업하던 파일은 남기기 (기본값)
git reset HEAD~
또는
git reset [commit_ID]

## 3. Soft: 커밋만 취소하고, 바로 다시 커밋할 수 있게 스테이징 상태 유지
git reset --soft HEAD~

## 2. Git Revert: 이력 남기고 취소하기
Reset과 달리 과거 기록을 삭제하지 않고, **'특정 커밋을 거꾸로 실행하는 새로운 커밋'**을 만듭니다.

Tip: 이미 원격 저장소(GitHub 등)에 push한 커밋을 되돌릴 때는 반드시 reset 대신 revert를 사용해야 협업 시 충돌이 발생하지 않습니다.
'''bash
마지막 커밋의 변경 사항을 취소하는 '새 커밋' 생성
git revert HEAD

커밋 메시지 작성 에디터를 열지 않고 바로 revert 진행
git revert --no-edit HEAD

revert 도중 충돌(Conflict) 발생 시 취소하고 싶을 때
git revert --abort

```
```
## 3. 복구 및 임시 저장
Reset 취소 (실수로 Reset 했을 때)
Reset 직전의 HEAD 위치는 ORIG_HEAD에 저장됩니다. 이를 이용해 복구할 수 있습니다.
```bash
git reset --hard ORIG_HEAD
```bash
# 가장 최근의 stash를 불러오면서, 스테이징 상태(--index)까지 그대로 복원
git stash apply --index

```
## 4. Reset vs Checkout 비교
Reset (git reset 9033)
브랜치 포인터 자체가 이동합니다.

즉, main 브랜치의 끝이 과거로 돌아갑니다. (역사 조작)

Checkout (git checkout 9033)
브랜치는 그대로 두고 **HEAD(나의 관점)**만 특정 커밋으로 이동합니다.

이 상태를 Detached HEAD라고 하며, 과거 시점의 코드를 '구경'하거나 임시로 테스트할 때 씁니다.
