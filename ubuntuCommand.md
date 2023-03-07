## ubuntu command 명령어 리스트 정리
  
### 디렉토리 관련 명령어  

1. 디렉토리 목록 확인  
  $ ls  
  $ ls -al : 감춰진 파일은 .이 붙는다. a 옵션을 사용하면 해당 파일을 확인할 수 있다.  
  $ ls -l  
  
2. 새 디렉토리 생성  
  $ mkdir [디렉토리명]  
  $ mkdir -p [디렉토리명/디렉토리명/디렉토리명...] : 여러 디렉토리 생성  
  
3. 디렉토리 이동  
  $ cd [디렉토리명]  
  $ cd .. : 부모 디렉토리로 이동  
  
> tip) 디렉토리명이 너무 길 때, 조금만 쓰고 tab키 누르면 자동완성
  
4. 디렉토리 삭제  
  $ rm -r [디렉토리명] : -r (remove directories and their contents recursively; 해당 디렉토리 아래 있는 내용들도 삭제한다.)   
  
---  

### 파일 관련 명령어
1. 비어있는 파일 생성  
  $ touch [파일명]  
  
2. 파일 삭제  
  $ rm [파일명]  
  
3. 파일 복사  
  $ cp [파일위치 및 파일이름] [목적지 파일위치 및 파일 이름]  
  
4. 파일 이동 (파일 이름을 바꿀 때에도 사용)  
  $ mv [파일위치 및 파일이름] [목적지 파일위치 및 파일 이름]  
  $ mv [원래 파일 이름] [바꾸고 싶은 파일 이름]  

5. 파일 만들고 편집 (nano 에디터)  
  $ nano [파일명] : 새 파일 작성 or 존재하는 파일 수정  
  
6. 파일 내용 보기  
  $ cat [파일명]  
  
7. 파일 위치 검색  
  $ locate *.log : (확장자가 .log인 파일 찾기) 디렉토리를 뒤지는게 아니라 데이터베이스(mlocate)를 뒤져서 찾는다.  
  $ find . *.log : 디렉토리 뒤짐  
  $ whereis ls  
  $ whereis rm : 실행파일 위치 찾기  
  
8. 현재 위치 확인  
  $ pwd
  
9. 명령창 내용 삭제  
  $ clear
  
10. 명령어 도움말 확인  
  $ [명령어] --help  
  $ man [명령어] : /[찾고싶은단어] 사용해서 단어찾기 가능, 그 상태로 n을 누르면 다음 단어 찾기  
  
---
  
### 패키지 매니저 (Package Manager)  
- 패키지 매니저 : 기본으로 내장되어 있는 패키지(프로그램)가 아닌 새로운 패키지(프로그램)를 설치하려고 할 때 도와주는 소프트웨어 (안드로이드의 구글플레이, iOS의 앱스토어...), apt, yum 등이 있음.

1. 패키지 목록 업데이트  
  $ apt-get update : 패키지 매니저를 통해 설치할 수 있는 패키지 목록들을 업데이트한다. (설치하기전에 => 설치X, 패키지 목록 update)   
2. 패키지 찾기  
  $ apt-cache search [패키지명] : 저장된 패키지 목록 중에 해당 패키지 찾기, 관련된 패키지 목록까지 나온다.  
  
3. 패키지 설치  
  $ apt-get install [패키지명]  
  
4. 패키지 업그레이드  
  $ apt-get upgrade  
  $ apt-get upgrade [패키지명]  
  
5. 패키지 삭제  
  $ apt-get remove [패키지명]  

6. 패키지를 설치하는 순서 (항상 이 순서를 따르는게 좋음.)  
  6-1. 패키지 목록 업데이트 (apt-get update)  
  6-2. 패키지 설치 (apt-get install)  
  
---
  
### 다운로드  
1. 파일 다운로드 (wget 사용)  
  $ wget -O [저장할 파일명] [다운로드 url]  
  
2. 소스코드 다운로드 (git 사용)  
  2-1. $ apt-get install git : git 설치  
  2-2. $ git clone [소스코드 url] [디렉토리명] : 소스코드 다운. 명시한 디렉토리에 소스코드 다운받는다.  

---
### why CLI?  
1. 순차적 실행 (using semicolon)
  ex) $ mkdir why; cd why  
  
  > 언제 유용한가?  
  > 하나하나의 명령들이 1000시간이 걸린다고 할 때, 명령어 하나하나씩 치는 것과 여러개를 한번에 치는 것은 차이가 있음.  
  > (여러 개 명령어를 한 번에 치면 알아서 마지막 결과만 나타남.)  

2. 파이프라인: 명령어의 연결
  > 어떤 프로세스의 출력을 다른 프로세스의 입력으로... 원하는 정보가 포함되어 있는 행을 출력  
  
  ex)  
  $ grep linux linux.txt : 'linux'가 포함된 행 출력  
  $ ls --help | grep sort : ls --help에서 'sort'가 포함된 행을 출력 (ls --help의 출력을 grep의 입력으로)  
  $ ls --help | grep sort | grep file : ls --help에서 'sort'와 'file'이 포함된 행을 출력  

### IO Redirection
1. output   
  $ ls -l > result.txt : result.txt 확인해보면 ls -l 출력물 담김  
  
2. error (에러 결과를 저장하려면? '2>' 를 사용한다. (standard error를 가리킴))  
  ex) 해당 디렉토리에 rename2.txt가 없을 때  
  $ rm rename2.txt 2> error.log : error.log에 에러 내용이 담김  

3. input  
  $ cat hello.txt : cat의 cammand-line arguments로써 역할  
  $ cat < hello.txt : hello.txt 내용을 standard input으로  
  $ head -n1 < linux.txt > one.txt : linux.txt 내용을 input, one.txt에 출력물을 저장  
  
### 디렉토리 구조
  /bin: 사용자가 사용하는 명령어 모음  
  /sbin: 관리자가 사용하는 명령어 모음  
  /etc: 프로그램 설정을 관리하는 디렉토리  
  /etc/init.d: daemon의 목적을 가진 프로그램들  
  /var: 내용이 바뀔 수 있는 파일들 모음  
  /tmp: 임시파일들. 컴퓨터가 꺼지면 삭제됨  
  /home: 사용자들의 파일들이 저장되는 디렉토리  
  /lib: /bin과 /sbin에 있는 프로그램들이 사용하는 라이브러리 모음  
  /usr: 유저가 다운받은 프로그램들 저장  
