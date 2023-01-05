### 개발 관련된 잡다한 정보들 및 내용들을 간략히 키워드 형식으로 남길 Readme
##### 추후 내용이 많아지면 블로그로 옮기거나 새로운 Repository 혹은 Notion을 통해 관리 예정

1. Javascript의 console.log를 통해 객체를 콘솔에 출력할 때 해당 console.log의 위치와 무관하게
최종적으로 객체에 값이 할당되는 순간의 값이 console에 출력이 된다.
  > Parameter를 통해서 객체를 전달할 때에도 해당 인자를 받은 function에서 객체를 변경하게 되면 따로 return해주지 않아도 전달한 쪽에도 변경이 된다.
  
2. Redis란?
Key, Value 구조의 비정형 데이터를 저장하고 관리하기 위한 오픈 소스 기반의 비관계형 데이터 베이스 관리 시스템 (DBMS)입니다.  
데이터베이스, 캐시, 메세지 브로커로 사용되며 인메모리 데이터 구조를 가진 저장소입니다.  
> db-engines.com 에서 key, value 저장소 중 가장 순위가 높습니다.

- Redis의 특징
  - Key, Value 구조이기 때문에 쿼리를 사용할 필요가 없습니다.  
  - 데이터를 디스크에 쓰는 구조가 아니라 메모리에서 데이터를 처리하기 때문에 속도가 빠릅니다.  
  - String, Lists, Sets, Sorted Sets, Hashes 자료 구조를 지원합니다.  
      1) String : 가장 일반적인 key - value 구조의 형태입니다.  
      2) Sets : String의 집합입니다. 여러 개의 값을 하나의 value에 넣을 수 있습니다. 포스트의 태깅 같은 곳에 사용될 수 있습니다.
      3) Sorted Sets : 중복된 데이터를 담지 않는 Set 구조에 정렬 Sort를 적용한 구조로 랭킹 보드 서버 같은 구현에 사용할 수 있습니다.
      4) Lists : Array 형식의 데이터 구조입니다. List를 사용하면 처음과 끝에 데이터를 넣고 빼는 건 빠르지만 중간에 데이터를 삽입하거나 삭제하는 것은 어렵습니다.

  - Single Threaded
  > 한 번에 하나의 명령만 처리할 수 있습니다. 
  > 그렇기 때문에 중간에 처리 시간이 긴 명령어가 들어오면 그 뒤에 명령어들은 모두 앞에 있는 명령어가 처리될 때까지 대기가 필요합니다.
  (하지만 get, set 명령어의 경우 초당 10만 개 이상 처리할 수 있을 만큼 빠릅니다.)

- Redis 사용에 주의점
  - 서버에 장애가 발생했을 경우 그에 대한 운영 플랜이 꼭 필요합니다.
    > 인메모리 데이터 저장소의 특성상, 서버에 장애가 발생했을 경우 데이터 유실이 발생할 수 있기 때문입니다.
  - 메모리 관리가 중요합니다.
  - 싱글 스레드의 특성상, 한 번에 하나의 명령만 처리할 수 있습니다. 처리하는데 시간이 오래 걸리는 요청, 명령은 피해야 합니다.

- POSTING 주제
  1. JS NULL 병합 연산자 (완료)
  2. JS 객체의 주의점
  3. JS || 
