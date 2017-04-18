---
title: "Visual Basic によるファイルとディレクトリの操作 | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- files, reading text
- reading files, text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files, walkthroughs
- Visual Basic code, file access
- files, writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files, walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
caps.latest.revision: 49
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 89137b3c927a7ac8ed126f2be3695c4aa72a85fb
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a>チュートリアル : Visual Basic によるファイルとディレクトリの操作
このチュートリアルでは、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] でのファイル I/O の基礎について概説します。 具体的には、ディレクトリ内のテキスト ファイルをリストして調査する小さなアプリケーションを作成する方法について説明します。 このアプリケーションは、選択された各テキスト ファイルについて、ファイルの属性とコンテンツの最初の行を取得します。 ログ ファイルに情報を書き込むオプションもあります。  
  
 このチュートリアルでは、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] で利用可能な、`My.Computer.FileSystem Object` のメンバーを使用します。 詳しくは、「<xref:Microsoft.VisualBasic.FileIO.FileSystem>」をご覧ください。 チュートリアルの最後では、<xref:System.IO> 名前空間のクラスを使用する同等の例を示します。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
1.  **[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  **[インストールされたテンプレート]** ペインで、**[Visual Basic]** を展開し、**[Windows]** をクリックします。 中央の **[テンプレート]** ペインで、**[Windows フォーム アプリケーション]** をクリックします。  
  
3.  **[名前]** ボックスに「`FileExplorer`」と入力してプロジェクト名を設定し、**[OK]** をクリックします。  
  
     [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] の**ソリューション エクスプローラー**にプロジェクトが追加され、Windows フォーム デザイナーが開きます。  
  
4.  次の表にあるコントロールをフォームに追加し、それらのプロパティに対応する値を設定します。  
  
    |コントロール|プロパティ|値|  
    |-------------|--------------|-----------|  
    |**ListBox**|**名前**|`filesListBox`|  
    |**Button**|**名前**<br /><br /> **テキスト**|`browseButton`<br /><br /> **参照**|  
    |**Button**|**名前**<br /><br /> **テキスト**|`examineButton`<br /><br /> **調査**|  
    |**CheckBox**|**名前**<br /><br /> **テキスト**|`saveCheckBox`<br /><br /> **結果の保存**|  
    |**FolderBrowserDialog**|**名前**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a>フォルダーを選択し、フォルダー内のファイルをリストするには  
  
1.  フォーム上のコントロールをダブルクリックして、`browseButton` の `Click` イベント ハンドラーを作成します。 コード エディターが開きます。  
  
2.  `Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]  
  
     `FolderBrowserDialog1.ShowDialog` 呼び出しにより、**[フォルダーの参照]** ダイアログ ボックスが開きます。 ユーザーが **[OK]** をクリックすると、<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> プロパティが引数として `ListFiles` メソッドに送られます (このメソッドは次の手順で追加します)。  
  
3.  次の `ListFiles` メソッドを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]  
  
     このコードでは、まず最初に **ListBox** をクリアします。  
  
     その後、<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> メソッドが、ディレクトリ内のファイルごとに 1 つずつ、文字列のコレクションを取得します。 `GetFiles` メソッドは、検索パターンの引数を受け取り、特定のパターンに一致するファイルを取得します。 この例では、拡張子 .txt が付いているファイルのみが返されます。  
  
     その後、`GetFiles` メソッドによって返された文字列が、**ListBox** に追加されます。  
  
4.  アプリケーションを実行します。 **[参照]** ボタンをクリックします。 **[フォルダーの参照]** ダイアログ ボックスで、.txt ファイルが含まれているフォルダーを参照し、そのフォルダーを選択して **[OK]** をクリックします。  
  
     `ListBox` に、選択したフォルダー内のファイルが追加されます。  
  
5.  アプリケーションの実行を停止します。  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a>テキスト ファイルからファイルの属性とコンテンツを取得するには  
  
1.  フォーム上のコントロールをダブルクリックして、`examineButton` の `Click` イベント ハンドラーを作成します。  
  
2.  `Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]  
  
     このコードは、`ListBox` で選択された項目を検証します。 その後、`ListBox` からファイル パスのエントリを取得します。 <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> メソッドは、ファイルが現在も存在するかどうかをチェックするために使用されます。  
  
     ファイル パスは引数として `GetTextForOutput` メソッドに送られます (このメソッドは次の手順で追加します)。 このメソッドは、ファイル情報を含んだ文字列を返します。 ファイル情報は、**MessageBox** に表示されます。  
  
