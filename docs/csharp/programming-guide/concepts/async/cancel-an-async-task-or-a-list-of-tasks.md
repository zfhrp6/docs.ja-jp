---
title: "非同期タスクまたはタスクの一覧のキャンセル (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 61f1ac22923ad637ba145b448f75e0f1a7e142b6
ms.lasthandoff: 03/13/2017

---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a>非同期タスクまたはタスクの一覧のキャンセル (C#)
非同期のアプリケーションが終了するまで待機しない場合、それを取り消すために使用できるボタンを設定できます。 このトピックの例に従うと、1 つの Web サイトのコンテンツまたは Web サイトのリストをダウンロードするアプリケーションにキャンセル ボタンを追加できます。  
  
 例では、「[非同期アプリケーションの微調整 (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)」で説明している UI を使用しています。  
  
> [!NOTE]
>  この例を実行するには、Visual Studio 2012 以降および .NET Framework 4.5 以降が、コンピューターにインストールされている必要があります。  
  
##  <a name="BKMK_CancelaTask"></a>タスクのキャンセル  
 最初の例では、**キャンセル** ボタンを単一のダウンロード タスクと関連付けます。 アプリケーションがコンテンツをダウンロード中にボタンをクリックすると、ダウンロードは取り消されます。  
  
### <a name="downloading-the-example"></a>例をダウンロードする  
 完全な Windows Presentation Foundation (WPF) プロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](http://go.microsoft.com/fwlink/?LinkId=255046)」からダウンロードできます。ダウンロード後、次の手順に従います。  
  
1.  ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。  
  
2.  メニュー バーで **[ファイル]**、 **[開く]**、 **[プロジェクト/ソリューション]**の順に選択します。  
  
3.  **[プロジェクトを開く]** ダイアログ ボックスで、圧縮解除したサンプル コードを含むフォルダーを開き、AsyncFineTuningCS のソリューション (.sln) ファイルを開きます。  
  
4.  **ソリューション エクスプローラー**で、**CancelATask** プロジェクトのショートカット メニューを開き、**[スタートアップ プロジェクトに設定]** をクリックします。  
  
5.  F5 キーを押してプロジェクトを実行します。  
  
     Ctrl + F5 キーを押して、デバッグを行わずにプロジェクトを実行します。  
  
 プロジェクトをダウンロードしない場合は、このトピックの最後の MainWindow.xaml.cs ファイルをレビューできます。  
  
### <a name="building-the-example"></a>例のビルド  
 次の変更は、Web サイトをダウンロードするアプリケーションに**キャンセル** ボタンを追加します。 この例のダウンロードまたはビルドをしない場合は、このトピックの最後にある「コード例全体」のセクションで最終製品をレビューできます。 アスタリスクはコードの変更点を示しています。  
  
 この例を自分でビルドするには、「例をダウンロードする」のセクションの詳細な手順の指示に従いますが、**[スタートアップ プロジェクト]** として、**[CancelATask]** の代わりに **[StarterCode]** を選択します。  
  
 次の変更点をプロジェクトの MainWindow.xaml.cs ファイルに追加します。  
  
1.  アクセスするすべてのメソッドのスコープである `CancellationTokenSource` 変数、`cts` を宣言します。  
  
    ```cs  
    public partial class MainWindow : Window  
    {  
        // ***Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  次のような**キャンセル** ボタンのイベント ハンドラーのコードを追加します。 ユーザーからキャンセルの要求があると、イベント ハンドラーは <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName> メソッドを使用して `cts` に通知します。  
  
    ```cs  
    // ***Add an event handler for the Cancel button.  
    private void cancelButton_Click(object sender, RoutedEventArgs e)  
    {  
        if (cts != null)  
        {  
            cts.Cancel();  
        }  
    }  
    ```  
  
3.  **開始**ボタン `startButton_Click` のためのイベント ハンドラーに次の変更を行います。  
  
    -   `CancellationTokenSource`、`cts` をインスタンス化します。  
  
        ```cs  
        // ***Instantiate the CancellationTokenSource.  
        cts = new CancellationTokenSource();  
        ```  
  
    -   指定した Web サイトのコンテンツをダウンロードする `AccessTheWebAsync` への呼び出しで、`cts` の <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=fullName> プロパティを引数として送信します。 取り消しが要求されると、`Token` プロパティがメッセージを伝達します。 ユーザーがダウンロード操作の取り消しを選択するとメッセージを表示する catch ブロックを追加します。 次のコードは変更点を示しています。  
  
        ```cs  
        try  
        {  
            // ***Send a token to carry the message if cancellation is requested.  
            int contentLength = await AccessTheWebAsync(cts.Token);  
            resultsTextBox.Text +=  
                String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
        }  
        // *** If cancellation is requested, an OperationCanceledException results.  
        catch (OperationCanceledException)  
        {  
            resultsTextBox.Text += "\r\nDownload canceled.\r\n";  
        }  
        catch (Exception)  
        {  
            resultsTextBox.Text += "\r\nDownload failed.\r\n";  
        }  
        ```  
  
4.  `AccessTheWebAsync` で、<xref:System.Net.Http.HttpClient> 型の `GetAsync` メソッドの <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=fullName> オーバーロードを使用して、Web サイトのコンテンツをダウンロードします。 `AccessTheWebAsync` の <xref:System.Threading.CancellationToken> パラメーター `ct`を 2 番目の引数として渡します。 ユーザーが**キャンセル** ボタンをクリックすると、トークンがメッセージを送信します。  
  
     次のコードは、`AccessTheWebAsync` の変更点を示しています。  
  
    ```cs  
    // ***Provide a parameter for the CancellationToken.  
    async Task<int> AccessTheWebAsync(CancellationToken ct)  
    {  
        HttpClient client = new HttpClient();  
  
        resultsTextBox.Text +=  
            String.Format("\r\nReady to download.\r\n");  
  
        // You might need to slow things down to have a chance to cancel.  
        await Task.Delay(250);  
  
        // GetAsync returns a Task<HttpResponseMessage>.   
        // ***The ct argument carries the message if the Cancel button is chosen.  
        HttpResponseMessage response = await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct);  
  
        // Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        // The result of the method is the length of the downloaded website.  
        return urlContents.Length;  
    }  
    ```  
  
5.  プログラムの取り消しをしない場合、次の出力を生成します。  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     プログラムがコンテンツのダウンロードを終了する前に**キャンセル** ボタンをクリックすると、プログラムは次の出力を生成します。  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <a name="BKMK_CancelaListofTasks"></a>タスクの一覧を取り消す  
 前の例を拡張すると、同じ `CancellationTokenSource` のインスタンスを各タスクに関連付けることによって、多数のタスクを取り消すことができます。 **キャンセル** ボタンをクリックすると、完了していないすべてのタスクを取り消します。  
  
### <a name="downloading-the-example"></a>例をダウンロードする  
 完全な Windows Presentation Foundation (WPF) プロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](http://go.microsoft.com/fwlink/?LinkId=255046)」からダウンロードできます。ダウンロード後、次の手順に従います。  
  
1.  ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。  
  
2.  メニュー バーで **[ファイル]**、 **[開く]**、 **[プロジェクト/ソリューション]**の順に選択します。  
  
3.  **[プロジェクトを開く]** ダイアログ ボックスで、圧縮解除したサンプル コードを含むフォルダーを開き、AsyncFineTuningCS のソリューション (.sln) ファイルを開きます。  
  
4.  **ソリューション エクスプローラー**で、**CancelAListOfTasks** プロジェクトのショートカット メニューを開き、**[スタートアップ プロジェクトに設定]** をクリックします。  
  
5.  F5 キーを押してプロジェクトを実行します。  
  
     Ctrl + F5 キーを押して、デバッグを行わずにプロジェクトを実行します。  
  
 プロジェクトをダウンロードしない場合は、このトピックの最後の MainWindow.xaml.cs ファイルをレビューできます。  
  
### <a name="building-the-example"></a>例のビルド  
 この例を自分で拡張するには、「例をダウンロードする」のセクションの詳細な手順の指示に従いますが、**[スタートアップ プロジェクト]** として **CancelATask** を選択します。 次の変更点をプロジェクトに追加します。 アスタリスクはプログラムの変更点を示しています。  
  
1.  Web アドレスのリストを作成するメソッドを追加します。  
  
    ```cs  
    // ***Add a method that creates a list of web addresses.  
    private List<string> SetUpURLList()  
    {  
        List<string> urls = new List<string>   
        {   
            "http://msdn.microsoft.com",  
            "http://msdn.microsoft.com/library/hh290138.aspx",  
            "http://msdn.microsoft.com/library/hh290140.aspx",  
            "http://msdn.microsoft.com/library/dd470362.aspx",  
            "http://msdn.microsoft.com/library/aa578028.aspx",  
            "http://msdn.microsoft.com/library/ms404677.aspx",  
            "http://msdn.microsoft.com/library/ff730837.aspx"  
        };  
        return urls;  
    }  
    ```  
  
2.  `AccessTheWebAsync` のメソッドを呼び出します。  
  
    ```cs  
    // ***Call SetUpURLList to make a list of web addresses.  
    List<string> urlList = SetUpURLList();  
    ```  
  
3.  次のループを `AccessTheWebAsync` に追加して、リストの各 Web アドレスを処理します。  
  
    ```cs  
    // ***Add a loop to process the list of web addresses.  
    foreach (var url in urlList)  
    {  
        // GetAsync returns a Task<HttpResponseMessage>.   
        // Argument ct carries the message if the Cancel button is chosen.   
        // ***Note that the Cancel button can cancel all remaining downloads.  
        HttpResponseMessage response = await client.GetAsync(url, ct);  
  
        // Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        resultsTextBox.Text +=  
            String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
    }  
    ```  
  
4.  `AccessTheWebAsync` は長さを表示するため、メソッドは何も返す必要はありません。 return ステートメントを削除し、メソッドの戻り値の型を <xref:System.Threading.Tasks.Task%601> ではなく <xref:System.Threading.Tasks.Task> に変更します。  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
     式の代わりにステートメントを使って、`startButton_Click` からメソッドを呼び出します。  
  
    ```cs  
    await AccessTheWebAsync(cts.Token);  
    ```  
  
5.  プログラムの取り消しをしない場合、次の出力を生成します。  
  
    ```  
  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Length of the downloaded string: 158124.  
  
    Length of the downloaded string: 204890.  
  
    Length of the downloaded string: 175488.  
  
    Length of the downloaded string: 145790.  
  
    Downloads complete.  
  
    ```  
  
     ダウンロードが完了する前に**キャンセル** ボタンをクリックすると、出力には取り消しの前に完了したダウンロードの長さが含まれています。  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
  
    ```  
  
##  <a name="BKMK_CompleteExamples"></a>コード例全体  
 次のセクションには、前の例の各コードが含まれています。 <xref:System.Net.Http> の参照を追加する必要があることに注意してください。  
  
 このプロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](http://go.microsoft.com/fwlink/?LinkId=255046)」からダウンロードできます。  
  
### <a name="cancel-a-task-example"></a>タスクを取り消す例  
 次のコードは、単一のタスクを取り消す例での MainWindow.xaml.cs ファイルの全体です。  
  
```cs  
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
  
// Add the following using directive for System.Threading.  
  
using System.Threading;  
namespace CancelATask  
{  
    public partial class MainWindow : Window  
    {  
        // ***Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // ***Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            resultsTextBox.Clear();  
  
            try  
            {  
                // ***Send a token to carry the message if cancellation is requested.  
                int contentLength = await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text +=  
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
            }  
            // *** If cancellation is requested, an OperationCanceledException results.  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownload canceled.\r\n";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownload failed.\r\n";  
            }  
  
            // ***Set the CancellationTokenSource to null when the download is complete.  
            cts = null;   
        }  
  
        // ***Add an event handler for the Cancel button.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // ***Provide a parameter for the CancellationToken.  
        async Task<int> AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            resultsTextBox.Text +=  
                String.Format("\r\nReady to download.\r\n");  
  
            // You might need to slow things down to have a chance to cancel.  
            await Task.Delay(250);  
  
            // GetAsync returns a Task<HttpResponseMessage>.   
            // ***The ct argument carries the message if the Cancel button is chosen.  
            HttpResponseMessage response = await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            // The result of the method is the length of the downloaded website.  
            return urlContents.Length;  
        }  
    }  
  
    // Output for a successful download:  
  
    // Ready to download.  
  
    // Length of the downloaded string: 158125.  
  
    // Or, if you cancel:  
  
    // Ready to download.  
  
    // Download canceled.  
}  
```  
  
### <a name="cancel-a-list-of-tasks-example"></a>タスクの一覧を取り消す例  
 次のコードは、タスクの一覧を取り消す例での MainWindow.xaml.cs ファイルの全体です。  
  
```cs  
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
  
// Add the following using directive for System.Threading.  
using System.Threading;  
  
namespace CancelAListOfTasks  
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
                await AccessTheWebAsync(cts.Token);  
                // ***Small change in the display lines.  
                resultsTextBox.Text += "\r\nDownloads complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownloads canceled.";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownloads failed.";  
            }  
  
            // Set the CancellationTokenSource to null when the download is complete.  
            cts = null;  
        }  
  
        // Add an event handler for the Cancel button.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // Provide a parameter for the CancellationToken.  
        // ***Change the return type to Task because the method has no return statement.  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            // Declare an HttpClient object.  
            HttpClient client = new HttpClient();  
  
            // ***Call SetUpURLList to make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Add a loop to process the list of web addresses.  
            foreach (var url in urlList)  
            {  
                // GetAsync returns a Task<HttpResponseMessage>.   
                // Argument ct carries the message if the Cancel button is chosen.   
                // ***Note that the Cancel button can cancel all remaining downloads.  
                HttpResponseMessage response = await client.GetAsync(url, ct);  
  
                // Retrieve the website contents from the HttpResponseMessage.  
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
                resultsTextBox.Text +=  
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
            }  
        }  
  
        // ***Add a method that creates a list of web addresses.  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
    }  
  
    // Output if you do not choose to cancel:  
  
    //Length of the downloaded string: 35939.  
  
    //Length of the downloaded string: 237682.  
  
    //Length of the downloaded string: 128607.  
  
    //Length of the downloaded string: 158124.  
  
    //Length of the downloaded string: 204890.  
  
    //Length of the downloaded string: 175488.  
  
    //Length of the downloaded string: 145790.  
  
    //Downloads complete.  
  
    // Sample output if you choose to cancel:  
  
    //Length of the downloaded string: 35939.  
  
    //Length of the downloaded string: 237682.  
  
    //Length of the downloaded string: 128607.  
  
    //Downloads canceled.  
}  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.CancellationTokenSource>   
 <xref:System.Threading.CancellationToken>   
 [Async および Await を使用した非同期プログラミング (C#)](../../../../csharp/programming-guide/concepts/async/index.md)   
 [非同期アプリケーションの微調整 (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)   
 [非同期のサンプル: アプリケーションの微調整](http://go.microsoft.com/fwlink/?LinkId=255046)
