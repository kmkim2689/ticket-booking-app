## Flutter-Tutorial

### default template of flutter

* lib
    * 가장 중요한 패키지로, 실질적인 Flutter 개발을 위한 패키지
    * Dart Code로 구성

* pubspec.yaml
    * 프로젝트의 메타데이터를 정의하고 관리하는 파일
    * 플러터 앱을 구성(configure)
    * 주요 정보들
        * name : 프로젝트명
        * description : 프로젝트 설명
        * version : 버전
        * environment : 사용 환경 version of dart sdk
        * dependencies
        * third-part libraries
        등등...


* 다양한 플랫폼 배포을 위한 패키지들로, 필요 없는 플랫폼은 제거해도 무방하다.
    * android
    * ios
    * linux
    * macos
    * web
    * windows

* test
    * Dart 관련 코드들을 테스트해볼 수 있음
    
* Configuration을 위한 파일들
    * android > build.gradle
    * ios > Runner > info.pilist

---

### Emulator Setup

* vscode 기준, 에뮬레이터 실행
* Ctrl + Shift + p > Flutter : Select Device

---

### Widget of Flutter

> 정적 vs 동적

* Widget

    * 일반적 의미의 Widget
        * 독립적으로 실행되는 작은 프로그램으로, 주로 바탕화면 등에서 날씨나 뉴스, 생활정보 등을 보여주는 것을 생각해볼 수 있음
        * 그래픽이나 데이터 요소를 처리하는 함수로 개발됨

    * Flutter 상의 Widget?
        * 의미 : 앱에서 UI를 만들고 구성하는 모든 기본 단위 요소를 이른다. 
            * text, icon, image, textfield, button...
        * 즉, 애플리케이션에서 눈에 보이는 모든 것이 Widget이라고 볼 수 있는데, 그렇다면 눈에 보이는 것만 Widget일까?
            * Flutter에서는, 눈에 보이지 않는 요소들까지 Widget
            * UI 디자인과 관련, 레이아웃 설계를 돕는 요소들까지 Widget으로 칭함
                * 요소들을 중앙으로 정렬하도록 하는 기능을 담당하는 center
                * 요소들을 세로로 배치시키도록 하는 Column
                * 이미지의 위치를 지정하는 padding
                등등....
        * Flutter 상에서 Widget은 레이아웃을 정의하는 모든 요소들로, 가시성의 여부는 Widget인지 아닌지를 결정하지 않는다. 
        
        > 결국, 모든 것이 위젯이다. 앱의 요소뿐만 아니라 앱의 요소들이 모여 만들어진 하나의 애플리케이션 역시 위젯

* 위젯의 타입

    * stateful vs stateless
        * stateful : 상호작용을 바탕으로 변화하는 value를 지속적으로 추적하며 보존한다는 의미
        * stateless : 이전 상호작용의 어떠한 값도 저장하지 않는다

    1. Stateless Widget
        * 상태가 없는 '정적'인 위젯
        * 움직임이나 변화가 전혀 없는 위젯
        * 특징
            * 앱 화면 상에 존재만 할 뿐, 상호작용과 관련된 모든 것과 관련 없다.
            * 어떠한 실시간 데이터도 저장하지 않는다.
            * 변화를 발생시키는 value도 가지지 않는다.
        * 예시
            * 단순 텍스트, 이미지
            * 모양의 변화나 움직임이 없는 모든 위젯

    2. Stateful Widget
        * 움직이거나 변화가 생기는 '동적'인 위젯
        * 어떠한 상태를 가지고 계속 변화하는 위젯
        * 특징
            * 사용자의 상호작용에 따라 모양이 바뀌거나 움직인다.
            * 데이터를 받았을 때, 모양이 바뀜
        * 예시
            * checkbox, radiobutton
            * textfield

    3. Inherited Widget


