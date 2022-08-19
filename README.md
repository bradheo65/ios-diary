# 일기장 

## 🙋🏻‍♂️ 프로젝트 소개
일기장 어플 입니다 

> 프로젝트 기간: 2022-08-16 ~ 2022-09-02</br>
> 팀원: [키위](https://github.com/kiwi1023), [브래드](https://github.com/bradheo65) </br>
리뷰어: [제이슨](https://github.com/ehgud0670)</br>


## 📑 목차

- [🧑🏻‍💻🧑🏻‍💻 개발자 소개](#-개발자-소개)
- [📦 파일 구조](#-파일-구조)
- [📱 동작 화면](#-동작-화면)
- [💡 키워드](#-키워드)
- [🤔 핵심경험](#-핵심경험)
- [📚 참고문서](#-참고문서)
- [📝 기능설명](#-기능설명)
- [🚀 TroubleShooting](#-TroubleShooting)
    - [🚀 STEP 1](#-STEP-1)

- STEP 상세 내용
    - [1️⃣ STEP 1](https://github.com/bradheo65/ios-open-market/blob/Step1/Docs/Step01.md)

## 🧑🏻‍💻🧑🏻‍💻 개발자 소개

|||
|:---:|:---:|
|<image src = "https://user-images.githubusercontent.com/45350356/174251611-46adf61c-93fa-42a0-815b-2c998af1c258.png" width="250" height="250">| <image src = "https://user-images.githubusercontent.com/45350356/185553406-b53072a6-5a79-48fe-8812-f6e47c91aa0c.png" width="250" height="250">
|[브래드](https://github.com/bradheo65)|[키위](https://github.com/kiwi1023)|  

## 📦 파일 구조

```
📦Diary
 ┣ 📂Assets.xcassets
 ┃ ┣ 📂AccentColor.colorset
 ┃ ┃ ┗ 📜Contents.json
 ┃ ┣ 📂AppIcon.appiconset
 ┃ ┃ ┗ 📜Contents.json
 ┃ ┗ 📜Contents.json
 ┣ 📂Base.lproj
 ┃ ┗ 📜LaunchScreen.storyboard
 ┣ 📂Controller
 ┃ ┣ 📜DiaryViewController.swift
 ┃ ┗ 📜MainViewController.swift
 ┣ 📂Diary.xcdatamodeld
 ┃ ┣ 📂Diary.xcdatamodel
 ┃ ┃ ┗ 📜contents
 ┃ ┗ 📜.xccurrentversion
 ┣ 📂Model
 ┃ ┣ 📂Json
 ┃ ┃ ┣ 📜JSONDecoder + Extension.swift
 ┃ ┃ ┣ 📜SampleJson.swift
 ┃ ┃ ┗ 📜sample.json
 ┃ ┗ 📜Date + Extension.swift
 ┣ 📂View
 ┃ ┣ 📜DiaryView.swift
 ┃ ┗ 📜MainTableViewCell.swift
 ┣ 📜AppDelegate.swift
 ┣ 📜Info.plist
 ┗ 📜SceneDelegate.swift
```
## 📱 동작 화면

|가로 모드|세로 모드|
|:---:|:---:|
|<image src = "https://user-images.githubusercontent.com/45350356/185554168-e4a1ee8c-58d1-4f02-841d-8268c1517a02.gif" width="250" height="500">|<image src = "https://user-images.githubusercontent.com/45350356/185554478-4cdea87f-4afa-4c0b-a9b6-932b05408d1a.gif" width="400" height="500">|

## 💡 키워드
- JSON
- TableView
- UITextView
- Keyboard layout
    
## 🤔 핵심경험
- [x]  Date Formatter의 지역 및 길이별 표현의 활용
- [x]  Text View의 활용


## 📚 참고문서
- Adaptivity and Layout
- UIKit: Apps for Every Size and Shape
- Making Apps Adaptive, Part 1 / Script
- Making Apps Adaptive, Part 2 / Script
- DateFormatter
- UITextView


## 📝 기능설명
- 작성한 일기장의 목록을 보여주는 Table View 구현
- UITextView를 활용하여 일기장 작성기능 구현
- Json Parsing을 통한 Cell과의 Data 연동
- Notification Center를 활용하여 키보드가 작성중인 화면을 가리지 않도록 기능 구현
    
## 🚀 TroubleShooting
    
### 🚀 STEP 1

#### T1. 키보드 레이아웃 문제
`UITextView`에 많은 내용이 있을 때 키보드를 사용하게 되면 `UITextView` 내용을 가리는 문제가 발생되었습니다. 해당 문제는 `NotificationCenter` 활용해서 `UITextView` 오토레이아웃 Bottom에 키보드 높이에 대한 제약(AutoLayout)을 설정해서 해결했습니다. 하지만 적용 후 다시 테스트 해보니 내용에 대한 `UITextView` 크기는 적용이 되었지만 키보드가 내려갈 시 `UITextView`가 원래 크기로 돌아가지 않았습니다.
해당 문제에 대해서는 NotificationCenter에서 `UIResponder.keyboardWillShowNotification`만 사용했었는데 추가적으로 `UIResponder.keyboardWillHideNotification`을 사용해서 해결할 수 있었습니다. 

|적용 전|적용 후|
|:---:|:---:|
|<image src = "https://user-images.githubusercontent.com/45350356/185552977-3b9daeda-28e8-45e4-b10a-29f0d10b67a5.gif" width="250" height="500">| <image src = "https://user-images.githubusercontent.com/45350356/185552870-35664bba-0537-405a-99d6-c4f31c11bb55.gif" width="250" height="500">