3.  次の `GetTextForOutput` メソッドを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]  
  
     このコードは、<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> メソッドを使用してファイルのパラメーターを取得します。 ファイル パラメーターは、<xref:System.Text.StringBuilder> に追加されます。  
  
     <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> メソッドは、ファイルのコンテンツを <xref:System.IO.StreamReader> 内に読み込みます。 コンテンツの最初の行が `StreamReader` から取得され、`StringBuilder` に追加されます。  
  
4.  アプリケーションを実行します。 **[参照]** をクリックし、.txt ファイルが含まれているフォルダーを参照します。 **[OK]** をクリックします。  
  
     `ListBox` でファイルを選択し、**[調査]** をクリックします。 `MessageBox` にファイル情報が表示されます。  
  
5.  アプリケーションの実行を停止します。  
  
### <a name="to-add-a-log-entry"></a>ログ エントリを追加するには  
  
1.  `examineButton_Click` イベント ハンドラーの末尾に、次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]  
  
     このコードは、ログ ファイルのパスを設定して、選択したファイルと同じディレクトリにログ ファイルを配置します。 ログ エントリのテキストは現在の日付と時刻に設定され、その後にファイル情報が記録されます。  
  
     `append` 引数が `True` に設定された <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> メソッドは、ログ エントリを作成するために使用されます。  
  
2.  アプリケーションを実行します。 テキスト ファイルを参照し、`ListBox` でファイルを選択して、**[結果の保存]** チェック ボックスをオンにした後、**[調査]** をクリックします。 ログ エントリが `log.txt` ファイルに書き込まれていることを確認します。  
  
3.  アプリケーションの実行を停止します。  
  
### <a name="to-use-the-current-directory"></a>現在のディレクトリを使用するには  
  
1.  フォームをダブルクリックして、`Form1_Load` のイベント ハンドラーを作成します。  
  
2.  イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]  
  
     このコードは、フォルダー ブラウザーの既定のディレクトリを現在のディレクトリに設定します。  
  
3.  アプリケーションを実行します。 **[参照]** を最初にクリックすると、**[フォルダーの参照]** ダイアログ ボックスが開き、現在のディレクトリが表示されます。  
  
4.  アプリケーションの実行を停止します。  
  
### <a name="to-selectively-enable-controls"></a>コントロールを選択的に有効化するには  
  
1.  次の `SetEnabled` メソッドを追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]  
  
     `SetEnabled` メソッドは、`ListBox` で項目が選択されているかどうかに応じて、コントロールを有効または無効にします。  
  
2.  フォーム上の `ListBox` コントロールをダブルクリックして、`filesListBox` の `SelectedIndexChanged` イベント ハンドラーを作成します。  
  
3.  新しい `filesListBox_SelectedIndexChanged` イベント ハンドラーで、`SetEnabled` に対する呼び出しを追加します。  
  
4.  `browseButton_Click` イベント ハンドラーの末尾に、`SetEnabled` に対する呼び出しを追加します。  
  
5.  `Form1_Load` イベント ハンドラーの末尾に、`SetEnabled` に対する呼び出しを追加します。  
  
6.  アプリケーションを実行します。 `ListBox` で項目が選択されていない場合は、**[結果の保存**] チェック ボックスと **[調査]** ボタンが無効になります。  
  
## <a name="full-example-using-mycomputerfilesystem"></a>My.Computer.FileSystem を使用した完全な例  
 完全な例を次に示します。  
  
 [!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]  
  
## <a name="full-example-using-systemio"></a>System.IO を使用した完全な例  
 次に示す同等の例では、`My.Computer.FileSystem` オブジェクトではなく、<xref:System.IO> 名前空間のクラスを使用しています。  
  
 [!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>   
 [チュートリアル : .NET Framework のメソッドによるファイル操作](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)

