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