* Widget Tree

    * 플러터는 모든 것이 위젯
    * 위젯들을 나열하여 앱을 만들어가면, 위젯들끼리는 계층(tree)구조를 가지게 된다.
        * 한 위젯 내에는 얼마든지 다른 위젯들이 들어갈 수 있음 -> 부모 자식 관계
    * Parent Widget -> Widget Container(위젯을 내포한다는 의미)
    * MyApp > MaterialApp > MyHomePage > Scaffold > AppBar(> Text), Center(> Column > Image, TextField, Button)
        * MyApp : 최상위 위젯으로, 앱의 시작점이다. 커스텀 위젯으로, 이곳에서 MaterialApp 위젯이 빌드됨
        * MaterialApp : 실질적으로 전체 앱을 감싸는 위젯으로, MaterialApp 위젯 내부에서 Flutter SDK에서 제공하는 위젯들을 사용할 수 있음
        * MyHomePage : 커스텀 위젯. 여기서부터 본격적으로 앱의 디자인과 기능들이 만들어짐
        * Scaffold : 아주 중요한 위젯으로, 앱 화면과 기능을 구성하기 위한 빈 페이지를 준비하는 위젯
            * AppBar : 앱 상단에 위치하는 바
                * Text : 말 그대로 Text를 띄우기 위한 위젯
            * Center : 눈에 보이지는 않지만, AppBar 아래로 보여질 메인 컨텐츠를 띄우기 위한 위젯
                * Column : 요소들을 세로로 배치하기 위한 위젯
                    * Image
                    * TextField
                    * Button   

---

### Flutter initial project codes

* Flutter Project를 제작하기 위해 해야할 일들
    
    * Custom Widget을 만들 때, 해당 위젯 내부에 무언가 변화하는 값이 들어가게 된다면 Stateful Widget으로 구현하고, 전혀 변하지 않는 화면을 구현한다면 Stateless Widget으로 구현하면 된다.

    * main.dart 파일에서의 작업

    1. Flutter Material Library를 반드시 import하는 것이 최우선
        * 해당 라이브러리를 가져와야만 Flutter Framework SDK에 포함된 기본 위젯들과 Material Design 테마 요소들을 사용할 수 있기 때문
    
        > import 'package:flutter/material.dart'; // import 엔터, fm 엔터

    2. main 함수 작성
        * 애플리케이션의 시작점
        * 컴파일 시, 컴퓨터는 main 함수를 가장 먼저 참조
        
        > void main() => runApp(MyApp());

        * runApp(Widget)
            * Widget 자리에 MyApp()이라는 Custom Widget 넣어줌.(Flutter에서 제공하는 위젯이 아님)
            * Flutter의 최상위 함수로, 최초로 불러오는 위젯이 무엇인지 설정

    3. MyApp 위젯 정의
        * 뼈대를 만드는 역할
        * 그렇기 때문에, 어떠한 변화나 움직임은 존재하지 않는다. 즉, Stateless Widget이다.
        
        > class MyApp extends StatelessWidget {
            @override
            Widget build(BuildContext context) {
                return Container(

                );
            }
        }

        * 모든 Custom Widget은 다른 Widget을 return하는 'build'라는 이름의 함수를 가지고 있다.
            * Container라는 Widget을 반환

        * 여기서 최소한의 틀을 만든 셈

        * 본격적으로 앱을 디자인. import했던 Flutter Material Library를 사용할 수 있는 기능을 가진 위젯을 return하도록 해야 함. 그 위젯이 바로 MaterialApp

        > class MyApp extends StatelessWidget {
            @override
            Widget build(BuildContext context) {
                return MaterialApp(
                    // 플러터 프레임워크가 제공하는 모든 기본 위젯과 디자인 테마 사용 가능

                );
            }
        }

    4. MaterialApp 위젯 구체화
        * constructors
            * title : 문자열로, 애플리케이션의 이름을 설정
            * theme : 애플리케이션의 기본 디자인 테마 설정
                * ThemeData(primarySwatch: Colors.blue) // swatch는 견본으로, 앱에서 기본적으로 사용할 색상 견본. 견본일 뿐이므로, 정해준 색상만을 사용하는 것이 아니라, 해당 색상의 음영을 조절하여 다양하게 사용 가능. Colors.blue로 설정함은 다양한 색상 중 blue 계열의 음영을 사용하겠다는 의미
            * home : 앱이 정상적으로 실행되었을 때, 가장 먼저 화면에 보여지는 경로. 여기에 다른 위젯을 설정. MyHomePage() 커스텀 위젯

        > class MyApp extends StatelessWidget {
            @override
            Widget build(BuildContext context) {
                return MaterialApp(
                    title: "My First App",
                    theme: ThemeData(
                        primarySwatch: Colors.deepPurple,
                    ),
                    home: MyHomePage(),
                );
            }
        }

    5. MyHomePage() Custom Widget 제작
        * 해당 위젯의 경우, 변화하는 값이 필요하지 않다고 가정하여 Stateless Widget을 구현
        * MaterialApp()과 대체로 동일하나, 여기서는 Scaffold를 return하도록 한다.
            * Scaffold : 발판. 앱 화면에 다양한 요소들을 배치하고 그릴 수 있도록 도와준다는 점에서 매우 중요
        * Scaffold constructors
            * appBar: 앱바를 정의
                * AppBar(title: Text("My First App"))
            * body : 말 그대로 앱바 아래의 주요 부분(몸통). The primary Content of the Scaffold
                * Center() : 화면의 모든 요소들을 중앙에 배치
                    * child // Center의 constructor
                        * Column() : 세로로 배치
                            * children : [] 내부에 위젯들을 배열. 각 위젯은 쉼표(,)로 구분

        > class MyHomePage extends StatelessWidget {
            @override
            Widget build(BuildContext context) {
                // 본격적으로 앱 화면에 보여질 요소들을 디자인
                return Scaffold(
                    appBar: AppBar(
                        title: Text("My First App"), // 앱바에서 보여주는 타이틀
                    ),
                    body: Center(
                        child: Column(
                        children: [Text("hello, welcome back"), Text("Login to Continue")],
                        ),
                    ),
                );
            }
        }

