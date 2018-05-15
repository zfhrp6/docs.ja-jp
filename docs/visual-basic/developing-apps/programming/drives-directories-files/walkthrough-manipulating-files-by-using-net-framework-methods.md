---
title: .NET Framework のメソッドによるファイル操作 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- I/O [Visual Basic], walkthroughs
- text files [Visual Basic], writing to
- reading text files [Visual Basic]
- text, writing to files
- files [Visual Basic], searching
- StreamReader class, walkthroughs
- files [Visual Basic], accessing
- I/O [Visual Basic], writing text to files
- writing to files [Visual Basic], walkthroughs
- StreamWriter class, walkthroughs
- text files [Visual Basic], reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ed363efeeef008927f2c34b393de66ca4ccbb0bb
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="49163-102">チュートリアル: .NET Framework のメソッドによるファイル操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49163-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>
<span data-ttu-id="49163-103">このチュートリアルでは、<xref:System.IO.StreamReader> クラスを使用してファイルを開いて読み取り、ファイルがアクセスされているかどうかをチェックし、<xref:System.IO.StreamReader> クラスのインスタンスを使用したファイル読み取り内の文字列を検索し、<xref:System.IO.StreamWriter> クラスを使用してファイルにデータを書き込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="49163-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-application"></a><span data-ttu-id="49163-104">アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="49163-104">Creating the Application</span></span>  
 <span data-ttu-id="49163-105">Visual Studio を起動し、ユーザーが指定のファイルへの書き込みに使用できるフォームを作成して、プロジェクトを開始します。</span><span class="sxs-lookup"><span data-stu-id="49163-105">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="49163-106">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="49163-106">To create the project</span></span>  
  
1.  <span data-ttu-id="49163-107">**[ファイル]** メニューの **[新しいプロジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="49163-107">On the **File** menu, select **New Project**.</span></span>  
  
2.  <span data-ttu-id="49163-108">**[新しいプロジェクト]** ペインで、**[Windows アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49163-108">In the **New Project** pane, click **Windows Application**.</span></span>  
  
3.  <span data-ttu-id="49163-109">**[名前]** ボックスに `MyDiary` と入力して、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49163-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>  
  
     <span data-ttu-id="49163-110">Visual Studio の**ソリューション エクスプローラー**にプロジェクトが追加され、**Windows フォーム デザイナー**が開きます。</span><span class="sxs-lookup"><span data-stu-id="49163-110">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>  
  
4.  <span data-ttu-id="49163-111">次の表にあるコントロールをフォームに追加し、それらのプロパティに対応する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="49163-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="49163-112">**オブジェクト**</span><span class="sxs-lookup"><span data-stu-id="49163-112">**Object**</span></span>|<span data-ttu-id="49163-113">**プロパティ**</span><span class="sxs-lookup"><span data-stu-id="49163-113">**Properties**</span></span>|<span data-ttu-id="49163-114">**[値]**</span><span class="sxs-lookup"><span data-stu-id="49163-114">**Value**</span></span>|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="49163-115">**Name**</span><span class="sxs-lookup"><span data-stu-id="49163-115">**Name**</span></span><br /><br /> <span data-ttu-id="49163-116">**[テキスト]**</span><span class="sxs-lookup"><span data-stu-id="49163-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="49163-117">**エントリの送信**</span><span class="sxs-lookup"><span data-stu-id="49163-117">**Submit Entry**</span></span>|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="49163-118">**Name**</span><span class="sxs-lookup"><span data-stu-id="49163-118">**Name**</span></span><br /><br /> <span data-ttu-id="49163-119">**[テキスト]**</span><span class="sxs-lookup"><span data-stu-id="49163-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="49163-120">**エントリのクリア**</span><span class="sxs-lookup"><span data-stu-id="49163-120">**Clear Entry**</span></span>|  
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="49163-121">**Name**</span><span class="sxs-lookup"><span data-stu-id="49163-121">**Name**</span></span><br /><br /> <span data-ttu-id="49163-122">**[テキスト]**</span><span class="sxs-lookup"><span data-stu-id="49163-122">**Text**</span></span><br /><br /> <span data-ttu-id="49163-123">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="49163-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="49163-124">**テキストを入力してください。**</span><span class="sxs-lookup"><span data-stu-id="49163-124">**Please enter something.**</span></span><br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a><span data-ttu-id="49163-125">ファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="49163-125">Writing to the File</span></span>  
 <span data-ttu-id="49163-126">アプリケーションを通じてファイルに書き込む機能を追加するには、<xref:System.IO.StreamWriter> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="49163-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="49163-127"><xref:System.IO.StreamWriter> は、特定のエンコードでの文字出力用に設計されています。これに対し <xref:System.IO.Stream> クラスは、バイト入出力用に設計されています。</span><span class="sxs-lookup"><span data-stu-id="49163-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="49163-128">標準のテキスト ファイルに複数行の情報を書き込む場合には、<xref:System.IO.StreamWriter> を使用します。</span><span class="sxs-lookup"><span data-stu-id="49163-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="49163-129"><xref:System.IO.StreamWriter> クラスの詳細については、「<xref:System.IO.StreamWriter>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="49163-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>  
  
#### <a name="to-add-writing-functionality"></a><span data-ttu-id="49163-130">書き込み機能を追加するには</span><span class="sxs-lookup"><span data-stu-id="49163-130">To add writing functionality</span></span>  
  
1.  <span data-ttu-id="49163-131">**[表示]** メニューの **[コード]** を選択してコード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="49163-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="49163-132">アプリケーションで <xref:System.IO> 名前空間を参照するので、コードの先頭、つまりフォームのクラス宣言 (`Public Class Form1` で始まるブロック) よりも前に、次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="49163-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_1.vb)]  
  
     <span data-ttu-id="49163-133">ファイルへの書き込みを行う前に、<xref:System.IO.StreamWriter> クラスのインスタンスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49163-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>  
  
