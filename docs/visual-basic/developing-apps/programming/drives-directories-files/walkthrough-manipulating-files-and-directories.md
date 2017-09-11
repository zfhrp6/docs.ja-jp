---
title: "Visual Basic によるファイルとディレクトリの操作"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e66d062df07fc23dfbd5d509e08ccd08813db15
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="e46de-102">チュートリアル : Visual Basic によるファイルとディレクトリの操作</span><span class="sxs-lookup"><span data-stu-id="e46de-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>
<span data-ttu-id="e46de-103">このチュートリアルでは、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] でのファイル I/O の基礎について概説します。</span><span class="sxs-lookup"><span data-stu-id="e46de-103">This walkthrough provides an introduction to the fundamentals of file I/O in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="e46de-104">具体的には、ディレクトリ内のテキスト ファイルをリストして調査する小さなアプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e46de-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="e46de-105">このアプリケーションは、選択された各テキスト ファイルについて、ファイルの属性とコンテンツの最初の行を取得します。</span><span class="sxs-lookup"><span data-stu-id="e46de-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="e46de-106">ログ ファイルに情報を書き込むオプションもあります。</span><span class="sxs-lookup"><span data-stu-id="e46de-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="e46de-107">このチュートリアルでは、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] で利用可能な、`My.Computer.FileSystem Object` のメンバーを使用します。</span><span class="sxs-lookup"><span data-stu-id="e46de-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="e46de-108">詳細については、「<xref:Microsoft.VisualBasic.FileIO.FileSystem>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e46de-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="e46de-109">チュートリアルの最後では、<xref:System.IO> 名前空間のクラスを使用する同等の例を示します。</span><span class="sxs-lookup"><span data-stu-id="e46de-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="e46de-110">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="e46de-110">To create the project</span></span>  
  