---

### Charater Page Design

* 기본 코드

        import 'package:flutter/material.dart';
        
        // 캐릭터 페이지 디자인
        void main() => runApp(MyApp());
        
        class MyApp extends StatelessWidget {
        
          @override
          Widget build(BuildContext context) {
            return MaterialApp(
              title: "Character Card", // 앱 이름
              theme: ThemeData(
                primarySwatch: Colors.deepPurple,
              ),
              home: MyCard(),
            );
          }
        }
        
        class MyCard extends StatelessWidget {
          @override
          Widget build(BuildContext context) {
            return Scaffold(
              appBar: AppBar(
                title: Text("Character Card"),
              ),
            );
          }
        }

* Scaffold의 생성자들
    * backgroundColor : body의 background color
    * appBar : AppBar 설정
    * body : AppBar 아래 주요 화면 구현

* AppBar의 생성자들
    * title을 중앙에 넣고자 한다면?
        * AppBar의 centerTitle 생성자를 true로 설정
    * AppBar의 Background 색상을 지정해주고 싶다면?
        * backgroundColor 생성자를 색깔로 설정
        * Colors.색상명 // Material에서 지원해주는 색상
    * AppBar의 그림자를 설정하는 elevation
        * AppBar가 표면으로부터 띄워져있는 효과를 얼마나 줄 것인지 설정 가능
        * 소수점 단위까지 정밀하게 설정 가능

* Center
    * child 생성자 존재 => 'child' 위젯을 정중앙에 배치하는 역할
    * 주의
        * Center위젯의 child로 어떤 위젯이 오느냐에 따라 정중앙으로 배치되는 것이 다르다.
        * Center 위젯의 자식 위젯으로 Column이 온다면 좌우로 정중앙으로 정렬해주지만, 상하 정렬은 Column의 mainAxisAlignment에서 결정된다.
        * 반면 자식 위젯으로 Row가 온다면, 상하로 정중앙으로 정렬해주지만, 좌우정렬은 Row의 mainAxisAlignment에서 결정된다.

* Padding
    * 사용하고자 하는 위젯이 특정 지점으로부터 얼마나 떨어지도록 할 것인지 그 거리를 설정하도록 하는 보이지 않는 Widget
    * 생성자들
        * padding: EdgeInsets.from~
            * 'children 요소'들이 Padding 컨테이너의 상하좌우 끝에서 얼만큼 떨어지도록 할 것인지 설정한다.
            * fromLTRB : 상하좌우 모두 설정

* Column
    * mainAxisAlignment
        * Column은 위아래로 children을 배치한다. mainAxis라는 것은 column의 정렬 방식인 위아래 방향의 축이라고 보면 된다.
        * column의 Alignment는 위아래로 어느 곳에 children들을 정렬시킬 것인지 결정하는 것이다.
        * MainAxisAlignment.xxx
            * start
            * end
            * center
            * spaceBetween
            * spaceAround
            ...

    * crossAxisAlignment
        * mainAxis와 수직 방향의 축을 기준으로 정렬
        * 즉 Column에서 crossAxisAlignment는 Column 내부 children에 대한 좌우 정렬을 결정
        * CrossAxisAlignment
            * start
            * end
            * center
            * stretch
            * baseline...


* Text
    * data : 말 그대로 들어갈 텍스트 내용
    * named constructors
        * style : 텍스트의 스타일을 지정
            * TextStyle로 지정 가능
                * color, fontWeight, fontSize, letterSpacing... 등등

