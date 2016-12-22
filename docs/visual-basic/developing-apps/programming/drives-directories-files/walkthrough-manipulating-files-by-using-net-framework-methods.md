---
title: "Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "I/O [Visual Basic], walkthroughs"
  - "text files, writing to"
  - "reading text files"
  - "text, writing to files"
  - "files, searching"
  - "StreamReader class, walkthroughs"
  - "files, accessing"
  - "I/O [Visual Basic], writing text to files"
  - "writing to files, walkthroughs"
  - "StreamWriter class, walkthroughs"
  - "text files, reading"
  - "I/O [Visual Basic], reading text from files"
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

このチュートリアルでは、<xref:System.IO.StreamReader> クラスによるファイルのオープンと読み取り、ファイルがアクセス中かどうかのチェック、<xref:System.IO.StreamReader> クラスのインスタンスによって読み取ったファイルからの文字列の検索、<xref:System.IO.StreamWriter> クラスによるファイルへの書き込みの方法を説明します。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## アプリケーションの作成  
 [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] を起動し、ユーザーが指定のファイルに書き込みを行うためのフォームを作成して、プロジェクトを開始します。  
  
#### プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューの **\[新しいプロジェクト\]** をクリックします。  
  
2.  **新しいプロジェクト** ペインの **\[Windows アプリケーション\]** をクリックします。  
  
3.  **\[プロジェクト名\]** ボックスに「`MyDiary`」と入力し、**\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] によってプロジェクトが**ソリューション エクスプローラー**に追加され、**Windows フォーム デザイナー**が表示されます。  
  
4.  次の表に示すコントロールをフォームに追加し、対応する値をプロパティに設定します。  
  
||||  
|-|-|-|  
|**Object**|**プロパティ**|**値**|  
|<xref:System.Windows.Forms.Button>|**名前**<br /><br /> **テキスト**|`Submit`<br /><br /> Submit Entry|  
|<xref:System.Windows.Forms.Button>|**名前**<br /><br /> **テキスト**|`Clear`<br /><br /> Clear Entry|  
|<xref:System.Windows.Forms.TextBox>|**名前**<br /><br /> **テキスト**<br /><br /> **Multiline**|`エントリ`<br /><br /> Please enter something.<br /><br /> `False`|  
  
## ファイルへの書き込み  
 ファイルへの書き込み機能をアプリケーションに追加するには、<xref:System.IO.StreamWriter> クラスを使用します。  <xref:System.IO.StreamWriter> は、特定のエンコーディングによる文字出力用として設計されています。一方、<xref:System.IO.Stream> クラスは、バイトの入出力用として設計されています。  標準のテキスト ファイルにデータ行を書き込むには、<xref:System.IO.StreamWriter> を使用します。  <xref:System.IO.StreamWriter> クラスの詳細については、「<xref:System.IO.StreamWriter>」を参照してください。  
  
#### 書き込み機能を追加するには  
  
1.  **\[表示\]** メニューの **\[コード\]** をクリックして、コード エディターを開きます。  
  
2.  アプリケーションが <xref:System.IO> 名前空間を参照できるように、コードの最初、つまり `Public Class Form1` で始まるフォームのクラス宣言の前に、次のステートメントを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_1.vb)]  
  
     ファイルに書き込む前に、<xref:System.IO.StreamWriter> クラスのインスタンスを作成する必要があります。  
  
3.  **\[表示\]** メニューの **\[デザイナー\]** をクリックして、**Windows フォーム デザイナー**に戻ります。  `Submit` ボタンをダブルクリックしてボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_2.vb)]  
  
> [!NOTE]
>  コード エディターに戻り、コードを追加するイベント ハンドラーにカーソルを配置する動作は、Visual Studio 統合開発環境 \(IDE: Integrated Development Environment\) によって行われます。  
  
1.  ファイルに書き込むには、<xref:System.IO.StreamWriter> クラスの <xref:System.IO.StreamWriter.Write%2A> メソッドを使用します。  `Dim fw As StreamWriter` の直後に次のコードを追加します。  ファイルが見つからない場合に例外がスローされることはありません。まだ存在していない場合は、ファイルが作成されます。  
  
     [!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_3.vb)]  
  
2.  ユーザーが何も入力しないで \[Submit Entry\] をクリックすることがないように、`Dim ReadString As String` の直後に次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_4.vb)]  
  
3.  これは日記なので、入力のたびに日付が入るようにします。  `Today` 変数を現在の日付に設定するために、`fw = New StreamWriter("C:\MyDiary.txt", True)` の後に次のコードを挿入します。  
  
     [!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_5.vb)]  
  
4.  最後に、<xref:System.Windows.Forms.TextBox> をクリアするコードを追加します。  `Clear` ボタンの <xref:System.Windows.Forms.Control.Click> イベントに次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_6.vb)]  
  
