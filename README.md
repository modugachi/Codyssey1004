# 개발 워크스테이션 구축 미션
## 작업 환경
- 첫 번째 PC: Windows + WSL2 Ubuntu (`DESKTOP-G603NQD`), 작업 폴더 `~/codyssey` (1~6번 로그)
- 두 번째 PC(교육장): Windows + WSL2 Ubuntu (`GNIA-C202-C06`), 작업 폴더 `~/codyssey-repo` (7번 이후 로그)
- 두 PC는 GitHub 저장소를 통해 작업을 이어받음 (`git push` / `git clone`, `git pull`)

## 터미널 조작 로그

### 1. 현재 위치 확인 (pwd)
```bash
modugachi@DESKTOP-G603NQD:~/codyssey$ pwd
/home/modugachi/codyssey
```
### 2. 목록 확인 (ls -la)
- 목적: 숨김 파일을 포함한 현재 폴더의 전체 목록 확인
```bash
modugachi@DESKTOP-G603NQD:~/codyssey/practice$ cd ~/codyssey-repo
ls -la
total 20
drwxr-xr-x 4 modugachi10042823 modugachi10042823 4096 Nov  5 16:11 .
drwxr-x--- 8 modugachi10042823 modugachi10042823 4096 Nov  5 16:18 ..
drwxr-xr-x 7 modugachi10042823 modugachi10042823 4096 Nov  5 16:20 .git
-rw-r--r-- 1 modugachi10042823 modugachi10042823 2892 Nov  5 16:11 README.md
drwxr-xr-x 3 modugachi10042823 modugachi10042823 4096 Nov  5 16:33 practice
```
- 확인한 점: `.`(현재 폴더), `..`(상위 폴더)와 `empty.txt`가 목록에 보였다.

### 3. 폴더 생성 (mkdir)
- 목적: 연습용 폴더 `practice` 생성
```bash
modugachi@DESKTOP-G603NQD:~/codyssey$ mkdir -p practice
modugachi@DESKTOP-G603NQD:~/codyssey$ ls -l
total 8
-rw-r--r-- 1 modugachi modugachi  183 Nov  3 14:01 README.md
drwxr-xr-x 2 modugachi modugachi 4096 Nov  3 16:08 practice
```
- 확인한 점: `mkdir`는 성공하면 출력이 없었고, `ls -l`에서 `practice` 앞에 `d`가 붙어 폴더임을 확인했다.

### 4. 폴더 이동 (cd)
- 목적: `practice` 폴더로 이동하고 위치 확인
```bash
modugachi@DESKTOP-G603NQD:~/codyssey$ cd practice
modugachi@DESKTOP-G603NQD:~/codyssey/practice$ pwd
/home/modugachi/codyssey/practice
```
- 확인한 점: 프롬프트의 위치 표시가 `~/codyssey/practice`로 바뀌었다.

