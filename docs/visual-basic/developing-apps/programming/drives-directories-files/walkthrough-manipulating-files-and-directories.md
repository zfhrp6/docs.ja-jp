---
title: "Walkthrough: Manipulating Files and Directories in Visual Basic | Microsoft Docs"
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
  - "files, reading text"
  - "reading files, text"
  - "I/O [Visual Basic], walkthroughs"
  - "text, writing to files"
  - "text, reading from files"
  - "reading text from files, walkthroughs"
  - "Visual Basic code, file access"
  - "files, writing text"
  - "I/O [Visual Basic], writing text to files"
  - "file access, walkthroughs"
  - "writing to files, walkthroughs"
  - "I/O [Visual Basic], reading text from files"
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
caps.latest.revision: 49
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 49
---
# Walkthrough: Manipulating Files and Directories in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このチュートリアルでは、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] によるファイル I\/O の基本事項について紹介します。  ここでは、ディレクトリ内のテキスト ファイルを一覧表示し、ファイルの内容をチェックする小さなアプリケーションを作成する方法について説明します。  このアプリケーションでは、選択した各テキスト ファイルのファイル属性と内容の 1 行目を表示します。  また、情報をログ ファイルに書き込むオプションもあります。  
  
 このチュートリアルでは、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で提供される `My.Computer.FileSystem Object` のメンバーを使用します。  詳細については、「<xref:Microsoft.VisualBasic.FileIO.FileSystem>」を参照してください。  このチュートリアルの最後に、<xref:System.IO> 名前空間のクラスを使用した場合の同等のコード例を示します。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューの **\[新しいプロジェクト\]** をクリックします。  
  
     **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
2.  **\[インストールされたテンプレート\]** ペインで、**\[Visual Basic\]** を展開し、**\[Windows\]** をクリックします。  中央の **\[テンプレート\]** ペインで、**\[Windows フォーム アプリケーション\]** をクリックします。  
  
3.  **\[名前\]** ボックスに「`FileExplorer`」と入力してプロジェクト名を設定し、**\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs-md.md)] によってプロジェクトが**ソリューション エクスプローラー**に追加され、Windows フォーム デザイナーが表示されます。  
  
4.  次の表に示すコントロールをフォームに追加し、プロパティの値を設定します。  
  
    |Control|プロパティ|値|  
    |-------------|-----------|-------|  
    |**ListBox**|**名前**|`filesListBox`|  
    |**ボタン**|**名前**<br /><br /> **テキスト**|`browseButton`<br /><br /> 参照|  
    |**ボタン**|**名前**<br /><br /> **テキスト**|`examineButton`<br /><br /> Examine|  
    |**CheckBox**|**名前**<br /><br /> **テキスト**|`saveCheckBox`<br /><br /> Save Results|  
    |**FolderBrowserDialog**|**名前**|`FolderBrowserDialog1`|  
  
### フォルダーを選択し、フォルダー内のファイルを一覧表示するには  
  
1.  フォーム上のコントロールをダブルクリックして、`browseButton` の `Click` イベント ハンドラーを作成します。  コード エディターが開きます。  
  
2.  `Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_0_1.vb)]  
  
     `FolderBrowserDialog1.ShowDialog` の呼び出しによって、**\[フォルダーの参照\]** ダイアログ ボックスが開きます。  ユーザーが **\[OK\]** をクリックすると、次の手順で追加する `ListFiles` メソッドに <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> プロパティが引数として渡されます。  
  
3.  次の `ListFiles` メソッドを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_0_2.vb)]  
  
     このコードでは、まず **ListBox** をクリアします。  
  
     次に、<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> メソッドによって、ディレクトリ内の各ファイルを表す文字列のコレクションを取得します。  `GetFiles` メソッドは、検索パターン引数を受け入れ、特定のパターンと一致するファイルを取得します。  この例では、拡張子が .txt のファイルだけが返されます。  
  
     `GetFiles` メソッドから返された文字列が **ListBox** に追加されます。  
  
4.  アプリケーションを実行します。  **\[Browse\]** をクリックします。  **\[フォルダーの参照\]** ダイアログ ボックスで、.txt ファイルが格納されたフォルダーを参照し、そのフォルダーを選択して **\[OK\]** をクリックします。  
  
     `ListBox` には、選択したフォルダー内の .txt ファイルの一覧が含まれています。  
  
5.  アプリケーションの実行を停止します。  
  
### ファイルの属性とテキスト ファイルの内容を取得するには  
  
1.  フォーム上のコントロールをダブルクリックして、`examineButton` の `Click` イベント ハンドラーを作成します。  
  
2.  `Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_0_3.vb)]  
  
     このコードでは、`ListBox` 内の項目が選択されていることを確認します。  次に、`ListBox` からファイル パス エントリを取得します。  <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> メソッドを使用して、ファイルがまだ存在するかどうかを確認します。  
  
     このファイル パスは、次の手順で追加する `GetTextForOutput` メソッドに引数として渡されます。  このメソッドは、ファイル情報を含む文字列を返します。  ファイル情報は、**MessageBox** に表示されます。  
  
