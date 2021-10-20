# GSHS_SERVER
경기과학고등학교 GPU SERVER 간단 설명서
## 기본 정보
- ip : 115.23.235.135
- port : 443
- Ubuntu 20.04 focal
- CPU : Intel Xeon E5-2680 v2 @ 40x
- GPU : TEsla K40c 6개
- RAM : 96639MiB
## 접속 방법
- `ssh -p 443 아이디@115.23.235.135`
  - 교육청 공유기라 포트는 고정되어 있다.
  - fingerprint -> yes 입력
  - 호스트 키 변경 오류가 난다면 .ssh 파일 삭제(C드라이브의)
- 파일질라에서
  - 호스트 : 115.23.235.135
  - 포트 : 443
  - 방법 : SFTP
  - 아이디 : 개인아이디
  - 비번 : 개인비밀번호
- 아이디 : 서버 관리자에서 연락 (현 : gs20059)
## Jupyter notebook 이용 방법
- 초기 설정 방법
`mkdir ~/.jupyter`  
`jupyter notebook --generate-config`  
`vi jupyter_notebook_config.py`    
`gg`  
`dG`  
`i`  
`c=get_config()  
c.NotebookApp.allow_origin='*'     
c.NotebookApp.notebook_dir='/home/아이디'  
c.NotebookApp.ip=115.23.235.135'  
c.NotebookApp.port=학번  
c.NotebookApp.open_browser=False` 을 입력한다.   
ESC -> `:wq`입력
`cd ~`  
여기서 관리자에게 말하기 (방화벽 문제 때문)  
`nohup jupyter notebook --config ~/.jupyter/jupyter_notebook_config.py > jupyter.out`  
## 가상환경 사용방법
- tensorflow, python 사용 원한다면 -> 관리자에게 연락, `source ./venv/bin/activate`
- 빈 가상환경 -> `virtualenv venv` -> `source ./venv/bin/activate`
## C 언어 사용법
- gpp : g++ -o test test.cpp
- gcc : gcc -o test test.cpp
- 실행 : ./test
## DB 사용법
- 따로 개인 연락 부탁드립니다.
## 기타 명령어
- `screenfetch` : 현재 서버 정보
- `ps` : 자신의 프로세스 확인(-ef 옵션 후 `kill -5 PID`를 하면 프로세스 강제 종료 가능)
- `nvidia-smi` : 현재 GPU 상태 확인
- 