### 5. 빈 파일 생성 (touch)와 숨김 파일 확인
- 목적: 빈 파일과 숨김 파일을 만들고 `ls`와 `ls -la`의 차이 비교
```bash
```bash
modugachi@DESKTOP-G603NQD:~/codyssey/practice$ touch empty.txt
modugachi@DESKTOP-G603NQD:~/codyssey/practice$ touch .hidden.txt
modugachi@DESKTOP-G603NQD:~/codyssey/practice$ ls
empty.txt
modugachi@DESKTOP-G603NQD:~/codyssey/practice$ ls -la
total 8
drwxr-xr-x 2 modugachi modugachi 4096 Nov  3 16:10 .
drwxr-xr-x 3 modugachi modugachi 4096 Nov  3 16:08 ..
-rw-r--r-- 1 modugachi modugachi    0 Nov  3 16:10 .hidden.txt
-rw-r--r-- 1 modugachi modugachi    0 Nov  3 16:10 empty.txt
```
- 확인한 점: `ls`에서는 `.hidden.txt`가 보이지 않았고 `ls -la`에서만 보였다.

### 6. 절대 경로와 상대 경로 이동 비교
- 목적: 상대 경로 이동(`cd ..`)과 절대 경로 이동(`cd ~/codyssey/practice`)의 동작 확인
```bash
modugachi@DESKTOP-G603NQD:~/codyssey/practice$ cd ..
modugachi@DESKTOP-G603NQD:~/codyssey$ pwd
/home/modugachi/codyssey
modugachi@DESKTOP-G603NQD:~/codyssey$ cd ~/codyssey/practice
modugachi@DESKTOP-G603NQD:~/codyssey/practice$ pwd
/home/modugachi/codyssey/practice
```
- 확인한 점: `cd ..`는 현재 위치(`practice`)를 기준으로 한 단계 위인 `/home/modugachi/codyssey`로 이동했다(**상대 경로**). 이어서 `cd ~/codyssey/practice`로 홈부터 전체 주소를 적어 `practice`로 다시 이동했다(**절대 경로**). 상대 경로는 실행하는 위치에 따라 도착지가 달라지고, 절대 경로는 어디서 실행해도 같은 곳에 도착한다.
### 7. 파일 내용 쓰기와 확인 (echo, cat)
- 목적: 파일에 내용을 쓰고 확인하며, `>`(덮어쓰기)와 `>>`(추가)의 차이를 관찰
```bash
modugachi10042823@GNIA-C202-C06:~/codyssey-repo/practice$ echo "hello codyssey" > hello.txt
modugachi10042823@GNIA-C202-C06:~/codyssey-repo/practice$ cat hello.txt
hello codyssey
modugachi10042823@GNIA-C202-C06:~/codyssey-repo/practice$ echo "second line" >> hello.txt
modugachi10042823@GNIA-C202-C06:~/codyssey-repo/practice$ cat hello.txt
hello codyssey
second line
```
- 확인한 점: `>`로 쓴 뒤에는 한 줄이었고, `>>`를 쓰자 기존 내용 뒤에 한 줄이 추가되어 두 줄이 되었다.

### 8. 복사 (cp)
- 목적: 파일을 복사하고 원본이 유지되는지 확인
```bash
modugachi10042823@GNIA-C202-C06:~/codyssey-repo/practice$ cp hello.txt copy.txt
ls -l
total 8
-rw-r--r-- 1 modugachi10042823 modugachi10042823 27 Nov  5 16:22 copy.txt
-rw-r--r-- 1 modugachi10042823 modugachi10042823  0 Nov  5 16:11 empty.txt
-rw-r--r-- 1 modugachi10042823 modugachi10042823 27 Nov  5 16:22 hello.txt
```
- 확인한 점: `hello.txt`가 그대로 남아 있고 `copy.txt`가 새로 생겼으며, 두 파일의 크기(바이트)가 같다. 

### 9. 이동과 이름 변경 (mv)
- 목적: `mv`로 이름을 바꾸고 다른 폴더로 이동
```bash
mv copy.txt renamed.txt
mkdir backup
mv renamed.txt backup/
ls -R
.:
backup  empty.txt  hello.txt

