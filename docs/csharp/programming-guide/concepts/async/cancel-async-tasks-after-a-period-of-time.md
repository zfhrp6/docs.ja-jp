---
title: "指定した時間の経過後の非同期タスクのキャンセル (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eca4b411f8d8151b18c7e83be15191a843e628b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="a7619-102">指定した時間の経過後の非同期タスクのキャンセル (C#)</span><span class="sxs-lookup"><span data-stu-id="a7619-102">Cancel Async Tasks after a Period of Time (C#)</span></span>
<span data-ttu-id="a7619-103"><xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> メソッドを使用すると、一定の時間が過ぎた後に非同期操作が完了するまで待たない場合に、その操作を取り消しできます。</span><span class="sxs-lookup"><span data-stu-id="a7619-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="a7619-104">このメソッドは、`CancelAfter` 式によって指定された時間内に完了しない、関連付けられたタスクの取り消しをスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="a7619-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>  
  
 <span data-ttu-id="a7619-105">この例では、「[タスクまたはタスクの一覧のキャンセル (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)」で開発したコードに追加して、Web サイトの一覧をダウンロードして各サイトのコンテンツの長さを表示します。</span><span class="sxs-lookup"><span data-stu-id="a7619-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7619-106">この例を実行するには、Visual Studio 2012 以降および .NET Framework 4.5 以降が、コンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7619-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="a7619-107">例をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="a7619-107">Downloading the Example</span></span>  
 <span data-ttu-id="a7619-108">完全な Windows Presentation Foundation (WPF) プロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](http://go.microsoft.com/fwlink/?LinkId=255046)」からダウンロードできます。ダウンロード後、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a7619-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="a7619-109">ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="a7619-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="a7619-110">メニュー バーで **[ファイル]**、 **[開く]**、 **[プロジェクト/ソリューション]**の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="a7619-110">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="a7619-111">**[プロジェクトを開く]** ダイアログ ボックスで、圧縮解除したサンプル コードを含むフォルダーを開き、AsyncFineTuningCS のソリューション (.sln) ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="a7619-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="a7619-112">**ソリューション エクスプローラー**で、**CancelAfterTime** プロジェクトのショートカット メニューを開き、**[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7619-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="a7619-113">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="a7619-113">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="a7619-114">Ctrl + F5 キーを押して、デバッグを行わずにプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="a7619-114">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="a7619-115">プログラムを複数回実行して、出力がすべての Web サイトの出力を示したり、どの Web サイトの出力も示さなかったり、一部の Web サイトの出力を示したりすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a7619-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>  
  
 <span data-ttu-id="a7619-116">プロジェクトをダウンロードしない場合は、このトピックの最後の MainWindow.xaml.cs ファイルをレビューできます。</span><span class="sxs-lookup"><span data-stu-id="a7619-116">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="a7619-117">例のビルド</span><span class="sxs-lookup"><span data-stu-id="a7619-117">Building the Example</span></span>  
 <span data-ttu-id="a7619-118">このトピックの例では、「[非同期タスクまたはタスクの一覧のキャンセル (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)」で開発したプロジェクトに追加して、タスクのリストをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="a7619-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="a7619-119">この例では、**[キャンセル]** ボタンは明示的に使用していませんが、同じ UI を使用します。</span><span class="sxs-lookup"><span data-stu-id="a7619-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="a7619-120">この例を自分で 1 つずつビルドするには、"例をダウンロードする" セクションの手順に従います。ただし、**[スタートアップ プロジェクト]** として **CancelAListOfTasks** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a7619-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="a7619-121">そのプロジェクトに、このトピックでの変更を追加します。</span><span class="sxs-lookup"><span data-stu-id="a7619-121">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="a7619-122">次の例に示すように、タスクが取り消し済みとマークされるまでの最大時間を指定するには、`CancelAfter` に `startButton_Click` への呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="a7619-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="a7619-123">追加部分にはアスタリスクが付いています。</span><span class="sxs-lookup"><span data-stu-id="a7619-123">The addition is marked with asterisks.</span></span>  
  
```csharp  
private async void startButton_Click(object sender, RoutedEventArgs e)  
{  
    // Instantiate the CancellationTokenSource.  
    cts = new CancellationTokenSource();  
  
    resultsTextBox.Clear();  
  
    try  
    {  
        // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You  
        // can adjust the time.)  
        cts.CancelAfter(2500);  
  
        await AccessTheWebAsync(cts.Token);  
        resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";  
    }  
    catch (OperationCanceledException)  
    {  
        resultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
    }  
    catch (Exception)  
    {  
        resultsTextBox.Text += "\r\nDownloads failed.\r\n";  
    }  
  
    cts = null;   
}  
```  
  
 <span data-ttu-id="a7619-124">プログラムを複数回実行して、出力がすべての Web サイトの出力を示したり、どの Web サイトの出力も示さなかったり、一部の Web サイトの出力を示したりすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a7619-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="a7619-125">出力例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a7619-125">The following output is a sample.</span></span>  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a><span data-ttu-id="a7619-126">コード例全体</span><span class="sxs-lookup"><span data-stu-id="a7619-126">Complete Example</span></span>  
 <span data-ttu-id="a7619-127">次のコードは、この例での MainWindow.xaml.cs ファイルのテキスト全体です。</span><span class="sxs-lookup"><span data-stu-id="a7619-127">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="a7619-128">アスタリスクはこの例のために追加された要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="a7619-128">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="a7619-129"><xref:System.Net.Http> の参照を追加する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7619-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="a7619-130">このプロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](http://go.microsoft.com/fwlink/?LinkId=255046)」からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="a7619-130">You can download the project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
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
  
// Add a using directive and a reference for System.Net.Http.  
using System.Net.Http;  
  
// Add the following using directive.  
using System.Threading;  
  
namespace CancelAfterTime  
{  
    public partial class MainWindow : Window  
    {  
        // Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            resultsTextBox.Clear();  
  
            try  
            {  
                // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You  
                // can adjust the time.)  
                cts.CancelAfter(2500);  
  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";  
            }  
  
            cts = null;   
        }  
  
        // You can still include a Cancel button if you want to.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            // Declare an HttpClient object.  
            HttpClient client = new HttpClient();  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            foreach (var url in urlList)  
            {  
                // GetAsync returns a Task<HttpResponseMessage>.   
                // Argument ct carries the message if the Cancel button is chosen.   
                // Note that the Cancel button cancels all remaining downloads.  
                HttpResponseMessage response = await client.GetAsync(url, ct);  
  
                // Retrieve the website contents from the HttpResponseMessage.  
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
                resultsTextBox.Text +=  
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
            }  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
    }  
  
    // Sample Output:  
  
    // Length of the downloaded string: 35990.  
  
    // Length of the downloaded string: 407399.  
  
    // Length of the downloaded string: 226091.  
  
    // Downloads canceled.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7619-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7619-131">See Also</span></span>  
 [<span data-ttu-id="a7619-132">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="a7619-132">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="a7619-133">チュートリアル: async と await を使用した Web へのアクセス (C#)</span><span class="sxs-lookup"><span data-stu-id="a7619-133">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="a7619-134">非同期タスクまたはタスク (c#) の一覧をキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="a7619-134">Cancel an Async Task or a List of Tasks (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)  
 [<span data-ttu-id="a7619-135">非同期アプリケーションの微調整 (C#)</span><span class="sxs-lookup"><span data-stu-id="a7619-135">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="a7619-136">非同期のサンプル: アプリケーションの微調整</span><span class="sxs-lookup"><span data-stu-id="a7619-136">Async Sample: Fine Tuning Your Application</span></span>](http://go.microsoft.com/fwlink/?LinkId=255046)
