# OSS-Project-DMU
오픈소스소프트웨어 1학년 2학기 깃허브 개인과제

---

## 1. Git 초기 설정 (Initial Setup)
Git을 처음 설치한 후 한 번만 설정하면 됩니다.

### 버전 및 사용자 정보 설정
```bash
# Git 버전 확인
git --version

# 사용자 이름 설정 (커밋 기록용)
git config --global user.name "이름"

# 사용자 이메일 설정 (커밋 기록용)
git config --global user.email "xxx@xxx.com"

# 설정 확인
git config user.name
git config user.email

# 줄바꿈 문자(Line Ending) 설정
# 운영체제 간의 호환성 문제를 방지하기 위해 설정합니다.
Windows: git config --global core.autocrlf true
Mac/Linux: git config --global core.autocrlf input