## 日記の表示機能の追加  
 このセクションでは、`DisplayEntry` <xref:System.Windows.Forms.TextBox> に最新のエントリを表示する機能を追加します。  また、さまざまなエントリを表示する <xref:System.Windows.Forms.ComboBox> を追加し、ユーザーがそこからエントリを選択して `DisplayEntry` <xref:System.Windows.Forms.TextBox> に表示できるようにします。  <xref:System.IO.StreamReader> クラスのインスタンスでは、`MyDiary.txt` から読み込みを行います。  <xref:System.IO.StreamReader> は、<xref:System.IO.StreamWriter> クラスと同じく、テキスト ファイルに対して使用するためのものです。  
  
 ここでは、次の表に示すコントロールをフォームに追加し、対応する値をプロパティに設定します。  
  
|Control|プロパティ|Values|  
|-------------|-----------|------------|  
|<xref:System.Windows.Forms.TextBox>|**名前**<br /><br /> **Visible**<br /><br /> **サイズ**<br /><br /> **Multiline**|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|**名前**<br /><br /> **テキスト**|`表示`<br /><br /> 表示|  
|<xref:System.Windows.Forms.Button>|**名前**<br /><br /> **テキスト**|`GetEntries`<br /><br /> Get Entries|  
|<xref:System.Windows.Forms.ComboBox>|**名前**<br /><br /> **テキスト**<br /><br /> **Enabled**|`PickEntries`<br /><br /> Select an Entry<br /><br /> `False`|  
  
#### コンボ ボックスの内容を設定するには  
  
1.  `PickEntries` <xref:System.Windows.Forms.ComboBox> を使用して、ユーザーが各エントリを送信 \(Submit\) した日付を表示します。ユーザーは、そこから特定の日付のエントリを選択できます。  `GetEntries` ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_7.vb)]  
  
2.  コードをテストするには、F5 キーを押してアプリケーションをコンパイルし、**\[Get Entries\]** をクリックします。  <xref:System.Windows.Forms.ComboBox> のドロップダウン矢印をクリックして、エントリの日付を表示します。  
  
#### 個別の入力内容を選択して表示するには  
  
1.  `Display` ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_8.vb)]  
  
2.  コードをテストするには、F5 キーを押してアプリケーションをコンパイルし、エントリを送信します。  **\[Get Entries\]** をクリックし、<xref:System.Windows.Forms.ComboBox> からエントリを選択して、**\[Display\]** をクリックします。  選択したエントリの内容が `DisplayEntry` <xref:System.Windows.Forms.TextBox> に表示されます。  
  
## ユーザーがエントリを削除または変更できるようにする  
 `DeleteEntry` ボタンと `EditEntry` ボタンを使用してユーザーがエントリを削除または変更できる機能を追加できます  エントリが表示されるまでは、どちらのボタンも無効にします。  
  
 次の表に示すコントロールをフォームに追加し、対応する値をプロパティに設定します。  
  
|Control|プロパティ|Values|  
|-------------|-----------|------------|  
|<xref:System.Windows.Forms.Button>|**名前**<br /><br /> **テキスト**<br /><br /> **Enabled**|`DeleteEntry`<br /><br /> Delete Entry<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**名前**<br /><br /> **テキスト**<br /><br /> **Enabled**|`EditEntry`<br /><br /> Edit Entry<br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|**名前**<br /><br /> **テキスト**<br /><br /> **Enabled**|`SubmitEdit`<br /><br /> Submit Edit<br /><br /> `False`|  
  
#### エントリを削除または変更できるようにするには  
  
1.  `Display` ボタンの <xref:System.Windows.Forms.Control.Click> イベントにある `DisplayEntry.Text = ReadString` の後に次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_9.vb)]  
  
2.  `DeleteEntry` ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_10.vb)]  
  
3.  ユーザーが入力内容を表示すると、`EditEntry` ボタンが有効になるようにします。  `Display` ボタンの <xref:System.Windows.Forms.Control.Click> イベントにある `DisplayEntry.Text = ReadString` の後に次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_11.vb)]  
  
4.  `EditEntry` ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_12.vb)]  
  
5.  `SubmitEdit` ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_13.vb)]  
  
 コードをテストするには、F5 キーを押してアプリケーションをコンパイルします。  **\[Get Entries\]** をクリックし、エントリを選択して、**\[Display\]** をクリックします。  `DisplayEntry` <xref:System.Windows.Forms.TextBox> にエントリが表示されます。  **\[Edit Entry\]** をクリックします。  `Entry` <xref:System.Windows.Forms.TextBox> にエントリが表示されます。  `Entry` <xref:System.Windows.Forms.TextBox> の入力内容を編集し、**\[Submit Edit\]** をクリックします。  `MyDiary.txt` ファイルを開いて修正内容を確認します。  次に、エントリを選択し、**\[Delete Entry\]** をクリックします。  確認を求める <xref:System.Windows.Forms.MessageBox> が表示されたら、**\[OK\]** をクリックします。  アプリケーションを終了し、`MyDiary.txt` を開いて削除を確認します。  
  
## 参照  
 <xref:System.IO.StreamReader>   
 <xref:System.IO.StreamWriter>   
 [Walkthroughs](../../../../visual-basic/walkthroughs.md)