3.  <span data-ttu-id="49163-134">**[表示]** メニューの **[デザイナー]** を選択して、**Windows フォーム デザイナー**に戻ります。</span><span class="sxs-lookup"><span data-stu-id="49163-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="49163-135">`Submit` ボタンをダブルクリックして、ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="49163-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_2.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="49163-136">Visual Studio 統合開発環境 (IDE) の画面がコード エディターに戻り、コードを追加するイベント ハンドラー内にカーソルが配置されます。</span><span class="sxs-lookup"><span data-stu-id="49163-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>  
  
1.  <span data-ttu-id="49163-137">ファイルへの書き込みを行うには、<xref:System.IO.StreamWriter> クラスの <xref:System.IO.StreamWriter.Write%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="49163-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="49163-138">`Dim fw As StreamWriter` の直後に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="49163-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="49163-139">ファイルが見つからない場合に例外がスローされることを心配する必要はありません。ファイルまだ存在しない場合は、新規に作成されます。</span><span class="sxs-lookup"><span data-stu-id="49163-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_3.vb)]  
  
2.  <span data-ttu-id="49163-140">ユーザーが空のエントリを送信しないよう、`Dim ReadString As String` の直後に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="49163-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_4.vb)]  
  
3.  <span data-ttu-id="49163-141">これは日記なので、ユーザーが各エントリに日付を割り当てられようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="49163-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="49163-142">`fw = New StreamWriter("C:\MyDiary.txt", True)` の後に次のコードを挿入して、変数 `Today` を現在の日付に設定します。</span><span class="sxs-lookup"><span data-stu-id="49163-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_5.vb)]  
  
4.  <span data-ttu-id="49163-143">最後に、<xref:System.Windows.Forms.TextBox> をクリアするためのコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="49163-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="49163-144">`Clear` ボタンの <xref:System.Windows.Forms.Control.Click> イベントに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="49163-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_6.vb)]  
  
## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="49163-145">日記に表示機能を追加する</span><span class="sxs-lookup"><span data-stu-id="49163-145">Adding Display Features to the Diary</span></span>  
 <span data-ttu-id="49163-146">このセクションでは、`DisplayEntry`<xref:System.Windows.Forms.TextBox> に最新のエントリを表示する機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="49163-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="49163-147"><xref:System.Windows.Forms.ComboBox> を追加することも可能で、これでさまざまなエントリを表示したり、`DisplayEntry`<xref:System.Windows.Forms.TextBox> に表示するエントリをユーザーが選択できるようにしたりできます。</span><span class="sxs-lookup"><span data-stu-id="49163-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="49163-148"><xref:System.IO.StreamReader> クラスのインスタンスは、`MyDiary.txt` からデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="49163-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="49163-149"><xref:System.IO.StreamWriter> クラスと同様、<xref:System.IO.StreamReader> はテキスト ファイル用です。</span><span class="sxs-lookup"><span data-stu-id="49163-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>  
  
 <span data-ttu-id="49163-150">チュートリアルのこのセクション用に、次の表にあるコントロールをフォームに追加し、それらのプロパティに対応する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="49163-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="49163-151">コントロール</span><span class="sxs-lookup"><span data-stu-id="49163-151">Control</span></span>|<span data-ttu-id="49163-152">プロパティ</span><span class="sxs-lookup"><span data-stu-id="49163-152">Properties</span></span>|<span data-ttu-id="49163-153">値</span><span class="sxs-lookup"><span data-stu-id="49163-153">Values</span></span>|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="49163-154">**Name**</span><span class="sxs-lookup"><span data-stu-id="49163-154">**Name**</span></span><br /><br /> <span data-ttu-id="49163-155">**Visible**</span><span class="sxs-lookup"><span data-stu-id="49163-155">**Visible**</span></span><br /><br /> <span data-ttu-id="49163-156">**Size**</span><span class="sxs-lookup"><span data-stu-id="49163-156">**Size**</span></span><br /><br /> <span data-ttu-id="49163-157">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="49163-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="49163-158">**Name**</span><span class="sxs-lookup"><span data-stu-id="49163-158">**Name**</span></span><br /><br /> <span data-ttu-id="49163-159">**[テキスト]**</span><span class="sxs-lookup"><span data-stu-id="49163-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="49163-160">**表示**</span><span class="sxs-lookup"><span data-stu-id="49163-160">**Display**</span></span>|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="49163-161">**Name**</span><span class="sxs-lookup"><span data-stu-id="49163-161">**Name**</span></span><br /><br /> <span data-ttu-id="49163-162">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="49163-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="49163-163">**エントリの取得**</span><span class="sxs-lookup"><span data-stu-id="49163-163">**Get Entries**</span></span>|  
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="49163-164">**Name**</span><span class="sxs-lookup"><span data-stu-id="49163-164">**Name**</span></span><br /><br /> <span data-ttu-id="49163-165">**[テキスト]**</span><span class="sxs-lookup"><span data-stu-id="49163-165">**Text**</span></span><br /><br /> <span data-ttu-id="49163-166">**有効**</span><span class="sxs-lookup"><span data-stu-id="49163-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="49163-167">**エントリの選択**</span><span class="sxs-lookup"><span data-stu-id="49163-167">**Select an Entry**</span></span><br /><br /> `False`|  
  
#### <a name="to-populate-the-combo-box"></a><span data-ttu-id="49163-168">コンボ ボックスを設定するには</span><span class="sxs-lookup"><span data-stu-id="49163-168">To populate the combo box</span></span>  
  
1.  <span data-ttu-id="49163-169">`PickEntries`<xref:System.Windows.Forms.ComboBox> は、ユーザーが各エントリを送信する日付を表示するために使用されます。これにより、ユーザーが特定の日付からエントリを選択できるようになります。</span><span class="sxs-lookup"><span data-stu-id="49163-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="49163-170">`GetEntries` ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="49163-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_7.vb)]  
  
2.  <span data-ttu-id="49163-171">コードをテストするには、F5 キーを押してアプリケーションをコンパイルし、**[エントリの取得]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49163-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="49163-172"><xref:System.Windows.Forms.ComboBox> でドロップダウンの矢印をクリックして、エントリの日付を表示します。</span><span class="sxs-lookup"><span data-stu-id="49163-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>  
  
#### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="49163-173">個別のエントリを選択して表示するには</span><span class="sxs-lookup"><span data-stu-id="49163-173">To choose and display individual entries</span></span>  
  
1.  <span data-ttu-id="49163-174">`Display` ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="49163-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_8.vb)]  
  
