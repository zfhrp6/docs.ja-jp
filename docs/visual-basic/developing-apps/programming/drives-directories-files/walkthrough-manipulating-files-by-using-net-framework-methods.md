---
title: ".NET Framework のメソッドによるファイル操作 (Visual Basic)"
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
- I/O [Visual Basic], walkthroughs
- text files, writing to
- reading text files
- text, writing to files
- files, searching
- StreamReader class, walkthroughs
- files, accessing
- I/O [Visual Basic], writing text to files
- writing to files, walkthroughs
- StreamWriter class, walkthroughs
- text files, reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
caps.latest.revision: 18
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
ms.openlocfilehash: eab8ebe0f1e6f3e86b9c4aa7c3b24a2763a27ffc
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="d7e66-102">チュートリアル: .NET Framework のメソッドによるファイル操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7e66-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>
<span data-ttu-id="d7e66-103">このチュートリアルでは、<xref:System.IO.StreamReader> クラスを使用してファイルを開いて読み取り、ファイルがアクセスされているかどうかをチェックし、<xref:System.IO.StreamReader> クラスのインスタンスを使用したファイル読み取り内の文字列を検索し、<xref:System.IO.StreamWriter> クラスを使用してファイルにデータを書き込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-application"></a><span data-ttu-id="d7e66-104">アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="d7e66-104">Creating the Application</span></span>  
 <span data-ttu-id="d7e66-105">[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] を起動し、ユーザーが指定のファイルへの書き込みに使用できるフォームを作成して、プロジェクトを開始します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-105">Start [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] and begin the project by creating a form that the user can use to write to the designated file.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="d7e66-106">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="d7e66-106">To create the project</span></span>  
  
