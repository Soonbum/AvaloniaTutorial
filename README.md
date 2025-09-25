# Avalonia 튜토리얼

* 본 문서는 Avalonia 공식 문서에서 참조하였습니다.
  - [Avalonia Docs](https://docs.avaloniaui.net/docs/welcome)

* 설치 방법
  - Windows의 경우: Microsoft Visual Studio 2022 > 확장 > 확장 관리 > 찾아보기 해서 다음을 설치할 것
    * Avalonia for Visual Studio 2022
    * Avalonia Template Studio

* 지원 IDE
  - JetBrains Rider
  - Visual Studio
  - Visual Studio Code

* Avalonia 프레임워크를 선택해야 할 이유
  - C# .NET 지원
  - WPF는 윈도우 전용 프레임워크이지만, Avalonia는 Windows, MacOS, Linux, Android, iOS, WebAssembly 등 다양한 플랫폼을 지원함 (크로스 플랫폼 지원)
  - Skia 또는 Direct2D 기반 GPU 렌더링을 사용하므로 매우 빠르고 화려함 (Windows Forms는 CPU 렌더링)

* Avalonia 프레임워크의 고유한 특징
  - WPF는 Blend라는 Designer 툴이 있지만, Avalonia는 실시간 미리보기(Live Preview), 핫 리로드(Hot Reload)를 통해 시각적 피드백을 받으면서 코드를 작성해야 함
  - WPF와 유사한 AXAML로 View 디자인 가능하고 MVVM 패턴에 적합함 (그러나 WPF와 세부적인 차이가 다수 존재함)
  - Windows Forms는 이벤트 기반 동작을 하지만 WPF나 Avalonia는 커맨드, 데이터 바인딩으로 동작을 제어함

* MVVM 패턴
  - Model: 데이터를 의미함 (자료형, 클래스, 이미지 등), C# 코드로 작성함
  - View: 사용자에게 보여주는 그래픽 인터페이스 부분, AXAML 문서로 작성함 (주의사항: 가급적 .axaml.cs 코드는 사용하지 말 것!) (Binding 키워드를 이용해 ViewModel에서 업데이트하는 프로퍼티를 연결함)
  - ViewModel: Model과 View 사이의 중간자 역할로 Frontend와 Backend 양쪽으로부터 들어오는 요청을 대응함 (여기에 PropertyChanged 이벤트를 구현한 INotifyPropertyChanged 인터페이스를 구현하면 프로퍼티가 변경될 때마다 View가 자동으로 업데이트됨)

* 뷰의 구성요소: [컨트롤](https://docs.avaloniaui.net/docs/basics/user-interface/controls/builtin-controls)
  - 레이아웃
    * Border: Child 컨트롤의 경계/배경을 꾸민다. 그 외 경계선 두께, 모서리 반지름, 그림자를 표현할 수 있다.
      - 예시: <img width="529" height="146" alt="image" src="https://github.com/user-attachments/assets/0a5e2209-573a-475b-ab67-7147f8bf8e2e" />

    * Canvas: Child 컨트롤을 좌표를 이용해 특정 위치에 표시한다. Z-index로 노출 순서를 제어할 수 있다. (좌상단이 원점이다. Border 바깥의 여백은 Margin, Border 내부의 여백은 Padding이라고 함)
      - 예시: <img width="448" height="412" alt="image" src="https://github.com/user-attachments/assets/cd81e0b7-b30b-495b-a87a-e17249d9750b" />

    * DockPanel: Child 컨트롤을 모서리에 도킹시킨다. (Top, Bottom, Left, Right)
      - 예시: <img width="441" height="399" alt="image" src="https://github.com/user-attachments/assets/d3ed4bf9-e22a-439d-a006-6b00d0e9a693" />

    * Expander: Expand/Collapse 기능으로 Child 컨트롤을 보여주거나 숨길 수 있다.
      - 예시: <img width="563" height="258" alt="image" src="https://github.com/user-attachments/assets/e5c5d30b-4351-4d06-9e5e-9dbdd7002e72" />

    * Grid: Child 요소들을 column, row 번호로 정렬한다. (절대값, 상대값, 자동크기 가능) Child 요소들은 0-기반 인덱스로 어떤 셀에 위치할지 지정한다. (만약 여러 컨트롤을 한 셀 안에 넣으려면 Panel 태그 등으로 감싸면 됨)
      - 예시: <img width="802" height="482" alt="image" src="https://github.com/user-attachments/assets/5dd4113f-b50e-485a-adf2-5d516097c563" />

    * GridSplitter: 사용자가 Grid를 실시간으로 리사이즈할 수 있게 해준다. Grid 태그 안에 들어가야 한다.
      - 예시: <img width="800" height="800" alt="image" src="https://github.com/user-attachments/assets/53c0c433-81bb-49ea-8598-68f783b6a707" />

    * Panel: 여러 Child 컨트롤을 품어주는 역할을 한다. 수평/수직 크기로 전체 크기를 지정할 수 있다.
      - 예시: <img width="327" height="329" alt="image" src="https://github.com/user-attachments/assets/b882064b-d348-4e22-a06a-2b372580b46b" />

    * RelativePanel: Panel과 비슷하나 Child 컨트롤들이 서로 정렬할 수 있게 해준다.
      - 예시: <img width="338" height="334" alt="image" src="https://github.com/user-attachments/assets/ccafaf9d-2ef8-4ed6-8057-d650324fac3e" />

    * ScrollViewer: 작은 공간 안에서 잘린 Child 요소들을 스크롤 바를 움직여 볼 수 있게 해준다. (단, ScrollViewer, DataGrid, ListBox, TextBox, TreeView는 자체 스크롤 바가 있으므로 연쇄 스크롤 바를 On/Off 할 수 있음)
      - 예시: <img width="458" height="343" alt="image" src="https://github.com/user-attachments/assets/122d372a-b691-44eb-99f8-b4ff2a39b177" />

    * SplitView: 메인 컨텐트와 측면 Pane으로 나누어서 보여준다. 측면 Pane은 평소 숨겨져 있고 일시적으로 펼칠 수 있다.
      - 예시: <img width="892" height="517" alt="image" src="https://github.com/user-attachments/assets/caa20252-71e8-4e24-832d-06ed31c68f89" />

    * StackPanel: 여러 Child 컨트롤들을 수평 혹은 수직 방향으로 정렬한다.
      - 예시: <img width="230" height="282" alt="image" src="https://github.com/user-attachments/assets/e9c7f92e-76f5-459b-bb63-542f385778f6" />

    * TabControl: 내부에 TabItem 태그를 넣어서 컨텐트 공간을 나눌 수 있다.
      - 예시: <img width="638" height="447" alt="image" src="https://github.com/user-attachments/assets/d2be82c3-f321-4aab-9f7f-c92f1fefce76" />

    * UniformGrid: Grid와 비슷하나 내부 공간이 균일하게 나눠져 있다.
      - 예시: <img width="344" height="243" alt="image" src="https://github.com/user-attachments/assets/dd3fc463-2227-4092-a1c6-2bdff78028c3" />

    * WrapPanel: 여러 Child 컨트롤들을 수평 혹은 수직 방향으로 이어서 배치한다.
      - 예시: <img width="506" height="456" alt="image" src="https://github.com/user-attachments/assets/f838222e-bef6-490e-b9a5-10e552fbee8e" />

  - 버튼
    * Button: 말 그대로 버튼이다. Click 이벤트를 처리할 수 있다.

    * RepeatButton: 일반 버튼과 달리 꾹 누르면 연속 Click 이벤트를 발생시킬 수 있다. (Delay, Interval 프로퍼티 있음)

    * RadioButton: 한 그룹 안에서 하나만 선택해야 할 때 사용하는 버튼이다.

    * ToggleButton: 토글 버튼으로 눌려 있거나 안 눌려 있음을 표현할 수 있다.

    * ButtonSpinner: 화살표 2개가 표시되어 있는 컨트롤로서 값을 증감할 때 사용한다. (좌우 혹은 상하 화살표)
      - 예시: <img width="166" height="64" alt="image" src="https://github.com/user-attachments/assets/1d00f8db-db3b-4289-858a-2365ea485cde" />

    * SplitButton: 콤보박스와 비슷한 기능을 하는 컨트롤이다. 텍스트뿐만 아니라 이미지 Picker 역할도 할 수 있다.
      - 예시 1: <img width="153" height="123" alt="image" src="https://github.com/user-attachments/assets/43b3612a-7aad-481a-8335-401bdcb116ca" />
 
      - 예시 2: <img width="226" height="257" alt="image" src="https://github.com/user-attachments/assets/31af94ae-4e6c-4389-9d6c-4bd8ac44b666" />
 
      - 예시 3: <img width="282" height="66" alt="image" src="https://github.com/user-attachments/assets/44f97fdf-6455-4b26-a885-dd2fe63619dd" />

    * ToggleSplitButton: SplitButton과 동일하나 ToggleButton처럼 Checked/Unchecked 상태가 추가되어 있다.

  - 반복된 데이터 표현
    * DataGrid: Windows Forms의 DataGridView와 같은 컨트롤이다. .cs 파일에서 List 객체와 연동시킬 수 있다.
      - 예시: <img width="646" height="439" alt="image" src="https://github.com/user-attachments/assets/576e643a-a828-405e-a8f4-257629f401b7" />

    * ItemsControl: 반복된 데이터를 표현하는 컨트롤 중 하나이다. ListBox, ComboBox, DataGrid가 이것을 상속 받았다.
      - 예시: <img width="646" height="439" alt="image" src="https://github.com/user-attachments/assets/26e6e8ce-6cec-472c-a6bd-b4ea50680770" />

    * ItemsRepeater: ItemsControl과 비슷하나 ScrollView, Layout을 직접 붙여야 한다. ItemsControl보다 가볍다. (항목 수량이 많을 때 권장함)
      - 예시 1: <img width="640" height="439" alt="image" src="https://github.com/user-attachments/assets/678b23e4-203e-46d1-bd77-16302e3c9a5b" />
 
      - 예시 2: <img width="646" height="439" alt="image" src="https://github.com/user-attachments/assets/64fcd71a-5e0a-4577-95d8-701aa075e472" />

    * ListBox: Windows Forms의 리스트박스와 같은 기능을 하는 컨트롤이다.
      - 예시: <img width="640" height="439" alt="image" src="https://github.com/user-attachments/assets/f146c371-6cb8-4b39-bd84-4aaa2378e56d" />

    * ComboBox: Windows Forms의 콤보박스와 같은 기능을 하는 컨트롤이다.
      - 예시: <img width="640" height="439" alt="image" src="https://github.com/user-attachments/assets/4a98461d-d7c9-4236-9084-e48625fe8ad2" />
    
  - 텍스트 편집/표시
    * AutoCompleteBox: 텍스트박스에 자동 완성이 추가된 컨트롤이다.

    * TextBlock: Windows Forms의 Label과 같은 역할을 하는 컨트롤이다. 텍스트 표시만 하고 편집은 불가능하다.
      - 예시: <img width="655" height="426" alt="image" src="https://github.com/user-attachments/assets/af200fc4-4bcd-4d2d-bb48-2c7847840500" />

    * TextBox: 텍스트 입력을 받을 때 사용하는 컨트롤이다. 일반/암호 입력용으로 사용할 수 있고 싱글/멀티 라인도 표현할 수 있다.
      - 예시: <img width="640" height="439" alt="image" src="https://github.com/user-attachments/assets/36031759-1525-47ce-ac49-471edc93a6aa" />

    * SelectableTextBlock: TextBlock과 비슷하나 텍스트를 선택/복사할 수 있다.
      - 예시: <img width="655" height="426" alt="image" src="https://github.com/user-attachments/assets/7a1474ac-3291-4e06-b03a-042ab461db39" />

    * MaskedTextBox: TextBox와 비슷하나 특정 포맷으로만 입력할 수 있게 해준다. (예: 전화번호 등)
      - 예시: <img width="640" height="439" alt="image" src="https://github.com/user-attachments/assets/15fb1a31-c9bf-467b-900a-45f2adeb3a7a" />

  - 값 선택
    * CheckBox: Windows Forms의 체크박스와 같은 기능을 하는 컨트롤이다. (3가지 상태를 표현할 수도 있다: Checked/Unchecked/Unknown)
      - 예시: <img width="631" height="393" alt="image" src="https://github.com/user-attachments/assets/24963602-0939-46c2-93af-abab3dcb86fd" />

    * Slider: 슬라이더 컨트롤
      - 예시: <img width="631" height="393" alt="image" src="https://github.com/user-attachments/assets/a9790683-a254-4018-8589-21acc6b27801" />

    * Calendar: 캘린더 컨트롤
      - 예시: <img width="638" height="447" alt="image" src="https://github.com/user-attachments/assets/125e9fe6-cc3a-4a58-8273-854ccfcc3bbe" />

    * CalendarDatePicker: 날짜를 선택할 때 사용하는 컨트롤이다.
      - 예시: <img width="638" height="447" alt="image" src="https://github.com/user-attachments/assets/11cebe05-f037-4dab-ab4e-bd8c453368c2" />

    * ColorPicker: 컬러 피커 컨트롤

    * DatePicker: 날짜 선택 컨트롤이며 CalendarDatePicker와 스타일이 약간 다르다.
      - 예시: <img width="638" height="447" alt="image" src="https://github.com/user-attachments/assets/93caf2fc-6b16-4c27-82f5-eba6c08e19f0" />

    * TimePicker: 시간 선택 컨트롤
      - 예시: <img width="638" height="447" alt="image" src="https://github.com/user-attachments/assets/6990c2fa-f099-4fb4-bf5d-4d90829582c8" />

  - 이미지 표시
    * Image: Raster 이미지를 표현하는 컨트롤이다. (문자열로 이미지 경로를 지정하거나, 파일 혹은 메모리 스트림으로부터 Bitmap을 로드할 수 있음)

    * PathIcon: 아이콘 표현을 위한 컨트롤이다.

  - 메뉴/팝업
    * Menu: 메뉴를 구성하기 위한 컨트롤이다. Menu 태그 밑에 MenuItem을 다단계로 nesting하여 구현할 수 있다.
      - 예시: <img width="646" height="439" alt="image" src="https://github.com/user-attachments/assets/c1e907ea-3ba1-4d13-934c-b767afa4d161" />

    * Flyouts: Tooltip 컨트롤과 달리 특정 이벤트에 의해 나타나게 할 수 있으며 텍스트 외에도 여러 가지 컨트롤을 표시할 수 있다. 주로 무엇을 해야 할지 제시할 때 사용한다.

    * ToolTip: 사용자가 컨트롤 위에 마우스 포인터를 올려놓았을 때 잠시 나타나는 임시 텍스트이다. 주로 힌트를 보여줄 때 사용한다.

* 스타일
  - Avalonia의 스타일 설정 방식은 WPF/UWP 스타일보다는 CSS 스타일에 가깝다.
  - 예시 코드
    ```axaml
    <Window ... >
        <Window.Styles>
            <Style Selector="TextBlock.h1">
                <Setter Property="FontSize" Value="24"/>
                <Setter Property="FontWeight" Value="Bold"/>
            </Style>
        </Window.Styles>
        <StackPanel Margin="20">
           <TextBlock Classes="h1">Heading 1</TextBlock>
        </StackPanel>
    </Window>    
    ```
  - 예시 이미지: <img width="437" height="134" alt="image" src="https://github.com/user-attachments/assets/db06e2ac-da66-485d-9970-1810bad40384" />
  - 또한, Theme 설정도 가능하다.
    * 예시 1: <img width="900" height="700" alt="image" src="https://github.com/user-attachments/assets/e1d55c78-9899-4bbf-bab5-8a69f660c4a0" />
    * 예시 2: <img width="900" height="700" alt="image" src="https://github.com/user-attachments/assets/d5d038f2-54af-4bb9-8f7b-ecab35145e0e" />
    * 예시 3: <img width="900" height="600" alt="image" src="https://github.com/user-attachments/assets/5d1d0052-744e-4afc-9b20-ff9888993162" />

* [데이터 바인딩](https://docs.avaloniaui.net/docs/basics/data/data-binding/data-binding-syntax)
  - AXAML로 작성된 코드에서 실제로 작동하는 .cs 파일의 변수를 연결시킬 수 있다. (변수 값이 바뀌면 뷰 내의 값도 자동으로 업데이트 됨)
  - 데이터 바인딩 문법: `<SomeControl SomeProperty="{Binding Path, Mode=ModeValue, StringFormat=Pattern}" />`
    * Path는 변수 이름으로 설정하면 된다. (`Binding` 또는 `Binding .`는 빈 경로를 의미함 / 다른 요소를 참조할 때에는 #을 앞에 붙이면 됨 / $parent로 부모 요소를 참조할 수 있음)
    * Mode
      - OneWay: 변수 값 --> 뷰로 업데이트 (예: TextBlock.Text 프로퍼티)
      - TwoWay: 변수 값 <--> 뷰로 업데이트 (예: TextBox.Text 프로퍼티)
      - OneTime: OneWay와 동일하나 1번만 업데이트됨
      - OneWayToSource: OneWay의 반대 방향으로 업데이트됨
    * Source: Path에 대한 루트 객체를 명시함 (기본적으로 DataContext)
    * StringFormat: OneWay 바이딩에 한해 정규표현식을 이용하여 문자열 포맷을 지정할 수 있음
    * Priority: ...
    * ElementName: ...
    * RelativeSource: ...
    * Converter: ...
    * ConverterParameter: ...
    * FallbackValue: ...
    * TargetNullValue: ...
    * UpdateSourceTrigger: ...

* 데이터 템플릿: 요소를 조합하여 더욱 풍성하고 화려한 커스텀 요소를 만들 수 있다.
  - 예제
```axaml
<ListBox ItemsSource="{Binding Items}">
  <ListBox.ItemTemplate>
    <DataTemplate>
        <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding Name}" />
            <Image Source="{Binding ImageSource}" />
        </StackPanel>
    </DataTemplate>
  </ListBox.ItemTemplate>
</ListBox>
```

* 의존성 주입 (Dependency Injection, DI)
  - ...

...