2.  <span data-ttu-id="49163-175">コードをテストするには、F5 キーを押してアプリケーションをコンパイルし、エントリを送信します。</span><span class="sxs-lookup"><span data-stu-id="49163-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="49163-176">**[Get Entries] (エントリの取得)** をクリックし、<xref:System.Windows.Forms.ComboBox> からエントリを選択して、**[表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49163-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="49163-177">選択したエントリのコンテンツが、`DisplayEntry`<xref:System.Windows.Forms.TextBox> に表示されます。</span><span class="sxs-lookup"><span data-stu-id="49163-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="49163-178">ユーザーがエントリの削除や変更を行えるようにする</span><span class="sxs-lookup"><span data-stu-id="49163-178">Enabling Users to Delete or Modify Entries</span></span>  
 <span data-ttu-id="49163-179">ユーザーが `DeleteEntry` ボタンと `EditEntry` ボタンを使用してエントリを削除したり変更したりできる機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="49163-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="49163-180">どちらのボタンも、エントリが表示されているとき以外は無効になります。</span><span class="sxs-lookup"><span data-stu-id="49163-180">Both buttons remain disabled unless an entry is displayed.</span></span>  
  
 <span data-ttu-id="49163-181">次の表にあるコントロールをフォームに追加し、それらのプロパティに対応する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="49163-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="49163-182">コントロール</span><span class="sxs-lookup"><span data-stu-id="49163-182">Control</span></span>|<span data-ttu-id="49163-183">プロパティ</span><span class="sxs-lookup"><span data-stu-id="49163-183">Properties</span></span>|<span data-ttu-id="49163-184">値</span><span class="sxs-lookup"><span data-stu-id="49163-184">Values</span></span>|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="49163-185">**Name**</span><span class="sxs-lookup"><span data-stu-id="49163-185">**Name**</span></span><br /><br /> <span data-ttu-id="49163-186">**[テキスト]**</span><span class="sxs-lookup"><span data-stu-id="49163-186">**Text**</span></span><br /><br /> <span data-ttu-id="49163-187">**有効**</span><span class="sxs-lookup"><span data-stu-id="49163-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="49163-188">**エントリの削除**</span><span class="sxs-lookup"><span data-stu-id="49163-188">**Delete Entry**</span></span><br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="49163-189">**Name**</span><span class="sxs-lookup"><span data-stu-id="49163-189">**Name**</span></span><br /><br /> <span data-ttu-id="49163-190">**[テキスト]**</span><span class="sxs-lookup"><span data-stu-id="49163-190">**Text**</span></span><br /><br /> <span data-ttu-id="49163-191">**有効**</span><span class="sxs-lookup"><span data-stu-id="49163-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="49163-192">**エントリの編集**</span><span class="sxs-lookup"><span data-stu-id="49163-192">**Edit Entry**</span></span><br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="49163-193">**Name**</span><span class="sxs-lookup"><span data-stu-id="49163-193">**Name**</span></span><br /><br /> <span data-ttu-id="49163-194">**[テキスト]**</span><span class="sxs-lookup"><span data-stu-id="49163-194">**Text**</span></span><br /><br /> <span data-ttu-id="49163-195">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="49163-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="49163-196">**編集結果の送信**</span><span class="sxs-lookup"><span data-stu-id="49163-196">**Submit Edit**</span></span><br /><br /> `False`|  
  
#### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="49163-197">エントリの削除と変更を有効にするには</span><span class="sxs-lookup"><span data-stu-id="49163-197">To enable deletion and modification of entries</span></span>  
  
1.  <span data-ttu-id="49163-198">`Display` ボタンの <xref:System.Windows.Forms.Control.Click> イベント (`DisplayEntry.Text = ReadString` の後) に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="49163-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_9.vb)]  
  
2.  <span data-ttu-id="49163-199">`DeleteEntry` ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="49163-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_10.vb)]  
  
3.  <span data-ttu-id="49163-200">ユーザーがエントリを表示すると、`EditEntry` ボタンが有効になります。</span><span class="sxs-lookup"><span data-stu-id="49163-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="49163-201">`Display` ボタンの <xref:System.Windows.Forms.Control.Click> イベント (`DisplayEntry.Text = ReadString` の後) に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="49163-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_11.vb)]  
  
4.  <span data-ttu-id="49163-202">`EditEntry` ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="49163-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_12.vb)]  
  
5.  <span data-ttu-id="49163-203">`SubmitEdit` ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを作成し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="49163-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_13.vb)]  
  
 <span data-ttu-id="49163-204">コードをテストするには、F5 キーを押してアプリケーションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="49163-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="49163-205">**[エントリの取得]** をクリックし、エントリを選択して、**[表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49163-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="49163-206">`DisplayEntry`<xref:System.Windows.Forms.TextBox> にエントリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="49163-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="49163-207">**[エントリの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49163-207">Click **Edit Entry**.</span></span> <span data-ttu-id="49163-208">`Entry`<xref:System.Windows.Forms.TextBox> にエントリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="49163-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="49163-209">`Entry`<xref:System.Windows.Forms.TextBox> でエントリを編集し、**[Submit Edit] (編集結果の送信)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49163-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="49163-210">`MyDiary.txt` ファイルを開いて修正結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="49163-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="49163-211">確認したら、エントリを選択し、**[エントリの削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49163-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="49163-212"><xref:System.Windows.Forms.MessageBox> で確認を求められたら、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49163-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="49163-213">アプリケーションを閉じ、`MyDiary.txt` を開いて削除を確認します。</span><span class="sxs-lookup"><span data-stu-id="49163-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49163-214">参照</span><span class="sxs-lookup"><span data-stu-id="49163-214">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="49163-215">チュートリアル</span><span class="sxs-lookup"><span data-stu-id="49163-215">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)
