# 기온별 옷차림(2)

### 기존에 하던 프로젝트랑 다른점은 무엇인가요?

- '또 다른 API를 끌어오면 어떨까?' 라는 이야기를 듣고 시도해 보는 프로젝트라서 네이버 쇼핑 API를 끌어올 예정이고 그에 따른 옷이 어떤것이 있는지 보여주는 프로젝트 입니다.
- 이번에는 Activity가 아닌 Fragment를 이용해 BottomNavigationView를 삽입해 화면을 꾸몄습니다. 그렇게 한 이유는 스토어 기능까지 추가하면 하나의 액티비티로 담으면 복잡할 것으로 
  예상이되서 BottomNavigationView를 이용하기로 했습니다.

### 방금 네이버 쇼핑 API를 끌어온다고 하는데...

- 맞습니다. 뭔가 더 추가할 수 있는 기능이 있지 않을까 고민을 했습니다. 이 API로 현재 날씨에 맞는 옷들이 무엇이 있는지 보여줄 예정입니다.
- 옷들을 보여주는 목록을 클릭하면 네이버 페이지로 이동하게 할 예정입니다.
- 대략적인 이미지

![20210407_234220](https://user-images.githubusercontent.com/68115246/117122084-70ab2800-add0-11eb-8983-b29a20657a06.jpg)

### 이번엔 어떻게 끌어올건가요?

- 이번에는 volley라이브러리가 아닌 Retrofit2로 끌어올 예정입니다.
- 그나마 최근에 나온 라이브러리이자 읽어들이는 속도도 빠르다고 합니다. 아무래도 많은 양의 옷들을 가져오려면 Retrofit2로 써야한다고 생각했습니다.
- Volley와 Retorfit2의 차이점을 알아낸 블로그 : https://cntechsystems.tistory.com/30

### BottomNavigationView를 사용했네요?

- 위에서도 이야기 했듯이 스토어 기능을 넣을 건데 액티비티로 구현하기엔 무겁기도 하고, 화면구성이 복잡할것 같아서 BottomnavigationView를 사용했습니다.
- BottomNavigationView를 알아내고 적용해본 블로그 : https://imleaf.tistory.com/78
- 유튜브 : https://www.youtube.com/watch?v=R1yeoFk-quU

### 어려운 점은 없었나요?

- 우선 프래그먼트에 대해서 알아야 했습니다. 제가 정리했을 때 액티비티는 말 그대로 화면이고, 프래그먼트는 하나의 액티비티 안에서 보여지는 조각을 말합니다. 
- 이를 알게된 블로그 : https://developer88.tistory.com/69
- 또한 프래그먼트 내 버튼을 눌렀을 때 다른 프래그먼트로 이동해야 했습니다. 이 부분을 몰라서 해멨습니다.
- 그리고 네비게이션 바에 있는 버튼을 계속 눌렀을 때 이미지가 제대로 로드가 안됐습니다. NullPoineException을 일으켰습니다. 
  
### 이에 대해 어떻게 해결했는지 간단하게 알 수 있을까요?

- 저는 UI에 대한 이벤트를 onActivityCreated() 메소드에 코딩을 했으며, 프래그먼트를 관리하는 BottomnavMain.kt에서관리를 하게끔 했습니다. 
  BottomnavMain.kt에 viewConfilmWeather()를 선언하고 인자값으로 ArrayList를 받아옵니다. 이를 BottomnavFragment3_1에 넘기는 작업을 코딩했습니다.
  도움이 된 블로그 : https://hijjang2.tistory.com/255?category=856483
  
- BottomnavFragment2 클래스에서 예외처리를 하고 Main에서 이미지가 설정되지 전 까지는 넘어가지 않게 설정했습니다.
  
- 또한 설정한 시간의 날씨를 보여주는 액티비티에서 뒤로가기를 눌렀을 때 시간을 설정하는 액티비티로 향하게 했습니다.
