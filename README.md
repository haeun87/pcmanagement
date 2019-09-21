# 주의사항
 1. 이 문서는 업로드된 팀프로젝트 소스 전체에 대한 설명을 목적으로 하고 있습니다. 
 2. heaun87(본인)의 기여도와 참여 정보에 대한 상세 내역은 별도의 문서에 기재되어 있으므로 이 문서는 보조적으로만 참고 바랍니다.  
 
# 프로젝트 pcmanagement
JAVA SWING기반 미니 pc방 관리프로그램 (팀 프로젝트)

# 프로젝트 명
 PC방 관리 프로그램

# 프로젝트 참여자 
 heaun87(본인) 외 3명

# 프로젝트 내 담당 파트
 1. 로그인, 사용자 프로그램 메인, 관리자 프로그램의 인터페이스
 2. 사용자 프로그램 : 물품 주문 기능 구현
 3. 관리자 프로그램 : 시재관리, 계산 기능 구현
 
# 프로젝트 기획 의도
 가상의 PC방 운영을 전제하여 PC방 운영에 기본이 되는 기능들을
구현함으로써, 관리 프로그램의 구조와 설계를 이해하고 기능별 장단점을 식별함으로써 자바
프로그래밍에 대한 숙련도와 이해도를 넓히는데 도움을 주기 위하여 해당 프로젝트를 수행하였습니다.

# 실행방법

  1.관리자 프로그램
 mgr폴더 내의 ManagerMain.java 파일로 관리자 로그인 화면을 먼저 띄웁니다. 관리자 로그인 인증을 
거치고 나면 관리자 프로그램이 실행됩니다.  관리자 프로그램 상에는 사용자 PC사용 현황과 회원관리 항목, 
물품관리 항목, 시재 및 매상관리, 시간추가, 계산 항목을 각각 선택하여 실행할 수 있습니다.
 각각의 항목들은 관련된 DB 데이터와 연결되어 동시적으로 정보가 반영되도록 설계하였습니다.
PC모니터 화면상에서는 현재 사용중인 사용자의 ID와 남은 시간을 확인할 수 있고, 오른쪽 상단의
접속리스트를 선택하면 해당 사용자에 대한 계산이 가능하도록 활성화시키는 기능을 추가하였습니다. 재고관리
및 시재관리는 사용자 프로그램에서 해당 데이터들의 수정,삭제,추가가 동시로 반영되도록 설계하였습니다.
관리자 프로그램은 메인 서버와 연동되어 있으므로 사용자들이 모두 접속을 중지하기 전까지는 강제 종료할 수 
없도록 설계되었습니다.

   2.사용자  프로그램   
  cnt폴더 내의 ClientMain.java 파일로 사용자 로그인 화면을 먼저 띄웁니다. 로그인 화면에서는 회원가입,
아이디/비밀번호 분실시의 검색 기능 등을 추가하였습니다. 회원가입된 회원의 정보는 관리자 프로그램 및
DB에 실시간으로 반영됩니다. 회원가입의 인증은 이메일 적합 인증을 통하여 최종 승인되도록 설계하였습니다.
회원 로그인과 비회원 로그인이 별도로 존재하므로 적합한 방식으로 로그인하도록 설계되었으며 로그인시에 사용자가 자신의
좌석을 입력하도록 설계되어 있습니다. 
사용자 프로그램은 메인 서버의 구동이 전제되므로 관리자 프로그램이 실행되지 않은 상황에서는 로그인 화면 이후로 넘어갈 수
없도록 설계하였습니다. 사용자 로그인 후 사용자 프로그램에는 사용자가 현재 착석한 좌석 번호, 관리자에게 보내는 메세지 항목,
물품주문 항목, 일시정지 항목 등이 구현되어 있습니다.  또한 실시간으로 사용자의 남은 시간 및 선불한 요금의 잔액이
반영됩니다. 사용자가 메세지 또는 물품주문을 하는 경우 관련 메세지와 항목이 관리자에게로 전송되어 관리자 프로그램 상의
팝업창으로 표시됩니다. 물품주문, 메세지 전송 등 사용자 요청으로부터 DB에 반영되는 프로세스까지는 실제 거래 프로세스와
동일한 순서대로 설계되었습니다. 일시정지 항목을 선택하는 경우에는 메세지 전송 또는 물품주문 항목을 일시사용중지로 만들어
실제 PC방과 같은 방식으로 기능하게 만들었습니다. 사용자가 청구한 항목에 대한 정보는 관리자프로그램으로 넘어가 최종 결제
가능하도록 되어 있습니다. 사용자의 잔여시간이 0분이 되어 사용이 종료되었을 때 및 사용자 본인이 사용종료를 요청한 경우
본래의 로그인 화면으로 돌아오게 설계되었습니다.

# 프로그램의 구성
   1> 관련 소스(코드) 
 프로젝트 폴더 내 소스 코드는 'cnt(고객 프로그램)','member.bean(사용자DTO)','member.dao(회원DB)','mgr(관리자 프로그램 관련','mgr.account(계산 관련',
