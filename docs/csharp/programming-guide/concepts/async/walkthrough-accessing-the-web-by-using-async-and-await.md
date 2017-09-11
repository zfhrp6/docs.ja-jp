---
title: "チュートリアル: Async と Await を使用した Web へのアクセス (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: get-started-article
dev_langs:
- CSharp
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7c03cad060e2ba459277c28f929df88be70e4044
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="7d9fd-102">チュートリアル: Async と Await を使用した Web へのアクセス (C#)</span><span class="sxs-lookup"><span data-stu-id="7d9fd-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>
<span data-ttu-id="7d9fd-103">async/await 機能を使用することで、非同期プログラムをより簡単かつ直感的に記述できます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="7d9fd-104">同期コードに似た非同期コードを記述し、通常の非同期コードが必要とする難しいコールバック関数や継続の処理をコンパイラに任せます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="7d9fd-105">非同期機能について詳しくは、「[Async および Await を使用した非同期プログラミング (C# および Visual Basic)](../../../../csharp/programming-guide/concepts/async/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="7d9fd-106">このチュートリアルは、Web サイトの一覧でのバイト数の合計を計算する同期 Windows Presentation Foundation (WPF) アプリケーションから開始します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="7d9fd-107">その後、新しい機能を使用して、アプリケーションを非同期ソリューションに変換します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="7d9fd-108">自分でアプリケーションを作成しない場合は、[開発者コード サンプル](http://go.microsoft.com/fwlink/?LinkId=255191)のページから、"Async Sample: Accessing the Web Walkthrough (C# and Visual Basic) (非同期サンプル: Web へのアクセスのチュートリアル (C# および Visual Basic))" をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
  
 <span data-ttu-id="7d9fd-109">このチュートリアルでは、次のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="7d9fd-110">WPF アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="7d9fd-111">単純な WPF MainWindow をデザインするには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="7d9fd-112">参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="7d9fd-113">ディレクティブを使用して必要なものを追加するには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-113">To add necessary using directives</span></span>](#usingDir)  
  
-   [<span data-ttu-id="7d9fd-114">同期アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="7d9fd-115">同期ソリューションをテストするには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="7d9fd-116">GetURLContents を非同期メソッドに変換するには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="7d9fd-117">SumPageSizes を非同期メソッドに変換するには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="7d9fd-118">startButton_Click を非同期メソッドに変換するには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="7d9fd-119">非同期ソリューションをテストするには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="7d9fd-120">GetURLContentsAsync メソッドを .NET Framework メソッドに置き換えるには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="7d9fd-121">例</span><span class="sxs-lookup"><span data-stu-id="7d9fd-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="7d9fd-122">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7d9fd-122">Prerequisites</span></span>  
 <span data-ttu-id="7d9fd-123">お使いのコンピューターに、Visual Studio 2012 以降がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="7d9fd-124">詳しくは、[Microsoft Web サイト](http://go.microsoft.com/fwlink/?LinkId=235233)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-124">For more information, see the [Microsoft website](http://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
###  <span data-ttu-id="7d9fd-125"><a name="CreateWPFApp"></a> WPF アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-125"><a name="CreateWPFApp"></a> To create a WPF application</span></span>  
  
1.  <span data-ttu-id="7d9fd-126">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-126">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="7d9fd-127">メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="7d9fd-128">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-128">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="7d9fd-129">**[インストールされたテンプレート]** ウィンドウで、[Visual C#] をクリックし、プロジェクトの種類の一覧で **[WPF アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-129">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="7d9fd-130">**[名前]** ボックスに「`AsyncExampleWPF`」と入力して、**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="7d9fd-131">**ソリューション エクスプローラー**に新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-131">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <span data-ttu-id="7d9fd-132"><a name="MainWindow"></a> 単純な WPF MainWindow をデザインするには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-132"><a name="MainWindow"></a> To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="7d9fd-133">Visual Studio コード エディターで、 **[MainWindow.xaml]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="7d9fd-134">**[ツールボックス]** ウィンドウが表示されていない場合は、**[表示]** メニューを開き、**[ツールボックス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="7d9fd-135">**[Button]** コントロールと **[TextBox]** コントロールを **[MainWindow]** ウィンドウに追加します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="7d9fd-136">**[TextBox]** コントロールを強調表示し、**[プロパティ]** ウィンドウで次の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="7d9fd-137">**[Name]** プロパティを `resultsTextBox` に設定します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="7d9fd-138">**[Height]** プロパティを 250 に設定します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-138">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="7d9fd-139">**[Width]** プロパティを 500 に設定します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-139">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="7d9fd-140">**[テキスト]** タブで、Lucida Console や Global Monospace などの等幅フォントを指定します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="7d9fd-141">**[Button]** コントロールを強調表示し、**[プロパティ]** ウィンドウで次の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="7d9fd-142">**[Name]** プロパティを `startButton` に設定します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-142">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="7d9fd-143">**[Content]** プロパティの値を **[Button]** から **[Start]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="7d9fd-144">テキスト ボックスとボタンの位置を調整し、両方が **[MainWindow]** ウィンドウ内に表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="7d9fd-145">WPF XAML デザイナーについて詳しくは、「[XAML デザイナーを使用した UI の作成](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <span data-ttu-id="7d9fd-146"><a name="AddRef"></a> 参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-146"><a name="AddRef"></a> To add a reference</span></span>  
  
1.  <span data-ttu-id="7d9fd-147">**ソリューション エクスプローラー**で、プロジェクトの名前を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="7d9fd-148">メニュー バーで、**[プロジェクト]**、**[参照の追加]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="7d9fd-149">**[参照マネージャー]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-149">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="7d9fd-150">ダイアログ ボックスの上部で、プロジェクトのターゲットが .NET Framework 4.5 以上であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="7d9fd-151">**[アセンブリ]** で、**[フレームワーク]** を選択します (選択されていない場合)。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="7d9fd-152">名前の一覧で、**[System.Net.Http]** のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="7d9fd-153">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-153">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <span data-ttu-id="7d9fd-154"><a name="usingDir"></a> ディレクティブを使用して必要なものを追加するには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-154"><a name="usingDir"></a> To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="7d9fd-155">**ソリューション エクスプローラー**で MainWindow.xaml.cs のショートカット メニューを開き、**[コードの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="7d9fd-156">次の `using` ディレクティブが含まれていない場合は、コード ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-156">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>  
  
    ```csharp  
    using System.Net.Http;  
    using System.Net;  
    using System.IO;  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <span data-ttu-id="7d9fd-157"><a name="synchronous"></a> 同期アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-157"><a name="synchronous"></a> To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="7d9fd-158">デザイン ウィンドウの MainWindow.xaml で、**[Start]** ボタンをダブルクリックして、MainWindow.xaml.cs に `startButton_Click` イベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="7d9fd-159">MainWindow.xaml.cs で、次のコードを `startButton_Click` の本文にコピーします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-159">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    SumPageSizes();  
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";  
    ```  
  
     <span data-ttu-id="7d9fd-160">このコードは、`SumPageSizes` アプリケーションを実行するメソッドを呼び出し、`startButton_Click` に制御が戻るとメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="7d9fd-161">同期ソリューションのコードには、次の 4 つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="7d9fd-162">`SumPageSizes` は、`SetUpURLList` から Web ページ URL のリストを取得し、`GetURLContents` と `DisplayResults` を呼び出して各 URL を処理します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="7d9fd-163">`SetUpURLList` は、Web アドレスのリストを作成して返します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="7d9fd-164">`GetURLContents` は、各 Web サイトのコンテンツをダウンロードし、バイト配列としてそのコンテンツを返します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="7d9fd-165">`DisplayResults` は、各 URL のバイト配列内のバイト数を表示します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="7d9fd-166">次の 4 つのメソッドをコピーし、それを MainWindow.xaml.cs の `startButton_Click` イベント ハンドラーの下に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>  
  
    ```csharp  
    private void SumPageSizes()  
    {  
        // Make a list of web addresses.  
        List<string> urlList = SetUpURLList();   
  
        var total = 0;  
        foreach (var url in urlList)  
        {  
            // GetURLContents returns the contents of url as a byte array.  
            byte[] urlContents = GetURLContents(url);  
  
            DisplayResults(url, urlContents);  
  
            // Update the total.  
            total += urlContents.Length;  
        }  
  
        // Display the total count for all of the web addresses.  
        resultsTextBox.Text +=   
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
    }  
  
    private List<string> SetUpURLList()  
    {  
        var urls = new List<string>   
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
        };  
        return urls;  
    }  
  
    private byte[] GetURLContents(string url)  
    {  
        // The downloaded resource ends up in the variable named content.  
        var content = new MemoryStream();  
  
        // Initialize an HttpWebRequest for the current URL.  
        var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
        // Send the request to the Internet resource and wait for  
        // the response.  
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        using (WebResponse response = webReq.GetResponse())  
        {  
            // Get the data stream that is associated with the specified URL.  
            using (Stream responseStream = response.GetResponseStream())  
            {  
                // Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content);  
            }  
        }  
  
        // Return the result as a byte array.  
        return content.ToArray();  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format   
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "http://".  
        var displayURL = url.Replace("http://", "");  
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
    }  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <span data-ttu-id="7d9fd-167"><a name="testSynch"></a> 同期ソリューションをテストするには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-167"><a name="testSynch"></a> To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="7d9fd-168">F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="7d9fd-169">次の一覧のような出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-169">Output that resembles the following list should appear.</span></span>  
  
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
  
     <span data-ttu-id="7d9fd-170">カウントの表示には数秒かかる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="7d9fd-171">その間、要求されたリソースのダウンロードが完了するまで UI スレッドがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="7d9fd-172">このため、**[Start]** ボタンのクリック後は、表示ウィンドウの移動、最大化、最小化のほか、閉じることさえできなくなります。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="7d9fd-173">バイト カウントの表示が開始するまでは、これらの操作を実行しても失敗します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="7d9fd-174">Web サイトが応答していない場合、どのサイトに問題があるのかを示す情報は表示されません。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="7d9fd-175">待つのをやめて、プログラムを閉じることさえ難しい状態になります。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-175">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <span data-ttu-id="7d9fd-176"><a name="GetURLContents"></a> GetURLContents を非同期メソッドに変換するには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-176"><a name="GetURLContents"></a> To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="7d9fd-177">同期ソリューションを非同期ソリューションに変換する際に、最初に取りかかるのに最適な場所は、`GetURLContents` 内です。その理由は、<xref:System.Net.HttpWebRequest> の <xref:System.Net.HttpWebRequest.GetResponse%2A> メソッドおよび <xref:System.IO.Stream> の <xref:System.IO.Stream.CopyTo%2A> メソッドへの呼び出しで、アプリケーションが Web にアクセスするためです。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="7d9fd-178">.NET Framework には両方のメソッドの非同期バージョンが用意されているため、変換は簡単です。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="7d9fd-179">`GetURLContents` で使用されているメソッドの詳細については、「<xref:System.Net.WebRequest>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7d9fd-180">このチュートリアルの手順に従っていると、いくつかのコンパイラ エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="7d9fd-181">これらのエラーは無視することで、チュートリアルを続行できます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="7d9fd-182">`GetURLContents` の 3 行目で呼び出されるメソッドを、`GetResponse` から、非同期でタスク ベースの <xref:System.Net.WebRequest.GetResponseAsync%2A> メソッドに変更します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```csharp  
    using (WebResponse response = webReq.GetResponseAsync())  
    ```  
  
2.  <span data-ttu-id="7d9fd-183">`GetResponseAsync` は、<xref:System.Threading.Tasks.Task%601> を返します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="7d9fd-184">この場合、*タスク戻り変数*の `TResult` の型は <xref:System.Net.WebResponse> です。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="7d9fd-185">このタスクは、要求されたデータのダウンロードが完了し、タスクが最後まで実行された後に、実際の `WebResponse` オブジェクトを生成するという約束です。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="7d9fd-186">タスクから `WebResponse` 値を取得するには、次のコードに示すように、[await](../../../../csharp/language-reference/keywords/await.md) (C#) 演算子を `GetResponseAsync` への呼び出しに適用します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-186">To retrieve the `WebResponse` value from the task, apply an [await](../../../../csharp/language-reference/keywords/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    using (WebResponse response = await webReq.GetResponseAsync())  
    ```  
  
     <span data-ttu-id="7d9fd-187">`await` 演算子は、現在のメソッド、`GetURLContents` の実行を、待機しているタスクが完了するまで中断します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-187">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="7d9fd-188">その間、現在のメソッドの呼び出し元に制御が戻されます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="7d9fd-189">この例では、現在のメソッドが `GetURLContents` で、呼び出し元が `SumPageSizes` です。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="7d9fd-190">タスクが完了すると、約束されていた `WebResponse` オブジェクトが完了したタスクの値として生成され、変数 `response` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="7d9fd-191">上記のステートメントは、動作を明確にするため、次の 2 つのステートメントに分割できます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```csharp  
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
    //using (WebResponse response = await responseTask)  
    ```  
  
     <span data-ttu-id="7d9fd-192">`webReq.GetResponseAsync` への呼び出しによって、`Task(Of WebResponse)` または `Task<WebResponse>` が返されます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="7d9fd-193">その後、`WebResponse` 値を取得するため、タスクに await 演算子が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-193">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="7d9fd-194">非同期メソッドにタスクの完了に依存しない処理がある場合、メソッドはこれら 2 つのステートメントの間、つまり非同期メソッドへの呼び出しから、`await` 演算子の適用までの間にその処理を続行することができます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="7d9fd-195">この例については、「[方法: Async と Await を使用して複数の Web 要求を並列実行する (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)」および「[方法: Task.WhenAll を使用して AsyncWalkthrough を拡張する (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3.  <span data-ttu-id="7d9fd-196">前の手順で `await` 演算子を追加したため、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-196">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="7d9fd-197">この演算子は、[async](../../../../csharp/language-reference/keywords/async.md) 修飾子でマークされているメソッドでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-197">The operator can be used only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="7d9fd-198">`CopyTo` への呼び出しを `CopyToAsync` への呼び出しに置き換える変換手順を繰り返す間は、エラーを無視してください。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="7d9fd-199">呼び出されるメソッドの名前を <xref:System.IO.Stream.CopyToAsync%2A> に変更します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="7d9fd-200">`CopyTo` または `CopyToAsync` メソッドは、その引数 `content` にバイトをコピーし、意味のある値は返しません。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="7d9fd-201">同期バージョンでは、`CopyTo` への呼び出しは値を返さない単純なステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="7d9fd-202">非同期バージョンでは、`CopyToAsync` は <xref:System.Threading.Tasks.Task> を返します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="7d9fd-203">タスクは "Task(void)" のように機能し、メソッドを待機できるようにします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="7d9fd-204">次のコードに示すように、`Await` または `await` を、`CopyToAsync` への呼び出しに適用します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```csharp  
        await responseStream.CopyToAsync(content);  
        ```  
  
         <span data-ttu-id="7d9fd-205">上記のステートメントでは、次の 2 行のコードを省略しています。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```csharp  
        // CopyToAsync returns a Task, not a Task<T>.  
        //Task copyTask = responseStream.CopyToAsync(content);  
  
        // When copyTask is completed, content contains a copy of  
        // responseStream.  
        //await copyTask;  
        ```  
  
4.  <span data-ttu-id="7d9fd-206">`GetURLContents` 内で必要な作業として残っているのは、メソッド シグネチャの調整のみです。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="7d9fd-207">`await` 演算子は、[async](../../../../csharp/language-reference/keywords/async.md) 修飾子でマークされているメソッドでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-207">You can use the `await` operator only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="7d9fd-208">次のコードに示すように、修飾子を追加し、メソッドを*非同期メソッド*としてマークします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```csharp  
    private async byte[] GetURLContents(string url)  
    ```  
  
5.  <span data-ttu-id="7d9fd-209">C# での非同期メソッドの戻り値の型は、<xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601>、または `void` のみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="7d9fd-210">通常、`void` の戻り値の型は、`void` を必要とする非同期イベント ハンドラーでのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-210">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="7d9fd-211">それ以外のケースでは、完成したメソッドに、T 型の値を返す [return](../../../../csharp/language-reference/keywords/return.md) ステートメントが含まれる場合は `Task(T)` を使用し、完成したメソッドが意味のある値を返さない場合は `Task` を使用します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-211">In other cases, you use `Task(T)` if the completed method has a [return](../../../../csharp/language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="7d9fd-212">戻り値の型 `Task` は、"Task(void)" を意味するものと考えることができます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-212">You can think of the `Task` return type as meaning "Task(void)."</span></span>  
  
     <span data-ttu-id="7d9fd-213">詳しくは、「[非同期の戻り値の型 (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-213">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="7d9fd-214">メソッド `GetURLContents` には return ステートメントがあり、このステートメントはバイト配列を返します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="7d9fd-215">そのため、非同期バージョンの戻り値の型は Task(T) であり、T はバイト配列です。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="7d9fd-216">メソッド シグネチャに、次の変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-216">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="7d9fd-217">戻り値の型を `Task<byte[]>` に変更します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-217">Change the return type to `Task<byte[]>`.</span></span>  
  
    -   <span data-ttu-id="7d9fd-218">規則により、非同期メソッドは "Async" で終わる名前を持つことになっているため、メソッドの名前を `GetURLContentsAsync` に変更します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="7d9fd-219">これらの変更を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-219">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task<byte[]> GetURLContentsAsync(string url)  
    ```  
  
     <span data-ttu-id="7d9fd-220">このいくつかの変更によって、`GetURLContents` の非同期メソッドへの変換が完了しました。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <span data-ttu-id="7d9fd-221"><a name="SumPageSizes"></a> SumPageSizes を非同期メソッドに変換するには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-221"><a name="SumPageSizes"></a> To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="7d9fd-222">`SumPageSizes` に対して、前述した手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="7d9fd-223">まずは、`GetURLContents` への呼び出しを非同期呼び出しに変更します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="7d9fd-224">呼び出されるメソッドの名前を `GetURLContents` から `GetURLContentsAsync` に変更します (まだ変更していない場合)。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="7d9fd-225">バイト配列値を取得するために、`await` を、`GetURLContentsAsync` が返すタスクに適用します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-225">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="7d9fd-226">これらの変更を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-226">The following code shows these changes.</span></span>  
  
    ```csharp  
    byte[] urlContents = await GetURLContentsAsync(url);  
    ```  
  
     <span data-ttu-id="7d9fd-227">上記の割り当てでは、次の 2 行のコードを省略しています。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-227">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```csharp  
    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    // produces a byte array.  
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //byte[] urlContents = await getContentsTask;  
    ```  
  
2.  <span data-ttu-id="7d9fd-228">メソッドのシグネチャに、次の変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-228">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="7d9fd-229">メソッドを `async` 修飾子でマークします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-229">Mark the method with the `async` modifier.</span></span>  
  
    -   <span data-ttu-id="7d9fd-230">メソッド名に "Async" を追加します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-230">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="7d9fd-231">今回、タスク戻り変数の T がない理由は、`SumPageSizesAsync` が T のための値を返さないからです (メソッドに `return` ステートメントがありません)。ただし、メソッドは待機可能になるために `Task` を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="7d9fd-232">そのため、メソッドの戻り値の型を `void` から `Task` に変更します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-232">Therefore, change the return type of the method from `void` to `Task`.</span></span>  
  
     <span data-ttu-id="7d9fd-233">これらの変更を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-233">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task SumPageSizesAsync()  
    ```  
  
     <span data-ttu-id="7d9fd-234">`SumPageSizes` から `SumPageSizesAsync` への変換が完了しました。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-234">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <span data-ttu-id="7d9fd-235"><a name="startButton"></a> startButton_Click を非同期メソッドに変換するには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-235"><a name="startButton"></a> To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="7d9fd-236">イベント ハンドラーで、呼び出されるメソッドの名前を `SumPageSizes` から `SumPageSizesAsync` に変更します (まだ変更していない場合)。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-236">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="7d9fd-237">`SumPageSizesAsync` は非同期メソッドであるため、結果を待機するイベント ハンドラーのコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-237">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="7d9fd-238">`SumPageSizesAsync` への呼び出しは、`GetURLContentsAsync` の `CopyToAsync` への呼び出しに似ています。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-238">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="7d9fd-239">この呼び出しによって、`Task(T)` ではなく `Task` が返されます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-239">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="7d9fd-240">前述した手順と同様に、1 つまたは 2 つのステートメントを使用して、呼び出しを変換できます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-240">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="7d9fd-241">これらの変更を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-241">The following code shows these changes.</span></span>  
  
    ```csharp  
    // One-step async call.  
    await SumPageSizesAsync();  
  
    // Two-step async call.  
    //Task sumTask = SumPageSizesAsync();  
    //await sumTask;  
    ```  
  
3.  <span data-ttu-id="7d9fd-242">誤って操作が再入することを避けるために、次のステートメントを `startButton_Click` の先頭に追加して **[Start]** ボタンを無効にします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-242">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```csharp  
    // Disable the button until the operation is complete.  
    startButton.IsEnabled = false;  
    ```  
  
     <span data-ttu-id="7d9fd-243">イベント ハンドラーの末尾で、ボタンを再び有効にできます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-243">You can reenable the button at the end of the event handler.</span></span>  
  
    ```csharp  
    // Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = true;  
    ```  
  
     <span data-ttu-id="7d9fd-244">再入について詳しくは、「[非同期アプリにおける再入の処理 (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-244">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="7d9fd-245">最後に、`async` 修飾子を宣言に追加し、イベント ハンドラーが `SumPagSizesAsync` を待機できるようにします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-245">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```csharp  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    ```  
  
     <span data-ttu-id="7d9fd-246">通常、イベント ハンドラーの名前は変更されません。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-246">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="7d9fd-247">戻り値の型が `Task` に変更されていない理由は、イベント ハンドラーが `void` を返す必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-247">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>  
  
     <span data-ttu-id="7d9fd-248">同期処理から非同期処理へのプロジェクトの変換が完了しました。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-248">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <span data-ttu-id="7d9fd-249"><a name="testAsynch"></a> 非同期ソリューションをテストするには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-249"><a name="testAsynch"></a> To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="7d9fd-250">F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-250">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="7d9fd-251">同期ソリューションの出力に似た出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-251">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="7d9fd-252">ただし、次の相違点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-252">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="7d9fd-253">処理の完了後に、すべての結果が同時に表示されることはありません。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-253">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="7d9fd-254">たとえば、両方のプログラムの `startButton_Click` には、テキスト ボックスをクリアする行が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-254">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="7d9fd-255">この目的は、実行ごとにテキスト ボックスをクリアすることです。1 つの結果セットが表示された後に、もう一度 **[Start]** ボタンをクリックすると、テキスト ボックスがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-255">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="7d9fd-256">同期バージョンでは、2 回目のカウントが表示される直前、ダウンロードが完了して UI スレッドが他の処理を実行できる状態になったときにテキスト ボックスがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-256">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="7d9fd-257">非同期バージョンでは、**[Start]** ボタンをクリックした直後にテキスト ボックスがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-257">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="7d9fd-258">最も重要な点は、ダウンロード中に UI スレッドがブロックされないことです。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-258">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="7d9fd-259">Web リソースをダウンロード、カウント、および表示している間に、ウィンドウの移動やサイズ変更を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-259">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="7d9fd-260">いずれかの Web サイトの処理が遅い、または応答しない場合、**閉じる**ボタン (右上隅の赤色のフィールドにある [x]) をクリックすることで、操作を取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-260">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <span data-ttu-id="7d9fd-261"><a name="GetURLContentsAsync"></a> GetURLContentsAsync メソッドを .NET Framework メソッドに置き換えるには</span><span class="sxs-lookup"><span data-stu-id="7d9fd-261"><a name="GetURLContentsAsync"></a> To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="7d9fd-262">.NET Framework 4.5 では、使用できる非同期メソッドが数多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-262">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="7d9fd-263">その 1 つである、<xref:System.Net.Http.HttpClient> の <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29> メソッドは、このチュートリアルに必要な処理だけを実行します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-263">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="7d9fd-264">これを、前述の手順で作成した `GetURLContentsAsync` メソッドの代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-264">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="7d9fd-265">まずは、`SumPageSizesAsync` メソッドに `HttpClient` オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-265">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="7d9fd-266">次の宣言をメソッドの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-266">Add the following declaration at the start of the method.</span></span>  
  
    ```csharp  
    // Declare an HttpClient object and increase the buffer size. The  
    // default buffer size is 65,536.  
    HttpClient client =  
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
    ```  
  
2.  <span data-ttu-id="7d9fd-267">`SumPageSizesAsync,` で、`GetURLContentsAsync` メソッドへの呼び出しを `HttpClient` メソッドへの呼び出しに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-267">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```csharp  
    byte[] urlContents = await client.GetByteArrayAsync(url);  
    ```  
  
3.  <span data-ttu-id="7d9fd-268">記述した `GetURLContentsAsync` メソッドを削除するかコメント アウトします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-268">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="7d9fd-269">F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-269">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="7d9fd-270">このバージョンのプロジェクトの動作は、「非同期ソリューションをテストするには」の手順で説明している動作と同じですが、さらに少ない手間で作成できます。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-270">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <span data-ttu-id="7d9fd-271"><a name="BKMK_CompleteCodeExamples"></a> 例</span><span class="sxs-lookup"><span data-stu-id="7d9fd-271"><a name="BKMK_CompleteCodeExamples"></a> Example</span></span>  
 <span data-ttu-id="7d9fd-272">次のコードには、記述した非同期 `GetURLContentsAsync` メソッドを使用する、同期ソリューションから非同期ソリューションへの変換例のすべてが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-272">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="7d9fd-273">この例は、元の同期ソリューションと非常によく似ています。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-273">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            resultsTextBox.Clear();  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            // Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                byte[] urlContents = await GetURLContentsAsync(url);  
  
                // The previous line abbreviates the following two assignment statements.  
  
                // GetURLContentsAsync returns a Task<T>. At completion, the task  
                // produces a byte array.  
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.            
                total += urlContents.Length;  
            }  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
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
            };  
            return urls;  
        }  
  
        private async Task<byte[]> GetURLContentsAsync(string url)  
        {  
            // The downloaded resource ends up in the variable named content.  
            var content = new MemoryStream();  
  
            // Initialize an HttpWebRequest for the current URL.  
            var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
            // Send the request to the Internet resource and wait for  
            // the response.                  
            using (WebResponse response = await webReq.GetResponseAsync())  
  
            // The previous statement abbreviates the following two statements.  
  
            //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
            //using (WebResponse response = await responseTask)  
            {  
                // Get the data stream that is associated with the specified url.  
                using (Stream responseStream = response.GetResponseStream())  
                {  
                    // Read the bytes in responseStream and copy them to content.   
                    await responseStream.CopyToAsync(content);  
  
                    // The previous statement abbreviates the following two statements.  
  
                    // CopyToAsync returns a Task, not a Task<T>.  
                    //Task copyTask = responseStream.CopyToAsync(content);  
  
                    // When copyTask is completed, content contains a copy of  
                    // responseStream.  
                    //await copyTask;  
                }  
            }  
            // Return the result as a byte array.  
            return content.ToArray();  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="7d9fd-274">次のコードには、`HttpClient` の `GetByteArrayAsync` メソッドを使用するソリューション例のすべてが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d9fd-274">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            //// Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Declare an HttpClient object and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                // GetByteArrayAsync returns a task. At completion, the task  
                // produces a byte array.  
                byte[] urlContents = await client.GetByteArrayAsync(url);                 
  
                // The following two lines can replace the previous assignment statement.  
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.  
                total += urlContents.Length;  
            }  
  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
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
            };  
            return urls;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d9fd-275">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d9fd-275">See Also</span></span>  
 <span data-ttu-id="7d9fd-276">[Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255191)  (非同期のサンプル: Web サイトへのアクセスのチュートリアル (C# および Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="7d9fd-276">[Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255191) </span></span>  
 <span data-ttu-id="7d9fd-277">[async](../../../../csharp/language-reference/keywords/async.md) </span><span class="sxs-lookup"><span data-stu-id="7d9fd-277">[async](../../../../csharp/language-reference/keywords/async.md) </span></span>  
 <span data-ttu-id="7d9fd-278">[await](../../../../csharp/language-reference/keywords/await.md) </span><span class="sxs-lookup"><span data-stu-id="7d9fd-278">[await](../../../../csharp/language-reference/keywords/await.md) </span></span>  
 <span data-ttu-id="7d9fd-279">[Async および Await を使用した非同期プログラミング (C#)](../../../../csharp/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="7d9fd-279">[Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md) </span></span>  
 <span data-ttu-id="7d9fd-280">[非同期の戻り値の型 (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md) </span><span class="sxs-lookup"><span data-stu-id="7d9fd-280">[Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md) </span></span>  
 <span data-ttu-id="7d9fd-281">[タスク ベースの非同期プログラミング (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847) </span><span class="sxs-lookup"><span data-stu-id="7d9fd-281">[Task-based Asynchronous Programming (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847) </span></span>  
 <span data-ttu-id="7d9fd-282">[方法: Task.WhenAll を使用して非同期のチュートリアルを拡張する (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md) </span><span class="sxs-lookup"><span data-stu-id="7d9fd-282">[How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md) </span></span>  
 [<span data-ttu-id="7d9fd-283">方法: Async と Await を使用して複数の Web 要求を並列実行する (C#)</span><span class="sxs-lookup"><span data-stu-id="7d9fd-283">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)