3.  次の `GetTextForOutput` メソッドを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_0_4.vb)]  
  
     このコードでは、<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> メソッドを使用してファイル パラメーターを取得します。  ファイル パラメーターは、<xref:System.Text.StringBuilder> に追加されます。  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> メソッドは、ファイルの内容を <xref:System.IO.StreamReader> に読み込みます。  `StreamReader` からファイルの内容の 1 行目が取得され、`StringBuilder` に追加されます。  
  
4.  アプリケーションを実行します。  **\[Browse\]** をクリックし、.txt ファイルが格納されたフォルダーを参照します。  **\[OK\]** をクリックします。  
  
     `ListBox` でファイルを選択し、**\[Examine\]** をクリックします。  `MessageBox` にファイル情報が表示されます。  
  
5.  アプリケーションの実行を停止します。  
  
### ログ エントリを追加するには  
  
1.  `examineButton_Click` イベント ハンドラーの末尾に、次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_0_5.vb)]  
  
     このコードでは、選択したファイルと同じディレクトリにログ ファイルを配置するようにログ ファイルのパスを設定します。  ログ エントリのテキストが現在の日付と時刻に設定され、その後にファイル情報が示されます。  
  
     `append` 引数を `True` に設定した <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> メソッドを使用して、ログ エントリを作成します。  
  
2.  アプリケーションを実行します。  テキスト ファイルを参照し、`ListBox` でファイルを選択します。**\[Save Results\]** チェック ボックスをオンにし、**\[Examine\]** をクリックします。  `log.txt` ファイルにログ エントリが書き込まれていることを確認します。  
  
3.  アプリケーションの実行を停止します。  
  
### 現在のディレクトリを使用するには  
  
1.  `Form1_Load` をダブルクリックして、このフォームのイベント ハンドラーを作成します。  
  
2.  イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_0_6.vb)]  
  
     このコードでは、フォルダー参照の既定のディレクトリを現在のディレクトリに設定します。  
  
3.  アプリケーションを実行します。  **\[Browse\]** をクリックすると、**\[フォルダーの参照\]** ダイアログ ボックスが開き、現在のディレクトリが表示されます。  
  
4.  アプリケーションの実行を停止します。  
  
### コントロールを選択的に有効にするには  
  
1.  次の `SetEnabled` メソッドを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_0_7.vb)]  
  
     `SetEnabled` メソッドは、`ListBox` で項目が選択されているかどうかに応じて、コントロールを有効または無効にします。  
  
2.  フォーム上の `ListBox` コントロールをダブルクリックして、`filesListBox` の `SelectedIndexChanged` イベント ハンドラーを作成します。  
  
3.  この新しい `filesListBox_SelectedIndexChanged` イベント ハンドラーに、`SetEnabled` の呼び出しを追加します。  
  
4.  `browseButton_Click` イベント ハンドラーの末尾に、`SetEnabled` の呼び出しを追加します。  
  
5.  `Form1_Load` イベント ハンドラーの末尾に、`SetEnabled` の呼び出しを追加します。  
  
6.  アプリケーションを実行します。  `ListBox` で項目が選択されていない場合、**\[Save Results\]** チェック ボックスと **\[Examine\]** ボタンが無効になります。  
  
## My.Computer.FileSystem を使用した完全なコード例  
 完成なコード例を次に示します。  
  
 [!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_0_8.vb)]  
  
## System.IO を使用した完全なコード例  
 `My.Computer.FileSystem` オブジェクトを使用する代わりに、<xref:System.IO> 名前空間のクラスを使用した場合の同等のコード例を次に示します。  
  
 [!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/walkthrough-manipulating_0_9.vb)]  
  
## 参照  
 <xref:System.IO>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>   
 [Walkthrough: Manipulating Files by Using .NET Framework Methods](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)