---
title: "Walkthrough: Defining Classes (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "execution, ending"
  - "objects [Visual Basic], initializing"
  - "Initialize event"
  - "files, closing"
  - "programs, quitting"
  - "code, exiting"
  - "objects [Visual Basic], creating"
  - "program termination"
  - "classes [Visual Basic], walkthroughs"
  - "class modules, walkthroughs"
  - "Terminate event"
  - "execution, stopping"
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Walkthrough: Defining Classes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このチュートリアルでは、クラスを定義する方法を説明します。クラスを定義したら、オブジェクトの作成に使用できます。  作成したクラスにプロパティとメソッドを追加する方法、およびオブジェクトを初期化する方法についても説明します。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### クラスを定義するには  
  
1.  **\[ファイル\]** メニューの **\[新しいプロジェクト\]** をクリックしてプロジェクトを作成します。  **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
2.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] プロジェクト テンプレートの一覧の Windows アプリケーションを選択して、新しいプロジェクトを表示します。  
  
3.  **\[プロジェクト\]** メニューの **\[クラスの追加\]** をクリックして、新規クラスをプロジェクトに追加します。  **\[新しい項目の追加\]** ダイアログ ボックスが表示されます。  
  
4.  **\[クラス\]** テンプレートを選択します。  
  
5.  新しいクラス `UserNameInfo.vb` に名前を指定し、**\[追加\]** をクリックして新しいクラスのコードを表示します。  
  
     [!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の**コード エディター**を使用して、クラスをスタートアップ フォームに追加できます。クラスを追加するには、`Class` キーワードに続けて新規クラスの名前を入力します。  **コード エディター** によって、対応する `End Class` ステートメントが自動的に入力されます。  
  
6.  `Class` ステートメントと `End Class` ステートメントの間に次のコードを追加して、クラスのプライベート フィールドを定義します。  
  
     [!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     フィールドに `Private` を宣言した場合、そのクラスの内部でのみ使用可能になります。  これらのフィールドをクラスの外部からアクセスできるようにするには、`Public` などのより広いアクセス範囲を提供するアクセス修飾子を使用します。  詳細については、「[Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
7.  次のコードを追加してクラスのプロパティを定義します。  
  
     [!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  次のコードを追加してクラスのメソッドを定義します。  
  
     [!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. `Sub New` というプロシージャを追加して新規クラスのパラメーター化されたコンストラクターを定義します。  
  
     [!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     `Sub New` コンストラクターは、このクラスからオブジェクトを作成するとき自動的に呼び出されます。  このコンストラクターは、ユーザー名を保持するフィールドの値を設定します。  
  
### クラスをテストするボタンを作成するには  
  
1.  スタートアップ フォームをデザイン モードに変更します。変更するには、**ソリューション エクスプローラー**でスタートアップ フォームの名前を右クリックし、**\[デザイナーの表示\]** をクリックします。  Windows アプリケーション プロジェクトのスタートアップ フォームは、既定で Form1.vb という名前が付きます。  メイン フォームが表示されます。  
  
2.  メイン フォームにボタンを追加し、それをダブルクリックして、`Button1_Click` イベント ハンドラーのコードを表示します。  テスト プロシージャを呼び出すために次のコードを追加します。  
  
     [!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### アプリケーションを実行するには  
  
1.  F5 キーを押してアプリケーションを実行します。  フォームのボタンをクリックしてテスト プロシージャを呼び出します。  プロシージャがオブジェクトの `Capitalize` メソッドを呼び出したため、元の `UserName` が "MOORE, BOBBY" であるというメッセージが表示されます。  
  
2.  **\[OK\]** をクリックしてメッセージ ボックスを閉じます。  `Button1 Click` プロシージャは `UserName` プロパティの値を変更し、変更後の `UserName` の値が "Worden, Joe" であるというメッセージを表示します。  
  
## 参照  
 [オブジェクト指向プログラミング](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)