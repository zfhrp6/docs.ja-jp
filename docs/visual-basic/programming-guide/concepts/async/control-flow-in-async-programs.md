---
title: "非同期プログラム (Visual Basic) でフロー制御 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
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
ms.openlocfilehash: 15e02fbc023db9ae2f3ee9f40598faa7c9c027a0
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="control-flow-in-async-programs-visual-basic"></a><span data-ttu-id="417c6-102">(Visual Basic) の非同期プログラムにおける制御フロー</span><span class="sxs-lookup"><span data-stu-id="417c6-102">Control Flow in Async Programs (Visual Basic)</span></span>
<span data-ttu-id="417c6-103">`Async` キーワードと `Await` キーワードを使用すると、非同期のプログラムの作成と保守をより簡単に行えます。</span><span class="sxs-lookup"><span data-stu-id="417c6-103">You can write and maintain asynchronous programs more easily by using the `Async` and `Await` keywords.</span></span> <span data-ttu-id="417c6-104">ただし、プログラムがどのように動作するかを理解しないと、その結果は予想に反するものになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="417c6-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="417c6-105">このトピックでは、簡単な非同期プログラムによる制御フローをトレースして、制御があるメソッドから別のメソッドに移るタイミングと、その都度転送される情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="417c6-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="417c6-106">`Async` キーワードおよび `Await` キーワードは、Visual Studio 2012 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="417c6-106">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="417c6-107">一般を使用した非同期コードを含むメソッドをマークする、 [Async](../../../../visual-basic/language-reference/modifiers/async.md)修飾子です。</span><span class="sxs-lookup"><span data-stu-id="417c6-107">In general, you mark methods that contain asynchronous code with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="417c6-108">Async 修飾子でマークされているメソッドで使用することができます、 [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md)メソッドが呼び出された非同期プロセスを完了するまで待機する一時停止を指定する演算子です。</span><span class="sxs-lookup"><span data-stu-id="417c6-108">In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="417c6-109">詳細については、次を参照してください。 [Async と Await (Visual Basic) を使用した非同期プログラミング](../../../../visual-basic/programming-guide/concepts/async/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="417c6-109">For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="417c6-110">次の例では、非同期メソッドを使用して、指定した Web サイトのコンテンツを文字列としてダウンロードし、その文字列の長さを表示します。</span><span class="sxs-lookup"><span data-stu-id="417c6-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="417c6-111">この例には、次の&2; つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="417c6-111">The example contains the following two methods.</span></span>  
  
-   <span data-ttu-id="417c6-112">`startButton_Click` を呼び出して結果を表示する `AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="417c6-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>  
  
-   <span data-ttu-id="417c6-113">Web サイトのコンテンツを文字列としてダウンロードして、その文字列の長さを返す `AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="417c6-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="417c6-114">`AccessTheWebAsync`非同期を使用して<xref:System.Net.Http.HttpClient>メソッド、 <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>、コンテンツをダウンロードします</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29></xref:System.Net.Http.HttpClient>。</span><span class="sxs-lookup"><span data-stu-id="417c6-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>  
  
 <span data-ttu-id="417c6-115">番号付き表示行はプログラム全体で重要なポイントを示し、プログラムがどのように実行され、マークされている各ポイントで何が発生するかを理解するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="417c6-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="417c6-116">表示行には「1」から「6」までのラベルが付けられています。</span><span class="sxs-lookup"><span data-stu-id="417c6-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="417c6-117">このラベルは、プログラムがこれらのコード行に到達する順序を表します。</span><span class="sxs-lookup"><span data-stu-id="417c6-117">The labels represent the order in which the program reaches these lines of code.</span></span>  
  
 <span data-ttu-id="417c6-118">次のコードは、プログラムの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="417c6-118">The following code shows an outline of the program.</span></span>  
  
```vb  
Class MainWindow  
  
    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click  
  
        ' ONE  
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
  
        ' FOUR  
        Dim contentLength As Integer = Await getLengthTask  
  
        ' SIX  
        ResultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
    End Sub  
  
    Async Function AccessTheWebAsync() As Task(Of Integer)  
  
        ' TWO  
        Dim client As HttpClient = New HttpClient()   
        Dim getStringTask As Task(Of String) =   
            client.GetStringAsync("http://msdn.microsoft.com")  
  
        ' THREE  
        Dim urlContents As String = Await getStringTask  
  
        ' FIVE  
        Return urlContents.Length  
    End Function  
  
End Class  
  
```  
  
 <span data-ttu-id="417c6-119">「1」から「6」までのそれぞれのラベルの位置は、プログラムの現在の状態に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="417c6-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="417c6-120">次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="417c6-120">The following output is produced.</span></span>  
  
```  
  
ONE:   Entering startButton_Click.  
           Calling AccessTheWebAsync.  
  
TWO:   Entering AccessTheWebAsync.  
           Calling HttpClient.GetStringAsync.  
  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
  
Length of the downloaded string: 33946.  
```  
  
## <a name="set-up-the-program"></a><span data-ttu-id="417c6-121">プログラムをセットアップする</span><span class="sxs-lookup"><span data-stu-id="417c6-121">Set Up the Program</span></span>  
 <span data-ttu-id="417c6-122">このトピックで使用するコードは、MSDN からダウンロードするか、または自分でビルドできます。</span><span class="sxs-lookup"><span data-stu-id="417c6-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="417c6-123">例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 が必要または以降のコンピューターにインストールします。</span><span class="sxs-lookup"><span data-stu-id="417c6-123">To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
### <a name="download-the-program"></a><span data-ttu-id="417c6-124">プログラムをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="417c6-124">Download the Program</span></span>  
 <span data-ttu-id="417c6-125">このトピックからのアプリケーションをダウンロードする[Async サンプル: 非同期プログラムにおける制御のフロー](http://go.microsoft.com/fwlink/?LinkId=255285)します。</span><span class="sxs-lookup"><span data-stu-id="417c6-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](http://go.microsoft.com/fwlink/?LinkId=255285).</span></span> <span data-ttu-id="417c6-126">次の手順でプログラムを開いて実行します。</span><span class="sxs-lookup"><span data-stu-id="417c6-126">The following steps open and run the program.</span></span>  
  
1.  <span data-ttu-id="417c6-127">ダウンロードしたファイルを解凍し、Visual Studio を開始します。</span><span class="sxs-lookup"><span data-stu-id="417c6-127">Unzip the downloaded file, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="417c6-128">メニュー バーで **[ファイル]**、 **[開く]**、 **[プロジェクト/ソリューション]**の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="417c6-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="417c6-129">解凍したサンプル コードが含まれるフォルダーに移動し、ソリューション (.sln) ファイルを開き、F5 キーを押してプロジェクトをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="417c6-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>  
  
### <a name="build-the-program-yourself"></a><span data-ttu-id="417c6-130">プログラムを手動でビルドする</span><span class="sxs-lookup"><span data-stu-id="417c6-130">Build the Program Yourself</span></span>  
 <span data-ttu-id="417c6-131">次の Windows Presentation Foundation (WPF) プロジェクトには、このトピックのコード例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="417c6-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>  
  
 <span data-ttu-id="417c6-132">このプロジェクトを実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="417c6-132">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="417c6-133">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="417c6-133">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="417c6-134">メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="417c6-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="417c6-135">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="417c6-135">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="417c6-136">**インストールされたテンプレート** ウィンドウで、選択**Visual Basic**、にして**WPF アプリケーション**プロジェクトの種類の一覧からです。</span><span class="sxs-lookup"><span data-stu-id="417c6-136">In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="417c6-137">入力`AsyncTracer`として、プロジェクトの名前を選択し、 **ok**  ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="417c6-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="417c6-138">新しいプロジェクトに表示されます**ソリューション エクスプ ローラー**します。</span><span class="sxs-lookup"><span data-stu-id="417c6-138">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="417c6-139">Visual Studio コード エディターで、 **[MainWindow.xaml]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="417c6-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="417c6-140">タブが表示されない場合で MainWindow.xaml のショートカット メニューを開き**ソリューション エクスプ ローラー**、にして**コードの表示**します。</span><span class="sxs-lookup"><span data-stu-id="417c6-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="417c6-141">**XAML** MainWindow.xaml のビューで、コードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="417c6-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```vb  
    <Window  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="MainWindow"  
        Title="Control Flow Trace" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="221,10,0,0" VerticalAlignment="Top" Width="75"/>  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="510" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" d:LayoutOverrides="HorizontalMargin"/>  
  
        </Grid>  
    </Window>  
  
    ```  
  
     <span data-ttu-id="417c6-142">テキスト ボックスとボタンを含む簡単なウィンドウに表示、**デザイン**MainWindow.xaml のビューです。</span><span class="sxs-lookup"><span data-stu-id="417c6-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="417c6-143"><xref:System.Net.Http>。</xref:System.Net.Http>への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="417c6-143">Add a reference for <xref:System.Net.Http>.</span></span>  
  
8.  <span data-ttu-id="417c6-144">**ソリューション エクスプ ローラー**MainWindow.xaml.vb のショートカット メニューを開き、クリックして**コードの表示**します。</span><span class="sxs-lookup"><span data-stu-id="417c6-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
9. <span data-ttu-id="417c6-145">MainWindow.xaml.vb で、コードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="417c6-145">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
    ```vb  
    ' Add an Imports statement and a reference for System.Net.Http.  
    Imports System.Net.Http  
  
    Class MainWindow  
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click  
  
            ' The display lines in the example lead you through the control shifts.  
            ResultsTextBox.Text &= "ONE:   Entering StartButton_Click." & vbCrLf &  
                "           Calling AccessTheWebAsync." & vbCrLf  
  
            Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
  
            ResultsTextBox.Text &= vbCrLf & "FOUR:  Back in StartButton_Click." & vbCrLf &  
                "           Task getLengthTask is started." & vbCrLf &  
                "           About to await getLengthTask -- no caller to return to." & vbCrLf  
  
            Dim contentLength As Integer = Await getLengthTask  
  
            ResultsTextBox.Text &= vbCrLf & "SIX:   Back in StartButton_Click." & vbCrLf &  
                "           Task getLengthTask is finished." & vbCrLf &  
                "           Result from AccessTheWebAsync is stored in contentLength." & vbCrLf &  
                "           About to display contentLength and exit." & vbCrLf  
  
            ResultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
        End Sub  
  
        Async Function AccessTheWebAsync() As Task(Of Integer)  
  
            ResultsTextBox.Text &= vbCrLf & "TWO:   Entering AccessTheWebAsync."  
  
            ' Declare an HttpClient object.  
            Dim client As HttpClient = New HttpClient()  
  
            ResultsTextBox.Text &= vbCrLf & "           Calling HttpClient.GetStringAsync." & vbCrLf  
  
            ' GetStringAsync returns a Task(Of String).   
            Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
            ResultsTextBox.Text &= vbCrLf & "THREE: Back in AccessTheWebAsync." & vbCrLf &  
                "           Task getStringTask is started."  
  
            ' AccessTheWebAsync can continue to work until getStringTask is awaited.  
  
            ResultsTextBox.Text &=  
                vbCrLf & "           About to await getStringTask & return a Task(Of Integer) to StartButton_Click." & vbCrLf  
  
            ' Retrieve the website contents when task is complete.  
            Dim urlContents As String = Await getStringTask  
  
            ResultsTextBox.Text &= vbCrLf & "FIVE:  Back in AccessTheWebAsync." &  
                vbCrLf & "           Task getStringTask is complete." &  
                vbCrLf & "           Processing the return statement." &  
                vbCrLf & "           Exiting from AccessTheWebAsync." & vbCrLf  
  
            Return urlContents.Length  
        End Function  
  
    End Class  
    ```  
  
10. <span data-ttu-id="417c6-146">F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="417c6-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="417c6-147">次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="417c6-147">The following output should appear.</span></span>  
  
    ```  
    ONE:   Entering startButton_Click.  
               Calling AccessTheWebAsync.  
  
    TWO:   Entering AccessTheWebAsync.  
               Calling HttpClient.GetStringAsync.  
  
    THREE: Back in AccessTheWebAsync.  
               Task getStringTask is started.  
               About to await getStringTask & return a Task<int> to startButton_Click.  
  
    FOUR:  Back in startButton_Click.  
               Task getLengthTask is started.  
               About to await getLengthTask -- no caller to return to.  
  
    FIVE:  Back in AccessTheWebAsync.  
               Task getStringTask is complete.  
               Processing the return statement.  
               Exiting from AccessTheWebAsync.  
  
    SIX:   Back in startButton_Click.  
               Task getLengthTask is finished.  
               Result from AccessTheWebAsync is stored in contentLength.  
               About to display contentLength and exit.  
  
    Length of the downloaded string: 33946.  
    ```  
  
## <a name="trace-the-program"></a><span data-ttu-id="417c6-148">プログラムのトレース</span><span class="sxs-lookup"><span data-stu-id="417c6-148">Trace the Program</span></span>  
  
### <a name="steps-one-and-two"></a><span data-ttu-id="417c6-149">手順&1;. および&2;.</span><span class="sxs-lookup"><span data-stu-id="417c6-149">Steps ONE and TWO</span></span>  
 <span data-ttu-id="417c6-150">最初の&2; つの表示行がパスをトレースする`startButton_Click`呼び出し`AccessTheWebAsync`、および`AccessTheWebAsync`非同期<xref:System.Net.Http.HttpClient><xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>メソッド</xref:System.Net.Http.HttpClient>を呼び出す</span><span class="sxs-lookup"><span data-stu-id="417c6-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="417c6-151">次の図は、メソッドからメソッドへの呼び出しを示しています。</span><span class="sxs-lookup"><span data-stu-id="417c6-151">The following image outlines the calls from method to method.</span></span>  
  
 <span data-ttu-id="417c6-152">![手順&1;. および&2;](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")</span><span class="sxs-lookup"><span data-stu-id="417c6-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>  
  
 <span data-ttu-id="417c6-153">両方の戻り値の型`AccessTheWebAsync`と`client.GetStringAsync` <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601>は、</span><span class="sxs-lookup"><span data-stu-id="417c6-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="417c6-154">`AccessTheWebAsync` では、TResult は整数です。</span><span class="sxs-lookup"><span data-stu-id="417c6-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="417c6-155">`GetStringAsync` では、TResult は文字列です。</span><span class="sxs-lookup"><span data-stu-id="417c6-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="417c6-156">非同期メソッドの戻り値の型の詳細については、次を参照してください。 [Async を返す型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)します。</span><span class="sxs-lookup"><span data-stu-id="417c6-156">For more information about async method return types, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
 <span data-ttu-id="417c6-157">タスクを返す非同期のメソッドは、制御が呼び出し元に戻ると、タスク インスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="417c6-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="417c6-158">呼び出し元に、非同期メソッドから制御が戻りますいずれかの場合、`Await`演算子が呼び出されたメソッドまたは呼び出されたメソッドが終了した場合に検出されました。</span><span class="sxs-lookup"><span data-stu-id="417c6-158">Control returns from an async method to its caller either when an `Await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="417c6-159">「3」から「6」のラベルの付いた表示行はこのプロセスの部分をトレースします。</span><span class="sxs-lookup"><span data-stu-id="417c6-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>  
  
### <a name="step-three"></a><span data-ttu-id="417c6-160">手順&3;.</span><span class="sxs-lookup"><span data-stu-id="417c6-160">Step THREE</span></span>  
 <span data-ttu-id="417c6-161">`AccessTheWebAsync`、非同期メソッド<xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>対象 web ページのコンテンツをダウンロードするために呼び出される</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>。</span><span class="sxs-lookup"><span data-stu-id="417c6-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="417c6-162">`client.GetStringAsync` が制御を返すと、`AccessTheWebAsync` から `client.GetStringAsync` に制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="417c6-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>  
  
 <span data-ttu-id="417c6-163">`client.GetStringAsync` メソッドは、`getStringTask` の `AccessTheWebAsync` 変数に割り当てる文字列のタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="417c6-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="417c6-164">プログラム例の次の行は、`client.GetStringAsync` の呼び出しと割り当てを示しています。</span><span class="sxs-lookup"><span data-stu-id="417c6-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>  
  
<span data-ttu-id="417c6-165"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="417c6-165"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="417c6-166">このタスクは `client.GetStringAsync` により実際の文字列が最終的に生成される約束と見なすことができます。</span><span class="sxs-lookup"><span data-stu-id="417c6-166">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="417c6-167">`AccessTheWebAsync` には `client.GetStringAsync` から約束された文字列に依存しない処理がある場合、その処理は `client.GetStringAsync` を待機している間は、続行できます。</span><span class="sxs-lookup"><span data-stu-id="417c6-167">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="417c6-168">この例では、「3」のラベルの付いた行の出力は、独立した処理を行う機会を表します。</span><span class="sxs-lookup"><span data-stu-id="417c6-168">In the example, the following lines of output, which are labeled "THREE,” represent the opportunity to do independent work</span></span>  
  
<span data-ttu-id="417c6-169"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="417c6-169"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="417c6-170">次のステートメントは `AccessTheWebAsync` が待機中の場合 `getStringTask` の進行を中断します。</span><span class="sxs-lookup"><span data-stu-id="417c6-170">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>  
  
<span data-ttu-id="417c6-171"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="417c6-171"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="417c6-172">次の図は、コントロールからのフローを示しています。`client.GetStringAsync`への割り当てへ`getStringTask`との作成から`getStringTask`Await 演算子のアプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="417c6-172">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.</span></span>  
  
 <span data-ttu-id="417c6-173">![ステップ&3;](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace&3;")</span><span class="sxs-lookup"><span data-stu-id="417c6-173">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>  
  
 <span data-ttu-id="417c6-174">await 式は `AccessTheWebAsync` が制御を返すまで `client.GetStringAsync` を中断します。</span><span class="sxs-lookup"><span data-stu-id="417c6-174">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="417c6-175">その間、コントロールは `AccessTheWebAsync` の呼び出し元である `startButton_Click` に戻されます。</span><span class="sxs-lookup"><span data-stu-id="417c6-175">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="417c6-176">通常、直ちに非同期メソッドへの呼び出しの待機状態となります。</span><span class="sxs-lookup"><span data-stu-id="417c6-176">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="417c6-177">たとえば、次の割り当てで作成し、それを待機する前のコードを置き換えられます`getStringTask`:`Dim urlContents As String = Await client.GetStringAsync("http://msdn.microsoft.com")`</span><span class="sxs-lookup"><span data-stu-id="417c6-177">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("http://msdn.microsoft.com")`</span></span>  
>   
>  <span data-ttu-id="417c6-178">このトピックでは、await 演算子が後で適用され、プログラムでの制御フローを示す出力行を格納します。</span><span class="sxs-lookup"><span data-stu-id="417c6-178">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>  
  
### <a name="step-four"></a><span data-ttu-id="417c6-179">手順&4;.</span><span class="sxs-lookup"><span data-stu-id="417c6-179">Step FOUR</span></span>  
 <span data-ttu-id="417c6-180">戻り値の型の宣言、`AccessTheWebAsync`は`Task(Of Integer)`です。</span><span class="sxs-lookup"><span data-stu-id="417c6-180">The declared return type of `AccessTheWebAsync` is `Task(Of Integer)`.</span></span> <span data-ttu-id="417c6-181">したがって、`AccessTheWebAsync` が中断されると、`startButton_Click` に整数のタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="417c6-181">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="417c6-182">返されたタスクは `getStringTask` ではないことに注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="417c6-182">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="417c6-183">返されたタスクは、中断されたメソッド `AccessTheWebAsync` での未処理を表す、整数の新しいタスクです。</span><span class="sxs-lookup"><span data-stu-id="417c6-183">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="417c6-184">これにより、タスクが完了したときに `AccessTheWebAsync` が整数を生成することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="417c6-184">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>  
  
 <span data-ttu-id="417c6-185">次のステートメントはこのタスクを `getLengthTask` 変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="417c6-185">The following statement assigns this task to the `getLengthTask` variable.</span></span>  
  
<span data-ttu-id="417c6-186"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="417c6-186"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="417c6-187">`AccessTheWebAsync` と同様に、`startButton_Click` は、非同期タスク (`getLengthTask`) の結果に依存しない処理を、タスクが待機するまで続行できます。</span><span class="sxs-lookup"><span data-stu-id="417c6-187">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="417c6-188">次の出力行はその処理を表します。</span><span class="sxs-lookup"><span data-stu-id="417c6-188">The following output lines represent that work.</span></span>  
  
<span data-ttu-id="417c6-189"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="417c6-189"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="417c6-190">`startButton_Click` が待機すると、`getLengthTask` の進行は中断します。</span><span class="sxs-lookup"><span data-stu-id="417c6-190">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="417c6-191">次の代入ステートメントは、`startButton_Click` が完了するまで `AccessTheWebAsync` を中断します。</span><span class="sxs-lookup"><span data-stu-id="417c6-191">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>  
  
<span data-ttu-id="417c6-192"><CodeContentPlaceHolder>10</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="417c6-192"><CodeContentPlaceHolder>10</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="417c6-193">次の図で、矢印は `AccessTheWebAsync` の await 式から `getLengthTask` への値の割り当てへの制御のフロー、および `startButton_Click` が待機するまでの `getLengthTask` の通常の処理を示しています。</span><span class="sxs-lookup"><span data-stu-id="417c6-193">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>  
  
 <span data-ttu-id="417c6-194">![ステップ&4;](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace&4;")</span><span class="sxs-lookup"><span data-stu-id="417c6-194">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>  
  
### <a name="step-five"></a><span data-ttu-id="417c6-195">手順&5;.</span><span class="sxs-lookup"><span data-stu-id="417c6-195">Step FIVE</span></span>  
 <span data-ttu-id="417c6-196">`client.GetStringAsync` が終了を通知すると、`AccessTheWebAsync` の処理は中断から解放され、await ステートメントを越えて続行できます。</span><span class="sxs-lookup"><span data-stu-id="417c6-196">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="417c6-197">次の出力行は、処理の再開を表します。</span><span class="sxs-lookup"><span data-stu-id="417c6-197">The following lines of output represent the resumption of processing.</span></span>  
  
<span data-ttu-id="417c6-198"><CodeContentPlaceHolder>11</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="417c6-198"><CodeContentPlaceHolder>11</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="417c6-199">return ステートメントのオペランド `urlContents.Length` は `AccessTheWebAsync` が返すタスクに格納されます。</span><span class="sxs-lookup"><span data-stu-id="417c6-199">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="417c6-200">await 式はその値を `getLengthTask` の `startButton_Click` から取得します。</span><span class="sxs-lookup"><span data-stu-id="417c6-200">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>  
  
 <span data-ttu-id="417c6-201">次の図は、`client.GetStringAsync` (および `getStringTask`) が完了した後の制御の移動を示します。</span><span class="sxs-lookup"><span data-stu-id="417c6-201">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>  
  
 <span data-ttu-id="417c6-202">![ステップ&5;](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace&5;")</span><span class="sxs-lookup"><span data-stu-id="417c6-202">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>  
  
 <span data-ttu-id="417c6-203">`AccessTheWebAsync` は完了するまで実行され、完了を待機していた `startButton_Click` に制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="417c6-203">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>  
  
### <a name="step-six"></a><span data-ttu-id="417c6-204">手順&6;.</span><span class="sxs-lookup"><span data-stu-id="417c6-204">Step SIX</span></span>  
 <span data-ttu-id="417c6-205">`AccessTheWebAsync` が終了を通知すると、処理は `startButton_Async` の await ステートメントを越えて続行できます。</span><span class="sxs-lookup"><span data-stu-id="417c6-205">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="417c6-206">実際、プログラムはそれ以上行うことがありません。</span><span class="sxs-lookup"><span data-stu-id="417c6-206">In fact, the program has nothing more to do.</span></span>  
  
 <span data-ttu-id="417c6-207">次の出力行は、`startButton_Async` の処理の再開を表します。</span><span class="sxs-lookup"><span data-stu-id="417c6-207">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>  
  
<span data-ttu-id="417c6-208"><CodeContentPlaceHolder>12</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="417c6-208"><CodeContentPlaceHolder>12</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="417c6-209">await 式は `getLengthTask` から `AccessTheWebAsync` の return ステートメントのオペランドである整数値を取得します。</span><span class="sxs-lookup"><span data-stu-id="417c6-209">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="417c6-210">次のステートメントはその値を `contentLength` 変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="417c6-210">The following statement assigns that value to the `contentLength` variable.</span></span>  
  
<span data-ttu-id="417c6-211"><CodeContentPlaceHolder>13</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="417c6-211"><CodeContentPlaceHolder>13</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="417c6-212">次の図は `AccessTheWebAsync` から `startButton_Click` に制御が戻ることを示しています。</span><span class="sxs-lookup"><span data-stu-id="417c6-212">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>  
  
 <span data-ttu-id="417c6-213">![ステップ&6;](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace&6;")</span><span class="sxs-lookup"><span data-stu-id="417c6-213">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="417c6-214">関連項目</span><span class="sxs-lookup"><span data-stu-id="417c6-214">See Also</span></span>  
 <span data-ttu-id="417c6-215">[非同期プログラミングを Async と Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="417c6-215">[Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="417c6-216"> [非同期の戻り値の型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span><span class="sxs-lookup"><span data-stu-id="417c6-216"> [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span></span>  
<span data-ttu-id="417c6-217"> [チュートリアル: Async を使用して Web へのアクセスと Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="417c6-217"> [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="417c6-218"> [(C# および Visual Basic)、非同期プログラムにおける制御フローの非同期のサンプル:](http://go.microsoft.com/fwlink/?LinkId=255285)</span><span class="sxs-lookup"><span data-stu-id="417c6-218"> [Async Sample: Control Flow in Async Programs (C# and Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255285)</span></span>
