# 개발 워크스테이션 구축 미션

## 터미널 조작 로그

### 1. 현재 위치 확인 (pwd)
```bash
modugachi@DESKTOP-G603NQD:~/codyssey$ pwd
/home/modugachi/codyssey
```
### 2. 목록 확인 (ls -la)
- 목적: 숨김 파일을 포함한 현재 폴더의 전체 목록 확인
```bash
modugachi@DESKTOP-G603NQD:~/codyssey/practice$ touch empty.txt
touch .hidden.txt
ls
ls -la
empty.txt
total 8
drwxr-xr-x 2 modugachi modugachi 4096 Nov  3 16:10 .
drwxr-xr-x 3 modugachi modugachi 4096 Nov  3 16:08 ..
-rw-r--r-- 1 modugachi modugachi    0 Nov  3 16:10 .hidden.txt
-rw-r--r-- 1 modugachi modugachi    0 Nov  3 16:10 empty.txt
```
- 확인한 점: `.`(현재 폴더), `..`(상위 폴더)와 `README.md`가 목록에 보였다.

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
modugachi@DESKTOP-G603NQD:~/codyssey/practice$ touch empty.txt
modugachi@DESKTOP-G603NQD:~/codyssey/practice$ touch .hidden.txt
modugachi@DESKTOP-G603NQD:~/codyssey/practice$ ls
(여기에 터미널 출력 붙여넣기)
modugachi@DESKTOP-G603NQD:~/codyssey/practice$ ls -la
(여기에 터미널 출력 붙여넣기)
```
- 확인한 점: `ls`에서는 `.hidden.txt`가 보이지 않았고 `ls -la`에서만 보였다.

### 6. 절대 경로와 상대 경로 이동 비교
- 목적: 같은 위치로 이동하는 두 가지 방법 비교
```bash
modugachi@DESKTOP-G603NQD:~/codyssey/practice$ cd ..
modugachi@DESKTOP-G603NQD:~/codyssey$ pwd
/home/modugachi/codyssey
modugachi@DESKTOP-G603NQD:~/codyssey$ cd ~/codyssey/practice
modugachi@DESKTOP-G603NQD:~/codyssey/practice$ pwd
/home/modugachi/codyssey/practice
```
- 확인한 점: `cd ..`는 현재 위치(`practice`)를 기준으로 한 단계 위인 `/home/modugachi/codyssey`로 이동했다(**상대 경로**). 이어서 `cd ~/codyssey/practice`로 홈부터 전체 주소를 적어 `practice`로 다시 이동했다(**절대 경로**). 상대 경로는 실행하는 위치에 따라 도착지가 달라지고, 절대 경로는 어디서 실행해도 같은 곳에 도착한다.