* SizedBox
    * 요소 간 간격 설정을 위하여 사용되는 위젯
    * 생성자들로 width, height, child 등이 있다


* 이미지 사용하는 방법
    * pubspec.yaml
    * assets가 주석처리 되어있는 것을 해제
    * 이미지에 대한 경로를 명시해준다.
    > assets/pic.jpg
    * indentation에 유의하기

* CircleAvatar 위젯
    * Flutter에서 제공하는, 원형으로 이미지를 넣을 수 있는 위젯
    * 둥글게 프로필 사진을 만들고 싶을 때 사용
    * constructors
        * backgroundImage : AssetImage(이미지경로)
        * radius : circle의 크기를 조절 가능
        * backgroundColor : png 파일의 경우 circleavatar가 위치하는 배경의 색과 동일하게 하면 해당 이미지만 있는 것 같은 효과 조성 가능
    * tip
        * CircleAvater 위젯에 나타나는 노란 전구 아이콘 클릭
        * Wrap with Center -> 해당 위젯을 Center로 감싸줌으로써 CircleAvatar를 가운데 정렬 가능

* Divider 위젯
    * 구분선을 그려줌
    * height : 공간의 전체 높이. divider는 상하로 중앙에 위치한다. divider 위로 30px padding, 아래로 30px padding이 주어진다는 의미
    * color : 색상
    * thickness : 두께
    * endIndent : 끝에서부터 얼만큼 떨어뜨릴 것인지
    * 여기서는 body의 padding이 좌로 30으로 지정되어 있기 때문에 endIndent를 startpadding과 같은 값으로 설정하면 됨