1.  <span data-ttu-id="d7e66-107">**[ファイル]** メニューの **[新しいプロジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-107">On the **File** menu, select **New Project**.</span></span>  
  
2.  <span data-ttu-id="d7e66-108">**[新しいプロジェクト]** ペインで、**[Windows アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e66-108">In the **New Project** pane, click **Windows Application**.</span></span>  
  
3.  <span data-ttu-id="d7e66-109">**[名前]** ボックスに `MyDiary` と入力して、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e66-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>  
  
     [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="d7e66-110"> の**ソリューション エクスプローラー**にプロジェクトが追加され、**Windows フォーム デザイナー**が開きます。</span><span class="sxs-lookup"><span data-stu-id="d7e66-110"> adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>  
  
4.  <span data-ttu-id="d7e66-111">次の表にあるコントロールをフォームに追加し、それらのプロパティに対応する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="d7e66-112">**オブジェクト**</span><span class="sxs-lookup"><span data-stu-id="d7e66-112">**Object**</span></span>|<span data-ttu-id="d7e66-113">**プロパティ**</span><span class="sxs-lookup"><span data-stu-id="d7e66-113">**Properties**</span></span>|<span data-ttu-id="d7e66-114">**値**</span><span class="sxs-lookup"><span data-stu-id="d7e66-114">**Value**</span></span>|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="d7e66-115">**Name**</span><span class="sxs-lookup"><span data-stu-id="d7e66-115">**Name**</span></span><br /><br /> <span data-ttu-id="d7e66-116">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="d7e66-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="d7e66-117">**エントリの送信**</span><span class="sxs-lookup"><span data-stu-id="d7e66-117">**Submit Entry**</span></span>|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="d7e66-118">**Name**</span><span class="sxs-lookup"><span data-stu-id="d7e66-118">**Name**</span></span><br /><br /> <span data-ttu-id="d7e66-119">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="d7e66-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="d7e66-120">**エントリのクリア**</span><span class="sxs-lookup"><span data-stu-id="d7e66-120">**Clear Entry**</span></span>|  
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="d7e66-121">**Name**</span><span class="sxs-lookup"><span data-stu-id="d7e66-121">**Name**</span></span><br /><br /> <span data-ttu-id="d7e66-122">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="d7e66-122">**Text**</span></span><br /><br /> <span data-ttu-id="d7e66-123">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="d7e66-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="d7e66-124">**テキストを入力してください。**</span><span class="sxs-lookup"><span data-stu-id="d7e66-124">**Please enter something.**</span></span><br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a><span data-ttu-id="d7e66-125">ファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="d7e66-125">Writing to the File</span></span>  
 <span data-ttu-id="d7e66-126">アプリケーションを通じてファイルに書き込む機能を追加するには、<xref:System.IO.StreamWriter> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="d7e66-127"><xref:System.IO.StreamWriter> は、特定のエンコードでの文字出力用に設計されています。これに対し <xref:System.IO.Stream> クラスは、バイト入出力用に設計されています。</span><span class="sxs-lookup"><span data-stu-id="d7e66-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="d7e66-128">標準のテキスト ファイルに複数行の情報を書き込む場合には、<xref:System.IO.StreamWriter> を使用します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="d7e66-129"><xref:System.IO.StreamWriter> クラスの詳細については、「<xref:System.IO.StreamWriter>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d7e66-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>  
  
#### <a name="to-add-writing-functionality"></a><span data-ttu-id="d7e66-130">書き込み機能を追加するには</span><span class="sxs-lookup"><span data-stu-id="d7e66-130">To add writing functionality</span></span>  
  
1.  <span data-ttu-id="d7e66-131">**[表示]** メニューの **[コード]** を選択してコード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="d7e66-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="d7e66-132">アプリケーションで <xref:System.IO> 名前空間を参照するので、コードの先頭、つまりフォームのクラス宣言 (`Public Class Form1` で始まるブロック) よりも前に、次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>  
  
     <span data-ttu-id="d7e66-133">[!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7e66-133">[!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_1.vb)]</span></span>  
  
     <span data-ttu-id="d7e66-134">ファイルへの書き込みを行う前に、<xref:System.IO.StreamWriter> クラスのインスタンスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7e66-134">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>  
  
3.  <span data-ttu-id="d7e66-135">**[表示]** メニューの **[デザイナー]** を選択して、**Windows フォーム デザイナー**に戻ります。</span><span class="sxs-lookup"><span data-stu-id="d7e66-135">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="d7e66-136">`Submit` ボタンをダブルクリックして、ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-136">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>  
  
     <span data-ttu-id="d7e66-137">[!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7e66-137">[!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_2.vb)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7e66-138">Visual Studio 統合開発環境 (IDE) の画面がコード エディターに戻り、コードを追加するイベント ハンドラー内にカーソルが配置されます。</span><span class="sxs-lookup"><span data-stu-id="d7e66-138">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>  
  
1.  <span data-ttu-id="d7e66-139">ファイルへの書き込みを行うには、<xref:System.IO.StreamWriter> クラスの <xref:System.IO.StreamWriter.Write%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-139">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="d7e66-140">`Dim fw As StreamWriter` の直後に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-140">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="d7e66-141">ファイルが見つからない場合に例外がスローされることを心配する必要はありません。ファイルまだ存在しない場合は、新規に作成されます。</span><span class="sxs-lookup"><span data-stu-id="d7e66-141">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>  
  
     <span data-ttu-id="d7e66-142">[!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7e66-142">[!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_3.vb)]</span></span>  
  
2.  <span data-ttu-id="d7e66-143">ユーザーが空のエントリを送信しないよう、`Dim ReadString As String` の直後に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-143">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>  
  
     <span data-ttu-id="d7e66-144">[!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7e66-144">[!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_4.vb)]</span></span>  
  
3.  <span data-ttu-id="d7e66-145">これは日記なので、ユーザーが各エントリに日付を割り当てられようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7e66-145">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="d7e66-146">`fw = New StreamWriter("C:\MyDiary.txt", True)` の後に次のコードを挿入して、変数 `Today` を現在の日付に設定します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-146">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>  
  
     <span data-ttu-id="d7e66-147">[!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7e66-147">[!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_5.vb)]</span></span>  
  
4.  <span data-ttu-id="d7e66-148">最後に、<xref:System.Windows.Forms.TextBox> をクリアするためのコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-148">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="d7e66-149">`Clear` ボタンの <xref:System.Windows.Forms.Control.Click> イベントに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-149">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
     <span data-ttu-id="d7e66-150">[!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7e66-150">[!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_6.vb)]</span></span>  
  
## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="d7e66-151">日記に表示機能を追加する</span><span class="sxs-lookup"><span data-stu-id="d7e66-151">Adding Display Features to the Diary</span></span>  
 <span data-ttu-id="d7e66-152">このセクションでは、`DisplayEntry`<xref:System.Windows.Forms.TextBox> に最新のエントリを表示する機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-152">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="d7e66-153"><xref:System.Windows.Forms.ComboBox> を追加することも可能で、これでさまざまなエントリを表示したり、`DisplayEntry`<xref:System.Windows.Forms.TextBox> に表示するエントリをユーザーが選択できるようにしたりできます。</span><span class="sxs-lookup"><span data-stu-id="d7e66-153">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="d7e66-154"><xref:System.IO.StreamReader> クラスのインスタンスは、`MyDiary.txt` からデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="d7e66-154">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="d7e66-155"><xref:System.IO.StreamWriter> クラスと同様、<xref:System.IO.StreamReader> はテキスト ファイル用です。</span><span class="sxs-lookup"><span data-stu-id="d7e66-155">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>  
  
 <span data-ttu-id="d7e66-156">チュートリアルのこのセクション用に、次の表にあるコントロールをフォームに追加し、それらのプロパティに対応する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-156">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="d7e66-157">コントロール</span><span class="sxs-lookup"><span data-stu-id="d7e66-157">Control</span></span>|<span data-ttu-id="d7e66-158">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d7e66-158">Properties</span></span>|<span data-ttu-id="d7e66-159">値</span><span class="sxs-lookup"><span data-stu-id="d7e66-159">Values</span></span>|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="d7e66-160">**Name**</span><span class="sxs-lookup"><span data-stu-id="d7e66-160">**Name**</span></span><br /><br /> <span data-ttu-id="d7e66-161">**Visible**</span><span class="sxs-lookup"><span data-stu-id="d7e66-161">**Visible**</span></span><br /><br /> <span data-ttu-id="d7e66-162">**Size**</span><span class="sxs-lookup"><span data-stu-id="d7e66-162">**Size**</span></span><br /><br /> <span data-ttu-id="d7e66-163">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="d7e66-163">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="d7e66-164">**Name**</span><span class="sxs-lookup"><span data-stu-id="d7e66-164">**Name**</span></span><br /><br /> <span data-ttu-id="d7e66-165">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="d7e66-165">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="d7e66-166">**表示**</span><span class="sxs-lookup"><span data-stu-id="d7e66-166">**Display**</span></span>|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="d7e66-167">**Name**</span><span class="sxs-lookup"><span data-stu-id="d7e66-167">**Name**</span></span><br /><br /> <span data-ttu-id="d7e66-168">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="d7e66-168">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="d7e66-169">**エントリの取得**</span><span class="sxs-lookup"><span data-stu-id="d7e66-169">**Get Entries**</span></span>|  
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="d7e66-170">**Name**</span><span class="sxs-lookup"><span data-stu-id="d7e66-170">**Name**</span></span><br /><br /> <span data-ttu-id="d7e66-171">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="d7e66-171">**Text**</span></span><br /><br /> <span data-ttu-id="d7e66-172">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="d7e66-172">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="d7e66-173">**エントリの選択**</span><span class="sxs-lookup"><span data-stu-id="d7e66-173">**Select an Entry**</span></span><br /><br /> `False`|  
  
#### <a name="to-populate-the-combo-box"></a><span data-ttu-id="d7e66-174">コンボ ボックスを設定するには</span><span class="sxs-lookup"><span data-stu-id="d7e66-174">To populate the combo box</span></span>  
  
1.  <span data-ttu-id="d7e66-175">`PickEntries`<xref:System.Windows.Forms.ComboBox> は、ユーザーが各エントリを送信する日付を表示するために使用されます。これにより、ユーザーが特定の日付からエントリを選択できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d7e66-175">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="d7e66-176">`GetEntries` ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-176">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>  
  
     <span data-ttu-id="d7e66-177">[!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7e66-177">[!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_7.vb)]</span></span>  
  
2.  <span data-ttu-id="d7e66-178">コードをテストするには、F5 キーを押してアプリケーションをコンパイルし、**[エントリの取得]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e66-178">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="d7e66-179"><xref:System.Windows.Forms.ComboBox> でドロップダウンの矢印をクリックして、エントリの日付を表示します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-179">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>  
  
#### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="d7e66-180">個別のエントリを選択して表示するには</span><span class="sxs-lookup"><span data-stu-id="d7e66-180">To choose and display individual entries</span></span>  
  
1.  <span data-ttu-id="d7e66-181">`Display` ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-181">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>  
  
     <span data-ttu-id="d7e66-182">[!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7e66-182">[!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_8.vb)]</span></span>  
  
2.  <span data-ttu-id="d7e66-183">コードをテストするには、F5 キーを押してアプリケーションをコンパイルし、エントリを送信します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-183">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="d7e66-184">**[Get Entries] (エントリの取得)** をクリックし、<xref:System.Windows.Forms.ComboBox> からエントリを選択して、**[表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e66-184">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="d7e66-185">選択したエントリのコンテンツが、`DisplayEntry`<xref:System.Windows.Forms.TextBox> に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7e66-185">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="d7e66-186">ユーザーがエントリの削除や変更を行えるようにする</span><span class="sxs-lookup"><span data-stu-id="d7e66-186">Enabling Users to Delete or Modify Entries</span></span>  
 <span data-ttu-id="d7e66-187">ユーザーが `DeleteEntry` ボタンと `EditEntry` ボタンを使用してエントリを削除したり変更したりできる機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="d7e66-187">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="d7e66-188">どちらのボタンも、エントリが表示されているとき以外は無効になります。</span><span class="sxs-lookup"><span data-stu-id="d7e66-188">Both buttons remain disabled unless an entry is displayed.</span></span>  
  
 <span data-ttu-id="d7e66-189">次の表にあるコントロールをフォームに追加し、それらのプロパティに対応する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-189">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="d7e66-190">コントロール</span><span class="sxs-lookup"><span data-stu-id="d7e66-190">Control</span></span>|<span data-ttu-id="d7e66-191">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d7e66-191">Properties</span></span>|<span data-ttu-id="d7e66-192">値</span><span class="sxs-lookup"><span data-stu-id="d7e66-192">Values</span></span>|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="d7e66-193">**Name**</span><span class="sxs-lookup"><span data-stu-id="d7e66-193">**Name**</span></span><br /><br /> <span data-ttu-id="d7e66-194">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="d7e66-194">**Text**</span></span><br /><br /> <span data-ttu-id="d7e66-195">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="d7e66-195">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="d7e66-196">**エントリの削除**</span><span class="sxs-lookup"><span data-stu-id="d7e66-196">**Delete Entry**</span></span><br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="d7e66-197">**Name**</span><span class="sxs-lookup"><span data-stu-id="d7e66-197">**Name**</span></span><br /><br /> <span data-ttu-id="d7e66-198">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="d7e66-198">**Text**</span></span><br /><br /> <span data-ttu-id="d7e66-199">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="d7e66-199">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="d7e66-200">**エントリの編集**</span><span class="sxs-lookup"><span data-stu-id="d7e66-200">**Edit Entry**</span></span><br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="d7e66-201">**Name**</span><span class="sxs-lookup"><span data-stu-id="d7e66-201">**Name**</span></span><br /><br /> <span data-ttu-id="d7e66-202">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="d7e66-202">**Text**</span></span><br /><br /> <span data-ttu-id="d7e66-203">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="d7e66-203">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="d7e66-204">**編集結果の送信**</span><span class="sxs-lookup"><span data-stu-id="d7e66-204">**Submit Edit**</span></span><br /><br /> `False`|  
  
#### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="d7e66-205">エントリの削除と変更を有効にするには</span><span class="sxs-lookup"><span data-stu-id="d7e66-205">To enable deletion and modification of entries</span></span>  
  
1.  <span data-ttu-id="d7e66-206">`Display` ボタンの <xref:System.Windows.Forms.Control.Click> イベント (`DisplayEntry.Text = ReadString` の後) に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-206">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>  
  
     <span data-ttu-id="d7e66-207">[!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7e66-207">[!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_9.vb)]</span></span>  
  
2.  <span data-ttu-id="d7e66-208">`DeleteEntry` ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-208">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>  
  
     <span data-ttu-id="d7e66-209">[!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7e66-209">[!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_10.vb)]</span></span>  
  
3.  <span data-ttu-id="d7e66-210">ユーザーがエントリを表示すると、`EditEntry` ボタンが有効になります。</span><span class="sxs-lookup"><span data-stu-id="d7e66-210">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="d7e66-211">`Display` ボタンの <xref:System.Windows.Forms.Control.Click> イベント (`DisplayEntry.Text = ReadString` の後) に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-211">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>  
  
     <span data-ttu-id="d7e66-212">[!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7e66-212">[!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_11.vb)]</span></span>  
  
4.  <span data-ttu-id="d7e66-213">`EditEntry` ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-213">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>  
  
     <span data-ttu-id="d7e66-214">[!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7e66-214">[!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_12.vb)]</span></span>  
  
5.  <span data-ttu-id="d7e66-215">`SubmitEdit` ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-215">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>  
  
     <span data-ttu-id="d7e66-216">[!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_13.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7e66-216">[!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_13.vb)]</span></span>  
  
 <span data-ttu-id="d7e66-217">コードをテストするには、F5 キーを押してアプリケーションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="d7e66-217">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="d7e66-218">**[エントリの取得]** をクリックし、エントリを選択して、**[表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e66-218">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="d7e66-219">`DisplayEntry`<xref:System.Windows.Forms.TextBox> にエントリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7e66-219">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="d7e66-220">**[エントリの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e66-220">Click **Edit Entry**.</span></span> <span data-ttu-id="d7e66-221">`Entry`<xref:System.Windows.Forms.TextBox> にエントリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d7e66-221">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="d7e66-222">`Entry`<xref:System.Windows.Forms.TextBox> でエントリを編集し、**[Submit Edit] (編集結果の送信)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e66-222">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="d7e66-223">`MyDiary.txt` ファイルを開いて修正結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-223">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="d7e66-224">確認したら、エントリを選択し、**[エントリの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e66-224">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="d7e66-225"><xref:System.Windows.Forms.MessageBox> で確認を求められたら、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d7e66-225">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="d7e66-226">アプリケーションを閉じ、`MyDiary.txt` を開いて削除を確認します。</span><span class="sxs-lookup"><span data-stu-id="d7e66-226">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7e66-227">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7e66-227">See Also</span></span>  
 <span data-ttu-id="d7e66-228"><xref:System.IO.StreamReader></span><span class="sxs-lookup"><span data-stu-id="d7e66-228"><xref:System.IO.StreamReader></span></span>   
 <span data-ttu-id="d7e66-229"><xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="d7e66-229"><xref:System.IO.StreamWriter></span></span>   
 [<span data-ttu-id="d7e66-230">チュートリアル</span><span class="sxs-lookup"><span data-stu-id="d7e66-230">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)

