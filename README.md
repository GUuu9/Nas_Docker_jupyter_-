# Nas_Docker_jupyter_-


### 참고 사이트
#### https://www.clien.net/service/board/cm_nas/17614098
#### https://bagng.tistory.com/159
#### https://teddylee777.github.io/visualization/matplotlib-ubuntu-한글폰트설치


### 순서대로 진행
#### NAS 에서
 1. 설정 -> 터미널 -> ssh 활성화

#### putty
 1. putty로 나스ip:22 접속 (로그인까지)
 2. sudo docker container exec -u 0 -it jupyter bash
 3. 위 명령에서 jupyter가 아니라며 컨테이너에 설정된 전체 이름으로 입력해준다.
 4. root권한으로 접속된 도커>jupyter내부 bash shell 이동 완료

#### jupyter내부 bash shell
 1. root@host:/notebooks# apt-get update 
 2. root@host:/notebooks# apt-get install locales 
 3. root@host:/notebooks# locale-gen ko_KR.UTF-8 
 4. root@host:/notebooks# locale -a
 5. 파일을 업데이트 하며 한글 패키지 설치
 6. root@host:/notebooks# apt-get install -y fonts-nanum fonts-nanum*
 7. 네이버 나눔 글꼴설치
 8. ls -l /usr/share/fonts/truetype/      으로 설치되었는지 확인
 9. rm -rf ~/.cache/matplotlib/*          폰트 캐시 삭제
 10. !fc-cache -fv.                       캐시 재생성

#### jupyter 노트북
 1. 프로그램 재실행
 2. 아래 코드를 실행하여 설치여부 확인
import matplotlib  
import matplotlib.font_manager  
[f.name for f in matplotlib.font_manager.fontManager.ttflist if 'Nanum' in f.name]  
