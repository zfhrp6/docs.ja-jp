---
title: "Async で Web にアクセスして、Await (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 643fff648336c664961ad7956308acbaea262f61
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="b9f98-102">チュートリアル: Async と Await を使用した Web へのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9f98-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="b9f98-103">プログラムを作成できます非同期より簡単かつ直感的にで導入された機能を使用して[!INCLUDE[vs_dev11_long](../../../../csharp/includes/vs_dev11_long_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-103">You can write asynchronous programs more easily and intuitively by using features that were introduced in [!INCLUDE[vs_dev11_long](../../../../csharp/includes/vs_dev11_long_md.md)].</span></span> <span data-ttu-id="b9f98-104">同期コードに似た非同期コードを記述し、通常の非同期コードが必要とする難しいコールバック関数や継続の処理をコンパイラに任せます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="b9f98-105">非同期機能の詳細については、次を参照してください。 [Async と Await (Visual Basic) を使用した非同期プログラミング](../../../../visual-basic/programming-guide/concepts/async/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="b9f98-106">このチュートリアルは、Web サイトの一覧でのバイト数の合計を計算する同期 Windows Presentation Foundation (WPF) アプリケーションから開始します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="b9f98-107">その後、新しい機能を使用して、アプリケーションを非同期ソリューションに変換します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="b9f98-108">アプリケーションをビルドしたくない場合は、ダウンロード"Async サンプル: Web のチュートリアル (c# および Visual Basic) にアクセスする"から[デベロッパー サンプル コード集](http://go.microsoft.com/fwlink/?LinkId=255191)します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
  
 <span data-ttu-id="b9f98-109">このチュートリアルでは、次のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="b9f98-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="b9f98-110">WPF アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="b9f98-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="b9f98-111">単純な WPF MainWindow をデザインします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="b9f98-112">参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="b9f98-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="b9f98-113">必要な Imports ステートメントを追加するには</span><span class="sxs-lookup"><span data-stu-id="b9f98-113">To add necessary Imports statements</span></span>](#ImportsState)  
  
-   [<span data-ttu-id="b9f98-114">同期アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="b9f98-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="b9f98-115">同期ソリューションをテストするには</span><span class="sxs-lookup"><span data-stu-id="b9f98-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="b9f98-116">GetURLContents を非同期メソッドに変換するには</span><span class="sxs-lookup"><span data-stu-id="b9f98-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="b9f98-117">SumPageSizes を非同期メソッドに変換するには</span><span class="sxs-lookup"><span data-stu-id="b9f98-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="b9f98-118">StartButton_Click を非同期メソッドに変換するには</span><span class="sxs-lookup"><span data-stu-id="b9f98-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="b9f98-119">非同期のソリューションをテストするには</span><span class="sxs-lookup"><span data-stu-id="b9f98-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="b9f98-120">GetURLContentsAsync メソッドを .NET Framework メソッドに置き換えます</span><span class="sxs-lookup"><span data-stu-id="b9f98-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="b9f98-121">使用例</span><span class="sxs-lookup"><span data-stu-id="b9f98-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="b9f98-122">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b9f98-122">Prerequisites</span></span>  
 <span data-ttu-id="b9f98-123">Visual Studio 2012 またはそれ以降は、お使いのコンピューターにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9f98-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="b9f98-124">詳細については、次を参照してください。、 [Microsoft web サイト](http://go.microsoft.com/fwlink/?LinkId=235233)します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-124">For more information, see the [Microsoft website](http://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
###  <span data-ttu-id="b9f98-125"><a name="CreateWPFApp"></a>WPF アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="b9f98-125"><a name="CreateWPFApp"></a> To create a WPF application</span></span>  
  
1.  <span data-ttu-id="b9f98-126">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-126">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="b9f98-127">メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="b9f98-128">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-128">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="b9f98-129">**インストールされたテンプレート**] ウィンドウでは、Visual Basic を選択し、[ **WPF アプリケーション**プロジェクトの種類の一覧からです。</span><span class="sxs-lookup"><span data-stu-id="b9f98-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="b9f98-130">**名**テキスト ボックスに、入力`AsyncExampleWPF`を選択し、 **OK**  ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="b9f98-131">新しいプロジェクトに表示されます**ソリューション エクスプ ローラー**します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-131">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <span data-ttu-id="b9f98-132"><a name="MainWindow"></a>単純な WPF MainWindow をデザインします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-132"><a name="MainWindow"></a> To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="b9f98-133">Visual Studio コード エディターで、 **[MainWindow.xaml]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="b9f98-134">場合、**ツールボックス**ウィンドウが表示されている、開かれている、**ビュー** ] メニューの [クリックして**ツールボックス**します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="b9f98-135">追加、**ボタン**コントロールと** テキスト ボックス**に制御を**MainWindow**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="b9f98-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="b9f98-136">強調表示、 ** テキスト ボックス**コントロールと、**プロパティ**ウィンドウでは、次の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="b9f98-137">設定、**名**プロパティを`resultsTextBox`します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="b9f98-138">設定、**高さ**250 プロパティです。</span><span class="sxs-lookup"><span data-stu-id="b9f98-138">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="b9f98-139">設定、**幅**500 プロパティです。</span><span class="sxs-lookup"><span data-stu-id="b9f98-139">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="b9f98-140">**テキスト**タブで、グローバル Monospace Lucida コンソールなどの等幅フォントを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="b9f98-141">強調表示、**ボタン**コントロールと、**プロパティ**ウィンドウでは、次の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="b9f98-142">設定、**名**プロパティを`startButton`します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-142">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="b9f98-143">値を変更、**コンテンツ**プロパティから**ボタン**に**開始**します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="b9f98-144">両方ともに表示されるように、テキスト ボックスとボタンを位置、 **MainWindow**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="b9f98-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="b9f98-145">WPF XAML デザイナーの詳細については、次を参照してください。 [XAML デザイナーを使用して UI を作成する](https://docs.microsoft.com/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio)です。</span><span class="sxs-lookup"><span data-stu-id="b9f98-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](https://docs.microsoft.com/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <span data-ttu-id="b9f98-146"><a name="AddRef"></a>参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="b9f98-146"><a name="AddRef"></a> To add a reference</span></span>  
  
1.  <span data-ttu-id="b9f98-147">**ソリューション エクスプ ローラー**プロジェクトの名前を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="b9f98-148">メニュー バー**プロジェクト**、**参照の追加**します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="b9f98-149">**参照マネージャー**  ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-149">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="b9f98-150">ダイアログ ボックスの上部にあるプロジェクトが .NET Framework 4.5 以降を対象としていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="b9f98-151">**アセンブリ**領域で、選択**Framework**が選択されていない場合。</span><span class="sxs-lookup"><span data-stu-id="b9f98-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="b9f98-152">名前の一覧で、選択、 **System.Net.Http**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="b9f98-153">選択、 **OK**  ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-153">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <span data-ttu-id="b9f98-154"><a name="ImportsState"></a>必要な Imports ステートメントを追加するには</span><span class="sxs-lookup"><span data-stu-id="b9f98-154"><a name="ImportsState"></a> To add necessary Imports statements</span></span>  
  
1.  <span data-ttu-id="b9f98-155">**ソリューション エクスプ ローラー**MainWindow.xaml.vb のショートカット メニューを開き、クリックして**コードの表示**します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="b9f98-156">次の追加`Imports`存在していない場合は、コード ファイルの上部にあるステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b9f98-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <span data-ttu-id="b9f98-157"><a name="synchronous"></a>同期アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="b9f98-157"><a name="synchronous"></a> To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="b9f98-158">デザイン ウィンドウで、MainWindow.xaml をダブルクリック、**開始**を作成するボタン、 `startButton_Click` MainWindow.xaml.vb 内のイベント ハンドラーです。</span><span class="sxs-lookup"><span data-stu-id="b9f98-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="b9f98-159">MainWindow.xaml.vb の本文に次のコードをコピー `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="b9f98-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     <span data-ttu-id="b9f98-160">このコードは、`SumPageSizes` アプリケーションを実行するメソッドを呼び出し、`startButton_Click` に制御が戻るとメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="b9f98-161">同期ソリューションのコードには、次の&4; つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9f98-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="b9f98-162">`SumPageSizes` は、`SetUpURLList` から Web ページ URL のリストを取得し、`GetURLContents` と `DisplayResults` を呼び出して各 URL を処理します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="b9f98-163">`SetUpURLList` は、Web アドレスのリストを作成して返します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="b9f98-164">`GetURLContents` は、各 Web サイトのコンテンツをダウンロードし、バイト配列としてそのコンテンツを返します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="b9f98-165">`DisplayResults` は、各 URL のバイト配列内のバイト数を表示します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="b9f98-166">次の&4; つのメソッドをコピーして貼り付けて下に、 `startButton_Click` MainWindow.xaml.vb 内のイベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="b9f98-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>  
  
    ```vb  
    Private Sub SumPageSizes()  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetURLContents returns the contents of url as a byte array.  
            Dim urlContents As Byte() = GetURLContents(url)  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)  
    End Sub  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Function GetURLContents(url As String) As Byte()  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        Using response As WebResponse = webReq.GetResponse()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <span data-ttu-id="b9f98-167"><a name="testSynch"></a>同期ソリューションをテストするには</span><span class="sxs-lookup"><span data-stu-id="b9f98-167"><a name="testSynch"></a> To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="b9f98-168">F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="b9f98-169">次の一覧のような出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-169">Output that resembles the following list should appear.</span></span>  
  
    ```  
  
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832  
    msdn.microsoft.com                                            33964  
    msdn.microsoft.com/library/hh290136.aspx               225793  
    msdn.microsoft.com/library/ee256749.aspx               143577  
    msdn.microsoft.com/library/hh290138.aspx               237372  
    msdn.microsoft.com/library/hh290140.aspx               128279  
    msdn.microsoft.com/library/dd470362.aspx               157649  
    msdn.microsoft.com/library/aa578028.aspx               204457  
    msdn.microsoft.com/library/ms404677.aspx               176405  
    msdn.microsoft.com/library/ff730837.aspx               143474  
  
    Total bytes returned:  1834802  
  
    Control returned to startButton_Click.  
  
    ```  
  
     <span data-ttu-id="b9f98-170">カウントの表示には数秒かかる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="b9f98-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="b9f98-171">その間、要求されたリソースのダウンロードが完了するまで UI スレッドがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="b9f98-172">その結果、移動できない場合を最大化、最小化、またはを選択した後、表示 ウィンドウを閉じることも、**開始** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="b9f98-173">バイト カウントの表示が開始するまでは、これらの操作を実行しても失敗します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="b9f98-174">Web サイトが応答していない場合、どのサイトに問題があるのかを示す情報は表示されません。</span><span class="sxs-lookup"><span data-stu-id="b9f98-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="b9f98-175">待つのをやめて、プログラムを閉じることさえ難しい状態になります。</span><span class="sxs-lookup"><span data-stu-id="b9f98-175">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <span data-ttu-id="b9f98-176"><a name="GetURLContents"></a>GetURLContents を非同期メソッドに変換するには</span><span class="sxs-lookup"><span data-stu-id="b9f98-176"><a name="GetURLContents"></a> To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="b9f98-177">開始する最適な場所が、同期ソリューションを非同期のソリューションに変換する`GetURLContents`ためへの呼び出し、<xref:System.Net.HttpWebRequest>メソッド<xref:System.Net.HttpWebRequest.GetResponse%2A>にされ、<xref:System.IO.Stream>メソッド<xref:System.IO.Stream.CopyTo%2A>アプリケーションが web にアクセスするには</xref:System.IO.Stream.CopyTo%2A></xref:System.IO.Stream></xref:System.Net.HttpWebRequest.GetResponse%2A></xref:System.Net.HttpWebRequest>。</span><span class="sxs-lookup"><span data-stu-id="b9f98-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="b9f98-178">.NET Framework には両方のメソッドの非同期バージョンが用意されているため、変換は簡単です。</span><span class="sxs-lookup"><span data-stu-id="b9f98-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="b9f98-179">使用される方法の詳細については`GetURLContents`、 <xref:System.Net.WebRequest>.</xref:System.Net.WebRequest>を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9f98-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b9f98-180">このチュートリアルの手順に従っていると、いくつかのコンパイラ エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="b9f98-181">これらのエラーは無視することで、チュートリアルを続行できます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="b9f98-182">3 行目に呼び出されるメソッドを変更する`GetURLContents`から`GetResponse`、非同期タスク ベース<xref:System.Net.WebRequest.GetResponseAsync%2A>メソッド</xref:System.Net.WebRequest.GetResponseAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="b9f98-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  <span data-ttu-id="b9f98-183">`GetResponseAsync`<xref:System.Threading.Tasks.Task%601>。</xref:System.Threading.Tasks.Task%601>を返します</span><span class="sxs-lookup"><span data-stu-id="b9f98-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="b9f98-184">ここで、*タスク戻り変数*、 `TResult`、型を持つ<xref:System.Net.WebResponse>.</xref:System.Net.WebResponse></span><span class="sxs-lookup"><span data-stu-id="b9f98-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="b9f98-185">このタスクは、要求されたデータのダウンロードが完了し、タスクが最後まで実行された後に、実際の `WebResponse` オブジェクトを生成するという約束です。</span><span class="sxs-lookup"><span data-stu-id="b9f98-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="b9f98-186">取得する、`WebResponse`タスクから値を適用、 [Await](../../../../visual-basic/language-reference/operators/await-operator.md)演算子への呼び出しを`GetResponseAsync`次のコードを示します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
<span data-ttu-id="b9f98-187"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="b9f98-187"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span></span>  
     <span data-ttu-id="b9f98-188">`Await`演算子は、現在のメソッドの実行を中断`GetURLContents`待機中のタスクが完了するまで、します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-188">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="b9f98-189">その間、現在のメソッドの呼び出し元に制御が戻されます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-189">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="b9f98-190">この例では、現在のメソッドが `GetURLContents` で、呼び出し元が `SumPageSizes` です。</span><span class="sxs-lookup"><span data-stu-id="b9f98-190">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="b9f98-191">タスクが完了すると、約束されていた `WebResponse` オブジェクトが完了したタスクの値として生成され、変数 `response` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-191">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     The previous statement can be separated into the following two statements to clarify what happens.  
  
<span data-ttu-id="b9f98-192"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="b9f98-192"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
     <span data-ttu-id="b9f98-193">`webReq.GetResponseAsync` への呼び出しによって、`Task(Of WebResponse)` または `Task<WebResponse>` が返されます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-193">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="b9f98-194">`Await`を取得するタスクに演算子を適用、`WebResponse`値。</span><span class="sxs-lookup"><span data-stu-id="b9f98-194">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied. For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3.  <span data-ttu-id="b9f98-195">追加したので、`Await`前の手順で演算子は、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-195">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="b9f98-196">マークされたメソッドでのみ使用できます、演算子、 [Async](../../../../visual-basic/language-reference/modifiers/async.md)修飾子です。</span><span class="sxs-lookup"><span data-stu-id="b9f98-196">The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="b9f98-197">`CopyTo` への呼び出しを `CopyToAsync` への呼び出しに置き換える変換手順を繰り返す間は、エラーを無視してください。</span><span class="sxs-lookup"><span data-stu-id="b9f98-197">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="b9f98-198"><xref:System.IO.Stream.CopyToAsync%2A>。</xref:System.IO.Stream.CopyToAsync%2A>ために呼び出されるメソッドの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-198">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="b9f98-199">`CopyTo` または `CopyToAsync` メソッドは、その引数 `content` にバイトをコピーし、意味のある値は返しません。</span><span class="sxs-lookup"><span data-stu-id="b9f98-199">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="b9f98-200">同期バージョンでは、`CopyTo` への呼び出しは値を返さない単純なステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b9f98-200">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="b9f98-201">非同期バージョン`CopyToAsync`、 <xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task>を返します</span><span class="sxs-lookup"><span data-stu-id="b9f98-201">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="b9f98-202">タスクは "Task(void)" のように機能し、メソッドを待機できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-202">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="b9f98-203">次のコードに示すように、`Await` または `await` を、`CopyToAsync` への呼び出しに適用します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-203">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
<span data-ttu-id="b9f98-204"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="b9f98-204"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span></span>  
         <span data-ttu-id="b9f98-205">上記のステートメントでは、次の&2; 行のコードを省略しています。</span><span class="sxs-lookup"><span data-stu-id="b9f98-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
<span data-ttu-id="b9f98-206"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="b9f98-206"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span></span>  
4.  <span data-ttu-id="b9f98-207">`GetURLContents` 内で必要な作業として残っているのは、メソッド シグネチャの調整のみです。</span><span class="sxs-lookup"><span data-stu-id="b9f98-207">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="b9f98-208">使用することができます、`Await`演算子でマークされたメソッドでのみ、 [Async](../../../../visual-basic/language-reference/modifiers/async.md)修飾子です。</span><span class="sxs-lookup"><span data-stu-id="b9f98-208">You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="b9f98-209">メソッドとしてマークする修飾子を追加、 *async メソッド*次のコードを示します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-209">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
<span data-ttu-id="b9f98-210"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="b9f98-210"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span></span>  
5.  <span data-ttu-id="b9f98-211"><xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>。</xref:System.Threading.Tasks.Task%601></xref:System.Threading.Tasks.Task>できる、非同期メソッドの戻り値の型</span><span class="sxs-lookup"><span data-stu-id="b9f98-211">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="b9f98-212">Visual Basic でのメソッドは、`Task` または `Task(Of T)` を返す `Function` にするか、`Sub` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9f98-212">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="b9f98-213">通常、`Sub`メソッドは非同期のイベント ハンドラーでのみ使用場所`Sub`が必要です。</span><span class="sxs-lookup"><span data-stu-id="b9f98-213">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="b9f98-214">使用するその他の場合、 `Task(T)` 、完成したメソッドがある場合、[返す](../../../../visual-basic/language-reference/statements/return-statement.md)の値を返すステートメントは、T を入力し、使用する`Task`完成したメソッドの有効な値が返されない場合。</span><span class="sxs-lookup"><span data-stu-id="b9f98-214">In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>  
  
     <span data-ttu-id="b9f98-215">詳細については、次を参照してください。 [Async を返す型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-215">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="b9f98-216">メソッド `GetURLContents` には return ステートメントがあり、このステートメントはバイト配列を返します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-216">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="b9f98-217">そのため、非同期バージョンの戻り値の型は Task(T) であり、T はバイト配列です。</span><span class="sxs-lookup"><span data-stu-id="b9f98-217">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="b9f98-218">メソッド シグネチャに、次の変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-218">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="b9f98-219">戻り値の型を変更する`Task(Of Byte())`です。</span><span class="sxs-lookup"><span data-stu-id="b9f98-219">Change the return type to `Task(Of Byte())`.</span></span>  
  
    -   <span data-ttu-id="b9f98-220">規則により、非同期メソッドは "Async" で終わる名前を持つことになっているため、メソッドの名前を `GetURLContentsAsync` に変更します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-220">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="b9f98-221">これらの変更を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-221">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     <span data-ttu-id="b9f98-222">このいくつかの変更によって、`GetURLContents` の非同期メソッドへの変換が完了しました。</span><span class="sxs-lookup"><span data-stu-id="b9f98-222">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <span data-ttu-id="b9f98-223"><a name="SumPageSizes"></a>SumPageSizes を非同期メソッドに変換するには</span><span class="sxs-lookup"><span data-stu-id="b9f98-223"><a name="SumPageSizes"></a> To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="b9f98-224">`SumPageSizes` に対して、前述した手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-224">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="b9f98-225">まずは、`GetURLContents` への呼び出しを非同期呼び出しに変更します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-225">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="b9f98-226">呼び出されるメソッドの名前を `GetURLContents` から `GetURLContentsAsync` に変更します (まだ変更していない場合)。</span><span class="sxs-lookup"><span data-stu-id="b9f98-226">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="b9f98-227">適用`Await`タスクにいる`GetURLContentsAsync`バイトを取得するを返します。 配列の値。</span><span class="sxs-lookup"><span data-stu-id="b9f98-227">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="b9f98-228">これらの変更を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-228">The following code shows these changes.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     <span data-ttu-id="b9f98-229">上記の割り当てでは、次の&2; 行のコードを省略しています。</span><span class="sxs-lookup"><span data-stu-id="b9f98-229">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
  
    ```  
  
2.  <span data-ttu-id="b9f98-230">メソッドのシグネチャに、次の変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-230">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="b9f98-231">使用してメソッドをマーク、`Async`修飾子です。</span><span class="sxs-lookup"><span data-stu-id="b9f98-231">Mark the method with the `Async` modifier.</span></span>  
  
    -   <span data-ttu-id="b9f98-232">メソッド名に "Async" を追加します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-232">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="b9f98-233">今回、タスク戻り変数の T がない理由は、`SumPageSizesAsync` が T のための値を返さないからです (メソッドには いいえ`Return`ステートメントです)。ただし、メソッドは待機可能になるために `Task` を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9f98-233">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="b9f98-234">したがってからメソッドの型を変更`Sub`に`Function`します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-234">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="b9f98-235">関数の戻り値の型は、`Task` です。</span><span class="sxs-lookup"><span data-stu-id="b9f98-235">The return type of the function is `Task`.</span></span>  
  
     <span data-ttu-id="b9f98-236">これらの変更を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-236">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     <span data-ttu-id="b9f98-237">`SumPageSizes` から `SumPageSizesAsync` への変換が完了しました。</span><span class="sxs-lookup"><span data-stu-id="b9f98-237">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <span data-ttu-id="b9f98-238"><a name="startButton"></a>StartButton_Click を非同期メソッドに変換するには</span><span class="sxs-lookup"><span data-stu-id="b9f98-238"><a name="startButton"></a> To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="b9f98-239">イベント ハンドラーで、呼び出されるメソッドの名前を `SumPageSizes` から `SumPageSizesAsync` に変更します (まだ変更していない場合)。</span><span class="sxs-lookup"><span data-stu-id="b9f98-239">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="b9f98-240">`SumPageSizesAsync` は非同期メソッドであるため、結果を待機するイベント ハンドラーのコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-240">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="b9f98-241">`SumPageSizesAsync` への呼び出しは、`GetURLContentsAsync` の `CopyToAsync` への呼び出しに似ています。</span><span class="sxs-lookup"><span data-stu-id="b9f98-241">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="b9f98-242">この呼び出しによって、`Task(T)` ではなく `Task` が返されます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-242">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="b9f98-243">前述した手順と同様に、1 つまたは&2; つのステートメントを使用して、呼び出しを変換できます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-243">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="b9f98-244">これらの変更を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-244">The following code shows these changes.</span></span>  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  <span data-ttu-id="b9f98-245">誤って、操作を再入力を防ぐためには、次のステートメントを追加の上部にある`startButton_Click`を無効にする、**開始** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-245">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     <span data-ttu-id="b9f98-246">イベント ハンドラーの末尾で、ボタンを再び有効にできます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-246">You can reenable the button at the end of the event handler.</span></span>  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     <span data-ttu-id="b9f98-247">再入の詳細については、次を参照してください。 [(Visual Basic) の非同期アプリにおける再入の処理](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-247">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="b9f98-248">最後に、追加、`Async`修飾子、宣言をイベント ハンドラーを待機できるように`SumPagSizesAsync`します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-248">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     <span data-ttu-id="b9f98-249">通常、イベント ハンドラーの名前は変更されません。</span><span class="sxs-lookup"><span data-stu-id="b9f98-249">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="b9f98-250">戻り値の型は変更されずに`Task`イベント ハンドラーがある必要がありますので`Sub`Visual Basic におけるプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="b9f98-250">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>  
  
     <span data-ttu-id="b9f98-251">同期処理から非同期処理へのプロジェクトの変換が完了しました。</span><span class="sxs-lookup"><span data-stu-id="b9f98-251">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <span data-ttu-id="b9f98-252"><a name="testAsynch"></a>非同期のソリューションをテストするには</span><span class="sxs-lookup"><span data-stu-id="b9f98-252"><a name="testAsynch"></a> To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="b9f98-253">F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-253">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="b9f98-254">同期ソリューションの出力に似た出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-254">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="b9f98-255">ただし、次の相違点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="b9f98-255">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="b9f98-256">処理の完了後に、すべての結果が同時に表示されることはありません。</span><span class="sxs-lookup"><span data-stu-id="b9f98-256">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="b9f98-257">たとえば、両方のプログラムの `startButton_Click` には、テキスト ボックスをクリアする行が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9f98-257">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="b9f98-258">選択した場合の実行の間のテキスト ボックスをオフにすることが目的、**開始**1 組の結果が表示されたら、2 回ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-258">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="b9f98-259">同期バージョンでは、2 回目のカウントが表示される直前、ダウンロードが完了して UI スレッドが他の処理を実行できる状態になったときにテキスト ボックスがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-259">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="b9f98-260">選択した後すぐに、非同期バージョンで、テキスト ボックスをクリア、**開始** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-260">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="b9f98-261">最も重要な点は、ダウンロード中に UI スレッドがブロックされないことです。</span><span class="sxs-lookup"><span data-stu-id="b9f98-261">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="b9f98-262">Web リソースをダウンロード、カウント、および表示している間に、ウィンドウの移動やサイズ変更を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-262">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="b9f98-263">Web サイトのいずれかの処理が遅いか応答していないする操作を取り消すことを選択している場合、**閉じる**(右上隅の赤いフィールドに x) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-263">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <span data-ttu-id="b9f98-264"><a name="GetURLContentsAsync"></a>GetURLContentsAsync メソッドを .NET Framework メソッドに置き換えます</span><span class="sxs-lookup"><span data-stu-id="b9f98-264"><a name="GetURLContentsAsync"></a> To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="b9f98-265">.NET Framework 4.5 では、使用できる非同期メソッドが数多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="b9f98-265">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="b9f98-266">1 つで、<xref:System.Net.Http.HttpClient>メソッド<xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>、必要なものだけをこのチュートリアルでは</xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29></xref:System.Net.Http.HttpClient>。</span><span class="sxs-lookup"><span data-stu-id="b9f98-266">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="b9f98-267">これを、前述の手順で作成した `GetURLContentsAsync` メソッドの代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-267">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="b9f98-268">まずは、`SumPageSizesAsync` メソッドに `HttpClient` オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-268">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="b9f98-269">次の宣言をメソッドの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="b9f98-269">Add the following declaration at the start of the method.</span></span>  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  <span data-ttu-id="b9f98-270">`SumPageSizesAsync,` で、`GetURLContentsAsync` メソッドへの呼び出しを `HttpClient` メソッドへの呼び出しに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-270">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  <span data-ttu-id="b9f98-271">記述した `GetURLContentsAsync` メソッドを削除するかコメント アウトします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-271">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="b9f98-272">F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="b9f98-272">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="b9f98-273">このバージョンのプロジェクトの動作は、「非同期ソリューションをテストするには」の手順で説明している動作と同じですが、さらに少ない手間で作成できます。</span><span class="sxs-lookup"><span data-stu-id="b9f98-273">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <span data-ttu-id="b9f98-274"><a name="BKMK_CompleteCodeExamples"></a>使用例</span><span class="sxs-lookup"><span data-stu-id="b9f98-274"><a name="BKMK_CompleteCodeExamples"></a> Example</span></span>  
 <span data-ttu-id="b9f98-275">次のコードには、記述した非同期 `GetURLContentsAsync` メソッドを使用する、同期ソリューションから非同期ソリューションへの変換例のすべてが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9f98-275">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="b9f98-276">この例は、元の同期ソリューションと非常によく似ています。</span><span class="sxs-lookup"><span data-stu-id="b9f98-276">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        ' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
            ' The previous line abbreviates the following two assignment statements.  
  
            '//<snippet21>  
            ' GetURLContentsAsync returns a task. At completion, the task  
            ' produces a byte array.  
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
  
            ' The previous statement abbreviates the following two statements.  
  
            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
            'Using response As WebResponse = Await responseTask  
  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                Await responseStream.CopyToAsync(content)  
  
                ' The previous statement abbreviates the following two statements.  
  
                ' CopyToAsync returns a Task, not a Task<T>.  
                'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
                ' When copyTask is completed, content contains a copy of  
                ' responseStream.  
                'Await copyTask  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
 <span data-ttu-id="b9f98-277">次のコードには、`HttpClient` の `GetByteArrayAsync` メソッドを使用するソリューション例のすべてが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9f98-277">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetByteArrayAsync returns a task. At completion, the task  
            ' produces a byte array.  
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
            ' The following two lines can replace the previous assignment statement.  
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9f98-278">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9f98-278">See Also</span></span>  
 <span data-ttu-id="b9f98-279">[非同期のサンプル: Web のチュートリアル (c# および Visual Basic) にアクセスします。](http://go.microsoft.com/fwlink/?LinkId=255191) </span><span class="sxs-lookup"><span data-stu-id="b9f98-279">[Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255191) </span></span>  
<span data-ttu-id="b9f98-280"> [Await 演算子](../../../../visual-basic/language-reference/operators/await-operator.md) </span><span class="sxs-lookup"><span data-stu-id="b9f98-280"> [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) </span></span>  
<span data-ttu-id="b9f98-281"> [非同期](../../../../visual-basic/language-reference/modifiers/async.md) </span><span class="sxs-lookup"><span data-stu-id="b9f98-281"> [Async](../../../../visual-basic/language-reference/modifiers/async.md) </span></span>  
<span data-ttu-id="b9f98-282"> [非同期プログラミングを Async と Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="b9f98-282"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="b9f98-283"> [非同期の戻り値の型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span><span class="sxs-lookup"><span data-stu-id="b9f98-283"> [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span></span>  
<span data-ttu-id="b9f98-284"> [タスク ベースの非同期プログラミング (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847) </span><span class="sxs-lookup"><span data-stu-id="b9f98-284"> [Task-based Asynchronous Programming (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847) </span></span>  
<span data-ttu-id="b9f98-285"> [方法: Task.WhenAll (Visual Basic) を使用して Asyncwalkthrough を拡張](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md) </span><span class="sxs-lookup"><span data-stu-id="b9f98-285"> [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md) </span></span>  
<span data-ttu-id="b9f98-286"> [方法: 並列で Async を使用して、複数の Web 要求を実行して、Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)</span><span class="sxs-lookup"><span data-stu-id="b9f98-286"> [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)</span></span>
