# Avalonia 개발환경 구축

* 설치 방법
  - Windows의 경우: Microsoft Visual Studio 2022 > 확장 > 확장 관리 > 찾아보기 해서 다음을 설치할 것
    * Avalonia for Visual Studio 2022
    * Avalonia Template Studio

* 지원 IDE
  - JetBrains Rider
  - Visual Studio
  - Visual Studio Code

* Avalonia를 선택해야 할 이유
  - C# .NET 지원
  - WPF는 윈도우 전용 프레임워크이지만, Avalonia는 Windows, MacOS, Linux, Android, iOS, WebAssembly 등 다양한 플랫폼을 지원함
  - WPF와 유사한 AXAML로 View 디자인 가능하고 MVVM 패턴에 적합함 (그러나 WPF와 세부적인 차이가 다수 존재함)
  - WPF는 Blend라는 Designer 툴이 있지만, Avalonia는 실시간 미리보기(Live Preview), 핫 리로드(Hot Reload)를 통해 시각적 피드백을 받으면서 코드를 작성해야 함
  - Windows Forms는 이벤트 기반 동작을 하지만 WPF나 Avalonia는 커맨드, 데이터 바인딩으로 동작을 제어함
  - Skia 또는 Direct2D 기반 GPU 렌더링을 사용함 (Windows Forms는 CPU 렌더링)

* MVVM 패턴
  - Model: 데이터를 의미함 (자료형, 클래스, 이미지 등), C# 코드로 작성함
  - View: 사용자에게 보여주는 그래픽 인터페이스 부분, AXAML 문서로 작성함 (주의사항: 가급적 .axaml.cs 코드는 사용하지 말 것!)
  - ViewModel: Model과 View 사이의 중간자 역할로 Frontend와 Backend 양쪽으로부터 들어오는 요청을 대응함

* 뷰의 구성요소: 컨트롤
  - 레이아웃
    * Border: Child 요소의 경계/배경을 꾸민다. 그 외 경계선 두께, 모서리 반지름, 그림자를 표현할 수 있다.
    * Canvas: 
    * Dock Panel
    * Expander
    * Grid
    * Grid Splitter
    * Panel
    * Relative Panel
    * Scroll Viewer
    * Split View
    * Stack Panel
    * Tab Control
    * Uniform Grid
    * Wrap Panel
  - 버튼
    * Button
    * RepeatButton
    * RadioButton
    * ToggleButton
    * ButtonSpinner
    * SplitButton
    * ToggleSplitButton
  - 반복된 데이터 표현
    * DataGrid
    * ItemsControl
    * ItemsRepeater
    * ListBox
    * ComboBox
  - 텍스트 편집/표시
    * AutoCompleteBox
    * TextBlock
    * TextBox
    * SelectableTextBlock
    * MaskedTextBox
  - 값 선택
    * CheckBox
    * Slider
    * Calendar
    * CalendarDatePicker
    * ColorPicker
    * DatePicker
    * TimePicker
  - 이미지 표시
    * Image
    * PathIcon
  - 메뉴/팝업
    * Menu
    * Flyouts
    * ToolTip

* ?
