---
title: "Walkthrough: Implementing Inheritance with COM Objects (Visual Basic) | Microsoft Docs"
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
  - "inheritance, COM reusability"
  - "base classes, COM reusability"
  - "inheritance, walkthroughs"
  - "derived classes, COM reusability"
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

COM オブジェクト内の `Public` クラス \(以前のバージョンの [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で作成されたクラスも含む\) から Visual Basic クラスを派生できます。  COM オブジェクトから継承されたクラスのプロパティとメソッドは、その他の基本クラスのプロパティとメソッドをオーバーライドまたはオーバーロードするのと同じ方法で、オーバーライドまたはオーバーロードできます。  COM オブジェクトからの継承は、再コンパイルしない既存のクラス ライブラリがあるときに利用すると便利です。  
  
 次の手順では、Visual Basic 6.0 を使用してクラスを含む COM オブジェクトを作成し、作成した COM オブジェクトを基本クラスとして使用する方法を示します。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### このチュートリアルで使用する COM オブジェクトを作成するには  
  
1.  Visual Basic 6.0 で、新しい ActiveX DLL プロジェクトを開きます。  `Project1` という名前のプロジェクトが作成されます。  `Class1` という名前のクラスが含まれています。  
  
2.  **プロジェクト エクスプローラー**で、**\[Project1\]** を右クリックし、**\[Project1 のプロパティ\]** をクリックします。  **\[プロジェクト プロパティ\]** ダイアログ ボックスが表示されます。  
  
3.  **\[プロジェクト プロパティ\]** ダイアログ ボックスの **\[全般\]** タブの **\[プロジェクト名\]** フィールドに「`ComObject1`」と入力してプロジェクトの名前を変更します。  
  
4.  **プロジェクト エクスプローラー**で \[`Class1`\] を右クリックし、**\[プロパティ\]** をクリックします。  このクラスの **\[プロパティ\]** ウィンドウが表示されます。  
  
5.  `Name` プロパティを `MathFunctions` に変更します。  
  
6.  **プロジェクト エクスプローラー**で \[`MathFunctions`\] を右クリックし、**\[コードの表示\]** をクリックします。  **コード エディター**が表示されます。  
  
7.  プロパティの値を保持するローカル変数を追加します。  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  Property `Let` および Property `Get` プロパティ プロシージャを追加します。  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. 関数を追加します。  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. **\[ファイル\]** メニューの **\[ComObject1.dll の作成\]** をクリックして、COM オブジェクトを作成および登録します。  
  
    > [!NOTE]
    >  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で作成したクラスも COM オブジェクトとして公開できますが、これは本当の COM オブジェクトではないので、このチュートリアルでは使用できません。  詳細については、「[COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)」を参照してください。  
  
## 相互運用アセンブリ  
 次の手順では、相互運用機能アセンブリを作成します。相互運用機能アセンブリは、アンマネージ コード \(COM オブジェクトなど\) と、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] が使用するマネージ コードの仲介役として機能します。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] によって作成される相互運用機能アセンブリは、*相互運用マーシャリング*など、COM オブジェクトの操作で発生する数多くの詳細な作業を処理します。相互運用マーシャリングとは、COM オブジェクトとの間の変換のときに、パラメーターと戻り値を対応するデータ型にパッケージ化する処理です。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] アプリケーション内の参照は、実際の COM オブジェクトではなく、相互運用機能アセンブリを指します。  
  
#### Visual Basic 2005 以降のバージョンで COM オブジェクトを使用するには  
  
1.  新しい [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] Windows アプリケーション プロジェクトを開きます。  
  
2.  **\[プロジェクト\]** メニューの **\[参照の追加\]** をクリックします。  
  
     **\[参照の追加\]** ダイアログ ボックスが表示されます。  
  
3.  **\[COM\]** タブの **\[コンポーネント名\]** ボックスの一覧の `ComObject1` をダブルクリックし、**\[OK\]** をクリックします。  
  
4.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
     **\[新しい項目の追加\]** ダイアログ ボックスが表示されます。  
  
5.  **テンプレート** ペインの **\[クラス\]** をクリックします。  
  
     既定のファイル名 `Class1.vb` が **\[ファイル名\]** フィールドに表示されます。  このフィールドを「MathClass.vb」に変更し、**\[追加\]** をクリックします。  これで `MathClass` という名前のクラスが作成され、コードが表示されます。  
  
6.  `MathClass` の先頭に次のコードを追加して、COM クラスを継承します。  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#31)]  
  
7.  次のコードを `MathClass` に追加して、基本クラスのパブリック メソッドをオーバーロードします。  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#32)]  
  
8.  次のコードを `MathClass` に追加して、継承されるクラスを拡張します。  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#33)]  
  
 新しいクラスは、COM オブジェクト内の基本クラスのプロパティを継承し、メソッドをオーバーロードし、新しいメソッドを定義してクラスを拡張します。  
  
#### 継承したクラスをテストするには  
  
1.  スタートアップ フォームにボタンを追加し、そのボタンをダブルクリックしてコードを表示します。  
  
2.  ボタンの `Click` イベント ハンドラー プロシージャに、次のコードを追加します。このコードは、`MathClass` のインスタンスを作成し、オーバーロードされたメソッドを呼び出します。  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#34)]  
  
3.  F5 キーを押してプロジェクトを実行します。  
  
 フォーム上のボタンをクリックすると、`Short` 型の数値を使用して `AddNumbers` メソッドが呼び出され、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] によって基本クラスの適切なメソッドが選択されます。  `AddNumbers` の 2 回目の呼び出しは `MathClass` のオーバーロード メソッドに渡されます。  3 回目の呼び出しでは `SubtractNumbers` メソッドが呼び出され、クラスが拡張されます。  基本クラス内のプロパティが設定され、値が表示されます。  
  
## 次の手順  
 オーバーロードされた `AddNumbers` 関数は、COM オブジェクトの基本クラスから継承されたメソッドと同じデータ型を持つように見えます。  これは、基本クラスのメソッドの引数とパラメーターが Visual Basic 6.0 では 16 ビットの整数として定義されているのに対し、以降のバージョンでは `Short` 型の 16 ビットの整数として公開されるためです。  新しい関数は、32 ビットの整数を受け取り、基本クラスの関数をオーバーロードします。  
  
 COM オブジェクトを操作するときは、パラメーターのサイズとデータ型を必ず確認してください。  たとえば、Visual Basic 6.0 のコレクション オブジェクトを引数として受け取る COM オブジェクトを使用するときは、以降のバージョンの Visual Basic のコレクションを提供できません。  
  
 COM クラスから継承されたプロパティとメソッドをオーバーライドできます。これは、COM の基本クラスから継承されたプロパティやメソッドを置き換えるローカルのプロパティやメソッドを宣言できることを意味します。  継承された COM プロパティをオーバーライドする場合の規則は、その他のプロパティやメソッドをオーバーライドする場合の規則と同じですが、次の例外もあります。  
  
-   COM クラスから継承されたプロパティやメソッドをオーバーライドする場合は、その他の継承されたプロパティとメソッドをすべてオーバーライドする必要があります。  
  
-   `ByRef` パラメーターを使用するプロパティをオーバーライドできません。  
  
## 参照  
 [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)   
 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)