'mgr.inventory(물품 관리)','mgr.member(회원 관리)','mgr.sales(시재/매상관리)','mgr.seat(좌석)'로 분류된 패키지 내부에 각각 보관되어 있습니다.
 관련 JAR 파일로는 'ojdbc(DB 관련)','JTatto(프로그램의 인터페이스 적용)','mail(메일 인증)'이 존재합니다.
  2> Oracle DB
 해당 프로젝트의 데이터베이스는 'Oracle Database 11g express Version'으로 구현하였습니다. 사용된 테이블은 '물품','매상',PCManager(회원정보)' 세 종이며,
각각 관련 프로세스에 맞게 연결되어 있습니다.  각 테이블의 항목은 다음으로 구성되어 있습니다.

Table 'PCMANAGER'			    Table '매상'		                Table '물품'

ID        VARCHAR2(15) 	거래번호 NOT NULL NUMBER    	  상품번호 NOT NULL NUMBER 
PW        VARCHAR2(15) 	상품번호 NOT NULL NUMBER 		    상품명 NOT NULL VARCHAR2(30) 
NAME      VARCHAR2(15) 	상품명 NOT NULL VARCHAR2(30)  	가격 NOT NULL NUMBER   
TEL1      VARCHAR2(15) 	매출액          NUMBER(38)   		재고 NOT NULL NUMBER  
TEL2      VARCHAR2(15) 	매출일자 NOT NULL DATE
TEL3      VARCHAR2(15)	 매입여부          NUMBER  
EMAIL1    VARCHAR2(15) 	매출수량          NUMBER 
EMAIL2    VARCHAR2(15) 	매입자ID          VARCHAR2(30) 
TIME      NUMBER(10)   
ON_OFF    NUMBER(1)    
SEAT      NUMBER(2)    
 <table>
   <tr><td colspan="6">테이블></td></tr>
   <tr><td colspan="2">PCMANAGER</td><td colspan="2">매상</td><td colspan="2">물품</td></tr> 
   <tr><td>이름</td><td>VARCHAR2(15)</td><td>이름</td><td>속성</td><td>이름</td><td>속성</td></tr>
   <tr><td>ID</td><td>VARCHAR2(15)</td><td>거래번호</td><td>속성</td><td>름</td><td>속성</td></tr>
   <tr><td>PW</td><td>VARCHAR2(15)</td><td>상품번호</td><td>속성</td><td>름</td><td>속성</td></tr>
   <tr><td>NAME</td><td>VARCHAR2(15)</td><td>상품명</td><td>속성</td><td>름</td><td>속성</td></tr>
   <tr><td>TEL1</td><td>VARCHAR2(15)</td><td>매출액</td><td>속성</td><td>름</td><td>속성</td></tr>
   <tr><td>TEL2</td><td>VARCHAR2(15)</td><td>매출일자</td><td>속성</td><td>름</td><td>속성</td></tr>
   <tr><td>TEL3</td><td>VARCHAR2(15)</td><td>매입여부</td><td>속성</td><td>름</td><td>속성</td></tr>
   <tr><td>EMAIL1</td><td>VARCHAR2(15)</td><td>매출수량</td><td>속성</td><td>름</td><td>속성</td></tr>
   <tr><td>EMAIL2</td><td>VARCHAR2(15)</td><td>매입자ID</td><td>속성</td><td>름</td><td>속성</td></tr>
   <tr><td>TIME</td><td>NUMBER(10)</td><td rowspan="3" colspan="2"></td><td rowspan="3" colspan="2"></td></tr>
   <tr><td>ON_OFF</td><td>NUMBER(1)</td><td>름</td><td>속성</td><td>름</td><td>속성</td></tr>
   <tr><td>SEAT</td><td>NUMBER(2)</td><td>름</td><td>속성</td><td>름</td><td>속성</td></tr>
</table>

# 프로그램 설계에 관련된 기술
 해당 프로그램은 JAVA 프로그래밍 언어로 설계되어 있습니다. 또한 DB 구현을 위한 데이터베이스 언어(SQL)가 포함되어 있습니다. 화면 설계는 JAVA API 중
대표적으로 JFRAME, SWING 등이 적용되었으며 그밖에 다양한 API을 적용시켰습니다. JAVA 프로그래밍 기술은 멀티스레드, 소켓프로그래밍을 포함하며,
객체지향의 개념에 충실하도록 다수의 bean 클래스를 작성하여 연계시킨 구조로 설계하였습니다.

# 참고

 <a href="#">팀프로젝트 중 본인 역할 분담분 설명서(PDF)[작성중]</a><br>
 <a href="https://drive.google.com/open?id=1WtERjyNFkspwlDFMkLOpS1nj3XVThunA">팀프로젝트 설명서(PDF)[참고용]</a>