1.  <span data-ttu-id="e46de-111">**[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e46de-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="e46de-112">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e46de-112">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="e46de-113">**[インストールされたテンプレート]** ペインで、**[Visual Basic]** を展開し、**[Windows]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e46de-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="e46de-114">中央の **[テンプレート]** ペインで、**[Windows フォーム アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e46de-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="e46de-115">**[名前]** ボックスに「`FileExplorer`」と入力してプロジェクト名を設定し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e46de-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="e46de-116"> の**ソリューション エクスプローラー**にプロジェクトが追加され、Windows フォーム デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="e46de-116"> adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4.  <span data-ttu-id="e46de-117">次の表にあるコントロールをフォームに追加し、それらのプロパティに対応する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="e46de-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="e46de-118">コントロール</span><span class="sxs-lookup"><span data-stu-id="e46de-118">Control</span></span>|<span data-ttu-id="e46de-119">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e46de-119">Property</span></span>|<span data-ttu-id="e46de-120">値</span><span class="sxs-lookup"><span data-stu-id="e46de-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |<span data-ttu-id="e46de-121">**ListBox**</span><span class="sxs-lookup"><span data-stu-id="e46de-121">**ListBox**</span></span>|<span data-ttu-id="e46de-122">**名前**</span><span class="sxs-lookup"><span data-stu-id="e46de-122">**Name**</span></span>|`filesListBox`|  
    |<span data-ttu-id="e46de-123">**Button**</span><span class="sxs-lookup"><span data-stu-id="e46de-123">**Button**</span></span>|<span data-ttu-id="e46de-124">**名前**</span><span class="sxs-lookup"><span data-stu-id="e46de-124">**Name**</span></span><br /><br /> <span data-ttu-id="e46de-125">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="e46de-125">**Text**</span></span>|`browseButton`<br /><br /> <span data-ttu-id="e46de-126">**参照**</span><span class="sxs-lookup"><span data-stu-id="e46de-126">**Browse**</span></span>|  
    |<span data-ttu-id="e46de-127">**Button**</span><span class="sxs-lookup"><span data-stu-id="e46de-127">**Button**</span></span>|<span data-ttu-id="e46de-128">**名前**</span><span class="sxs-lookup"><span data-stu-id="e46de-128">**Name**</span></span><br /><br /> <span data-ttu-id="e46de-129">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="e46de-129">**Text**</span></span>|`examineButton`<br /><br /> <span data-ttu-id="e46de-130">**調査**</span><span class="sxs-lookup"><span data-stu-id="e46de-130">**Examine**</span></span>|  
    |<span data-ttu-id="e46de-131">**CheckBox**</span><span class="sxs-lookup"><span data-stu-id="e46de-131">**CheckBox**</span></span>|<span data-ttu-id="e46de-132">**名前**</span><span class="sxs-lookup"><span data-stu-id="e46de-132">**Name**</span></span><br /><br /> <span data-ttu-id="e46de-133">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="e46de-133">**Text**</span></span>|`saveCheckBox`<br /><br /> <span data-ttu-id="e46de-134">**結果の保存**</span><span class="sxs-lookup"><span data-stu-id="e46de-134">**Save Results**</span></span>|  
    |<span data-ttu-id="e46de-135">**FolderBrowserDialog**</span><span class="sxs-lookup"><span data-stu-id="e46de-135">**FolderBrowserDialog**</span></span>|<span data-ttu-id="e46de-136">**名前**</span><span class="sxs-lookup"><span data-stu-id="e46de-136">**Name**</span></span>|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="e46de-137">フォルダーを選択し、フォルダー内のファイルをリストするには</span><span class="sxs-lookup"><span data-stu-id="e46de-137">To select a folder, and list files in a folder</span></span>  
  
1.  <span data-ttu-id="e46de-138">フォーム上のコントロールをダブルクリックして、`browseButton` の `Click` イベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e46de-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="e46de-139">コード エディターが開きます。</span><span class="sxs-lookup"><span data-stu-id="e46de-139">The Code Editor opens.</span></span>  
  
2.  <span data-ttu-id="e46de-140">`Click` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e46de-140">Add the following code to the `Click` event handler.</span></span>  
  
     <span data-ttu-id="e46de-141">[!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e46de-141">[!code-vb[VbVbcnMyFileSystem#103](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_1.vb)]</span></span>  
  
     <span data-ttu-id="e46de-142">`FolderBrowserDialog1.ShowDialog` 呼び出しにより、**[フォルダーの参照]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="e46de-142">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="e46de-143">ユーザーが **[OK]** をクリックすると、次の手順で追加する `ListFiles` メソッドに <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> プロパティが引数として渡されます。</span><span class="sxs-lookup"><span data-stu-id="e46de-143">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3.  <span data-ttu-id="e46de-144">次の `ListFiles` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="e46de-144">Add the following `ListFiles` method.</span></span>  
  
     <span data-ttu-id="e46de-145">[!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e46de-145">[!code-vb[VbVbcnMyFileSystem#104](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_2.vb)]</span></span>  
  
     <span data-ttu-id="e46de-146">このコードでは、まず最初に **ListBox** をクリアします。</span><span class="sxs-lookup"><span data-stu-id="e46de-146">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="e46de-147">次に、<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> メソッドによって、ディレクトリ内の各ファイルを表す文字列のコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="e46de-147">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="e46de-148">`GetFiles` メソッドは、検索パターンの引数を受け取り、特定のパターンに一致するファイルを取得します。</span><span class="sxs-lookup"><span data-stu-id="e46de-148">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="e46de-149">この例では、拡張子 .txt が付いているファイルのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="e46de-149">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="e46de-150">その後、`GetFiles` メソッドによって返された文字列が、**ListBox** に追加されます。</span><span class="sxs-lookup"><span data-stu-id="e46de-150">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4.  <span data-ttu-id="e46de-151">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="e46de-151">Run the application.</span></span> <span data-ttu-id="e46de-152">**[参照]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e46de-152">Click the **Browse** button.</span></span> <span data-ttu-id="e46de-153">**[フォルダーの参照]** ダイアログ ボックスで、.txt ファイルが含まれているフォルダーを参照し、そのフォルダーを選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e46de-153">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="e46de-154">`ListBox` に、選択したフォルダー内のファイルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="e46de-154">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5.  <span data-ttu-id="e46de-155">アプリケーションの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="e46de-155">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="e46de-156">テキスト ファイルからファイルの属性とコンテンツを取得するには</span><span class="sxs-lookup"><span data-stu-id="e46de-156">To obtain attributes of a file, and content from a text file</span></span>  
  
1.  <span data-ttu-id="e46de-157">フォーム上のコントロールをダブルクリックして、`examineButton` の `Click` イベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e46de-157">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2.  <span data-ttu-id="e46de-158">`Click` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e46de-158">Add the following code to the `Click` event handler.</span></span>  
  
     <span data-ttu-id="e46de-159">[!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="e46de-159">[!code-vb[VbVbcnMyFileSystem#105](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_3.vb)]</span></span>  
  
     <span data-ttu-id="e46de-160">このコードは、`ListBox` で選択された項目を検証します。</span><span class="sxs-lookup"><span data-stu-id="e46de-160">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="e46de-161">その後、`ListBox` からファイル パスのエントリを取得します。</span><span class="sxs-lookup"><span data-stu-id="e46de-161">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="e46de-162"><xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> メソッドを使用して、ファイルがまだ存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="e46de-162">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="e46de-163">ファイル パスは引数として `GetTextForOutput` メソッドに送られます (このメソッドは次の手順で追加します)。</span><span class="sxs-lookup"><span data-stu-id="e46de-163">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="e46de-164">このメソッドは、ファイル情報を含んだ文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="e46de-164">This method returns a string that contains file information.</span></span> <span data-ttu-id="e46de-165">ファイル情報は、**MessageBox** に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e46de-165">The file information appears in a **MessageBox**.</span></span>  
  
3.  <span data-ttu-id="e46de-166">次の `GetTextForOutput` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="e46de-166">Add the following `GetTextForOutput` method.</span></span>  
  
     <span data-ttu-id="e46de-167">[!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="e46de-167">[!code-vb[VbVbcnMyFileSystem#107](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_4.vb)]</span></span>  
  
     <span data-ttu-id="e46de-168">このコードでは、<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> メソッドを使用してファイル パラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="e46de-168">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="e46de-169">ファイル パラメーターは、<xref:System.Text.StringBuilder> に追加されます。</span><span class="sxs-lookup"><span data-stu-id="e46de-169">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="e46de-170"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> メソッドは、ファイルの内容を <xref:System.IO.StreamReader> に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e46de-170">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="e46de-171">コンテンツの最初の行が `StreamReader` から取得され、`StringBuilder` に追加されます。</span><span class="sxs-lookup"><span data-stu-id="e46de-171">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4.  <span data-ttu-id="e46de-172">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="e46de-172">Run the application.</span></span> <span data-ttu-id="e46de-173">**[参照]** をクリックし、.txt ファイルが含まれているフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="e46de-173">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="e46de-174">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e46de-174">Click **OK**.</span></span>  
  
     <span data-ttu-id="e46de-175">`ListBox` でファイルを選択し、**[調査]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e46de-175">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="e46de-176">`MessageBox` にファイル情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e46de-176">A `MessageBox` shows the file information.</span></span>  
  
5.  <span data-ttu-id="e46de-177">アプリケーションの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="e46de-177">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="e46de-178">ログ エントリを追加するには</span><span class="sxs-lookup"><span data-stu-id="e46de-178">To add a log entry</span></span>  
  
1.  <span data-ttu-id="e46de-179">`examineButton_Click` イベント ハンドラーの末尾に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e46de-179">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     <span data-ttu-id="e46de-180">[!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="e46de-180">[!code-vb[VbVbcnMyFileSystem#106](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_5.vb)]</span></span>  
  
     <span data-ttu-id="e46de-181">このコードは、ログ ファイルのパスを設定して、選択したファイルと同じディレクトリにログ ファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="e46de-181">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="e46de-182">ログ エントリのテキストは現在の日付と時刻に設定され、その後にファイル情報が記録されます。</span><span class="sxs-lookup"><span data-stu-id="e46de-182">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="e46de-183">`append` 引数を `True` に設定した <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> メソッドを使用して、ログ エントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="e46de-183">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2.  <span data-ttu-id="e46de-184">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="e46de-184">Run the application.</span></span> <span data-ttu-id="e46de-185">テキスト ファイルを参照し、`ListBox` でファイルを選択して、**[結果の保存]** チェック ボックスをオンにした後、**[調査]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e46de-185">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="e46de-186">ログ エントリが `log.txt` ファイルに書き込まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e46de-186">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3.  <span data-ttu-id="e46de-187">アプリケーションの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="e46de-187">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="e46de-188">現在のディレクトリを使用するには</span><span class="sxs-lookup"><span data-stu-id="e46de-188">To use the current directory</span></span>  
  
1.  <span data-ttu-id="e46de-189">フォームをダブルクリックして、`Form1_Load` のイベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e46de-189">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2.  <span data-ttu-id="e46de-190">イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e46de-190">Add the following code to the event handler.</span></span>  
  
     <span data-ttu-id="e46de-191">[!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="e46de-191">[!code-vb[VbVbcnMyFileSystem#102](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_6.vb)]</span></span>  
  
     <span data-ttu-id="e46de-192">このコードは、フォルダー ブラウザーの既定のディレクトリを現在のディレクトリに設定します。</span><span class="sxs-lookup"><span data-stu-id="e46de-192">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3.  <span data-ttu-id="e46de-193">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="e46de-193">Run the application.</span></span> <span data-ttu-id="e46de-194">**[参照]** を最初にクリックすると、**[フォルダーの参照]** ダイアログ ボックスが開き、現在のディレクトリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e46de-194">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4.  <span data-ttu-id="e46de-195">アプリケーションの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="e46de-195">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="e46de-196">コントロールを選択的に有効化するには</span><span class="sxs-lookup"><span data-stu-id="e46de-196">To selectively enable controls</span></span>  
  
1.  <span data-ttu-id="e46de-197">次の `SetEnabled` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="e46de-197">Add the following `SetEnabled` method.</span></span>  
  
     <span data-ttu-id="e46de-198">[!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="e46de-198">[!code-vb[VbVbcnMyFileSystem#108](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_7.vb)]</span></span>  
  
     <span data-ttu-id="e46de-199">`SetEnabled` メソッドは、`ListBox` で項目が選択されているかどうかに応じて、コントロールを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="e46de-199">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2.  <span data-ttu-id="e46de-200">フォーム上の `ListBox` コントロールをダブルクリックして、`filesListBox` の `SelectedIndexChanged` イベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e46de-200">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3.  <span data-ttu-id="e46de-201">新しい `filesListBox_SelectedIndexChanged` イベント ハンドラーで、`SetEnabled` に対する呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="e46de-201">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4.  <span data-ttu-id="e46de-202">`browseButton_Click` イベント ハンドラーの末尾に、`SetEnabled` に対する呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="e46de-202">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5.  <span data-ttu-id="e46de-203">`Form1_Load` イベント ハンドラーの末尾に、`SetEnabled` に対する呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="e46de-203">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6.  <span data-ttu-id="e46de-204">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="e46de-204">Run the application.</span></span> <span data-ttu-id="e46de-205">`ListBox` で項目が選択されていない場合は、**[結果の保存**] チェック ボックスと **[調査]** ボタンが無効になります。</span><span class="sxs-lookup"><span data-stu-id="e46de-205">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="e46de-206">My.Computer.FileSystem を使用した完全な例</span><span class="sxs-lookup"><span data-stu-id="e46de-206">Full example using My.Computer.FileSystem</span></span>  
 <span data-ttu-id="e46de-207">完全な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e46de-207">Following is the complete example.</span></span>  
  
 <span data-ttu-id="e46de-208">[!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="e46de-208">[!code-vb[VbVbcnMyFileSystem#101](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_8.vb)]</span></span>  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="e46de-209">System.IO を使用した完全な例</span><span class="sxs-lookup"><span data-stu-id="e46de-209">Full example using System.IO</span></span>  
 <span data-ttu-id="e46de-210">次に示す同等の例では、`My.Computer.FileSystem` オブジェクトではなく、<xref:System.IO> 名前空間のクラスを使用しています。</span><span class="sxs-lookup"><span data-stu-id="e46de-210">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 <span data-ttu-id="e46de-211">[!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="e46de-211">[!code-vb[VbVbcnMyFileSystem#111](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-and-directories_9.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e46de-212">関連項目</span><span class="sxs-lookup"><span data-stu-id="e46de-212">See Also</span></span>  
 <span data-ttu-id="e46de-213"><xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="e46de-213"><xref:System.IO></span></span>   
 <span data-ttu-id="e46de-214"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="e46de-214"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="e46de-215"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A></span><span class="sxs-lookup"><span data-stu-id="e46de-215"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A></span></span>   
 [<span data-ttu-id="e46de-216">チュートリアル : .NET Framework のメソッドによるファイル操作</span><span class="sxs-lookup"><span data-stu-id="e46de-216">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)