./backup:
renamed.txt
```
- 확인한 점: 같은 폴더 안에서 `mv`를 쓰면 이름이 바뀌고(`copy.txt` → `renamed.txt`), 폴더를 지정하면 이동한다(`backup/` 안으로). `ls -R`에서 `renamed.txt`가 `backup` 안에 있는 것을 확인했다.

### 10. 삭제 (rm)
- 목적: 연습용 파일과 폴더를 삭제하고 사라진 것을 확인
```bash
touch delete_me.txt
ls
rm delete_me.txt
ls
rm -r backup
ls
backup  delete_me.txt  empty.txt  hello.txt
backup  empty.txt  hello.txt
empty.txt  hello.txt
```
- 확인한 점: `rm`으로 파일이 목록에서 사라졌고, 폴더는 `-r` 옵션을 붙여야 안의 내용까지 지워졌다. `rm`은 휴지통이 없어 되돌릴 수 없으므로 연습용 파일만 지웠다.

## 권한 실습 (chmod)

### 11-1. 파일 권한 변경
- 목적: 파일 1개의 권한을 변경하고 변경 전/후를 비교
```bash
touch perm_test.txt
ls -l perm_test.txt
chmod 600 perm_test.txt
ls -l perm_test.txt
chmod 755 perm_test.txt
ls -l perm_test.txt
-rw-r--r-- 1 modugachi10042823 modugachi10042823 0 Nov  5 16:28 perm_test.txt
-rw------- 1 modugachi10042823 modugachi10042823 0 Nov  5 16:28 perm_test.txt
-rwxr-xr-x 1 modugachi10042823 modugachi10042823 0 Nov  5 16:28 perm_test.txt
```
- 확인한 점: 권한 표기가 `-rw-r--r--`(644) → `-rw-------`(600) → `-rwxr-xr-x`(755)로 바뀌었다. (처음 값은 실제 출력 기준으로 적기)

| 숫자 | 해석 | 의미 |
|---|---|---|
| 6 (4+2) | rw- | 읽기, 쓰기 |
| 7 (4+2+1) | rwx | 읽기, 쓰기, 실행 |
| 5 (4+1) | r-x | 읽기, 실행 |
| 0 | --- | 권한 없음 |

### 11-2. 디렉토리 권한 변경
- 목적: 디렉토리 1개의 권한을 변경하고 변경 전/후를 비교 (`-d`는 폴더 자신의 정보를 보는 옵션)
```bash
mkdir perm_dir
ls -ld perm_dir
chmod 700 perm_dir
ls -ld perm_dir
drwxr-xr-x 2 modugachi10042823 modugachi10042823 4096 Nov  5 16:33 perm_dir
drwx------ 2 modugachi10042823 modugachi10042823 4096 Nov  5 16:33 perm_dir
```
- 확인한 점: `drwxr-xr-x`(755)가 `drwx------`(700)로 바뀌어 소유자 외에는 접근 권한이 없어졌다.

### 11-3. 권한이 실제로 막는 모습
- 목적: 숫자 표기가 아니라 실제 동작이 막히는지 관찰
```bash
chmod 000 perm_dir
cd perm_dir
chmod 755 perm_dir
cd perm_dir
cd ..
bash: cd: perm_dir: Permission denied
```
- 확인한 점: 권한이 `000`일 때 `cd`가 `Permission denied`로 막혔고, `755`로 되돌리자 폴더 안으로 들어갈 수 있었다. 폴더에서 `x` 권한은 "그 안으로 들어갈 수 있는 권한"이다.

## 트러블슈팅

### 12-1. 명령어 입력 실수 (bath, -1, code.)
- **문제**: `bath`, `-1`, `code.`를 입력했을 때 `command not found` 또는 "인식되지 않습니다" 오류 발생
- **원인 가설**: 오타나 띄어쓰기 누락으로 존재하지 않는 이름의 명령으로 해석되었을 것이다 (`bash`의 오타, `ls -l`에서 `ls ` 누락, `code .`의 공백 누락)
- **확인**: (본인이 확인한 방법. 예: 명령을 올바르게 다시 입력해 정상 동작 확인)
- **해결**: 명령과 옵션 사이에 공백을 두고 철자를 바로잡아 재입력했다.
- **배운 점**: 오류의 첫 줄에 "무슨 이름을 못 찾았는지"가 나오므로 내가 입력한 글자를 먼저 확인한다.

### 12-2. PowerShell과 Ubuntu 터미널의 차이
- **문제**: PowerShell에서 리눅스 명령(`bash` 등)이 동작하지 않음
- **원인 가설**: 프롬프트가 `PS C:\...>`인 윈도우 PowerShell이라 리눅스 환경이 아니었을 것이다
- **확인**: 프롬프트 형태와 `pwd` 출력 경로가 `C:\...`인지 `/home/...`인지 비교
- **해결**: WSL(Ubuntu)을 설치하고 VS Code를 WSL에 연결해 Ubuntu 터미널에서 실습했다.

### 12-3. git push 거절 (fetch first)
- **문제**: `git push -u origin main` 시 `! [rejected] main -> main (fetch first)` 오류
- **원인 가설**: GitHub 저장소에 내 컴퓨터에 없는 파일이 이미 있어 기록이 달랐을 것이다
- **확인**: 저장소를 `git clone`해 확인한 결과 GitHub에 빈 `README.md`가 이미 있었다
- **해결**: `git push --force`는 기존 내용을 지우므로 쓰지 않고, 저장소를 먼저 복제한 뒤 내 파일을 복사해 넣고 `git add`, `git commit`, `git push`로 올렸다.
- **배운 점**: Git은 원격의 내용을 보호하기 위해 push를 거절하며, 먼저 받아온 뒤 올려야 한다.