* 코드

    import 'package:flutter/material.dart';
    
    // 캐릭터 페이지 디자인
    
    void main() => runApp(MyApp());
    
    class MyApp extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return MaterialApp(
          debugShowCheckedModeBanner: false,
          title: 'Character',
          home: Grade(),
        );
      }
    }
    
    class Grade extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return Scaffold(
            backgroundColor: Colors.amber[800],
            appBar: AppBar(
              title: const Text('Character'),
              backgroundColor: Colors.amber[700],
              centerTitle: true,
              elevation: 0.0,
            ),
            body: Padding(
              padding: EdgeInsets.fromLTRB(30.0, 40.0, 0.0, 0.0),
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: <Widget>[
                  Center(
                    child: CircleAvatar(
                      backgroundImage: AssetImage("assets/pic.jpg"),
                      radius: 40.0,
                    ),
                  ),
                  Divider(
                    height: 60.0,
                    color: Colors.grey[850],
                    thickness: 0.5,
                    endIndent: 30.0,
                  ),
                  Text(
                    "Name",
                    style: TextStyle(
                      color: Colors.white,
                      letterSpacing: 2.0,
                    ),
                  ),
                  SizedBox(
                    height: 10.0,
                  ),
                  Text(
                    "banto",
                    style: TextStyle(
                      color: Colors.white,
                      letterSpacing: 2.0,
                      fontSize: 28.0,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                  SizedBox(
                    height: 30.0,
                  ),
                  Text(
                    "level",
                    style: TextStyle(
                      color: Colors.white,
                      letterSpacing: 2.0,
                    ),
                  ),
                  SizedBox(
                    height: 10.0,
                  ),
                  Text(
                    "14",
                    style: TextStyle(
                      color: Colors.white,
                      letterSpacing: 2.0,
                      fontSize: 28.0,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                  SizedBox(
                    height: 30.0,
                  ),
                  Row(
                    children: <Widget>[
                      Icon(
                        Icons.check_circle_outline,
                        color: Colors.white,
                        size: 30.0,
                      ),
                      SizedBox(
                        width: 10.0,
                      ),
                      Text(
                        "using lightsaber",
                        style: TextStyle(
                          color: Colors.white,
                          letterSpacing: 1.0,
                          fontSize: 18.0,
                        ),
                      ),
                    ],
                  ),
                  Row(
                    children: <Widget>[
                      Icon(
                        Icons.check_circle_outline,
                        color: Colors.white,
                        size: 30.0,
                      ),
                      SizedBox(
                        width: 10.0,
                      ),
                      Text(
                        "using lightsaber",
                        style: TextStyle(
                          color: Colors.white,
                          letterSpacing: 1.0,
                          fontSize: 18.0,
                        ),
                      ),
                    ],
                  ),
                  Row(
                    children: <Widget>[
                      Icon(
                        Icons.check_circle_outline,
                        color: Colors.white,
                        size: 30.0,
                      ),
                      SizedBox(
                        width: 10.0,
                      ),
                      Text(
                        "using lightsaber",
                        style: TextStyle(
                          color: Colors.white,
                          letterSpacing: 1.0,
                          fontSize: 18.0,
                        ),
                      ),
                    ],
                  ),
                ],
              ),
            )
        );
      }
    }

---

### AppBar

* AppBar를 이용하여 상당히 많은 기능 구현 가능

* AppBar Widget의 constructor들
    * title
    * centerTitle(Boolean)
    * elevation
    * leading
        * 아이콘 혹은 간단한 위젯을 앱바의 '좌측'에 위치시키는 기능
        * 여기에 IconButton을 할당. 단순히 아이콘만 보여주려 하는 것이 아니라 눌렀을 때 반응해야 하기 때문.
        * IconButton의 필수 속성들
            * 필수 속성 : icon, onPressed
            * IconButton에 있는 icon 속성으로 Icon위젯을 넣는 방식으로 구현
                * Icons라는 Material 제공 아이콘 클래스 사용 가능
            * onPressed에서는 클릭 시 실행되어야 할 내용들을 정의
                * 함수의 형태는 반환값이 없는 함수(void)
    
    * action
        * 아이콘을 앱바의 우측에 위치시키는 기능
        * Widget의 리스트가 올 수 있다.
        * 1개 이상의 아이콘 가능

---

### Drawer

* Drawer의 구성
    * Drawer head
    * Menu

* 주의점
    * Scaffold에 Drawer를 추가할 수 있는데, 이 과정에서 AppBar의 leading 아이콘은 넣어줄 필요가 없다. 자동으로 AppBar에 메뉴 아이콘이 추가되기 때문이다.

* Drawer 구현법
    * Scaffold의 생성자 중 하나 -> Scaffold에 추가
    * Scaffold 하위에 drawer 속성으로 Drawer위젯 호출
        * Drawer의 속성
            * child : ListView()

* ListView
    * 안드로이드의 RecyclerView, LazyColumn/Row/Grid 등과 유사
    * 같은 형태의 아이템을 하나만 보여주는 것이 아니라 여러 개 보여주기 위해 사용
    * ListView에서 아이템 하나하나를 Flutter에서는 'ListTile'이라고 한다.
        * ListTitle에 대한 정의 역시 추후 필요할 것. 다만 플러터에서는 ListTile 포맷을 많이 제공해주고 있음... 커스텀하지 않아도 된다는 의미
            * 속성들
                * padding
                * children
                    * UserAccountsDrawerHeader
                        * Drawer에서 상단에 유저의 사진과 이름, 이메일을 띄울 수 있도록 만들어진 위젯
                        * currentAccountPicture
                            * CircleAvatar 이용함으로써 계정 사진을 둥글게
                        * otherAccountsPicture
                            * 우측 상단에 간단하게 작게 다른 계정의 프로필 사진을 설정 가능
                            * Widget의 리스트 삽입 가능 -> 즉 하나 이상의 다른 계정 추가 가능
                        * accountName, accountEmail 필수
                            * Text 위젯 삽입
                        * onDetailsPressed : void 함수
                            * 유저 정보 옆에 화살표를 띄움으로써, 추가 정보를 확인할 수 있도록 함
                        * decoration : UserAccountsDrawerHeader를 하나의 Box로 간주한다는 점이 포인트. 이것을 꾸미겠다는 의미
                            * BoxDecoration 위젯을 사용
                                * color
                                * borderRadius
                                    * BorderRadius
                                        * .only : 특정 모서리만  radius 설정 가능
                    
                    * ListTile : 반복되는 아이템
                        * leading : 앞에 나오는 아이콘
                        * title
                        * onTap : 탭했을 때 동작 정의
                        * trailing : 우측 끝에 있는 아이콘

                    

    * onPressed vs onTap
        * 기능상으로는 거의 동일
        * onPressed는 주로 버튼에 사용
        * onTap은 주로 gestureDetector나 InkWell에 사용
            * 일반 버튼의 onPressed와는 달리, ListTile 위젯은 길게  누르기, 두 번 탭하기 등 액션을 감지 가능할 수 있음.
            * 예) 길게 누르기, 두 번 누르기 등의 이벤트를 위해 사용 

    
---

### BuildContext


