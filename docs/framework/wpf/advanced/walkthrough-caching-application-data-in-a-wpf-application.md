---
title: 'チュートリアル: WPF アプリケーション内のアプリケーション データのキャッシュ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: 7a4f84281da78068b5c6f7a505c8cb9225b31a39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>チュートリアル: WPF アプリケーション内のアプリケーション データのキャッシュ
キャッシュを使用すると、メモリにデータを格納して高速にアクセスできます。 データを再度アクセスすると、アプリケーションは、代わりに、元のソースから取得するキャッシュからデータを取得できます。 そのため、パフォーマンスとスケーラビリティが向上します。 また、データ ソースが一時的に使用できない場合でも、キャッシュのデータを使用できます。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]でのキャッシュを使用するためのクラスを提供[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アプリケーションです。 これらのクラスにある、<xref:System.Runtime.Caching>名前空間。  
  
> [!NOTE]
>  <xref:System.Runtime.Caching>名前空間はの新機能、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。 この名前空間は、キャッシュは、すべて使用できる[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アプリケーションです。 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の以前のバージョンでは、キャッシュは <xref:System.Web> 名前空間でのみ使用可能だったため、ASP.NET クラスへの依存が必要でした。  
  
 このチュートリアルで使用可能なキャッシュの機能を使用する方法、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]の一部として、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーションです。 このチュートリアルでは、テキスト ファイルの内容をキャッシュします。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   WPF アプリケーション プロジェクトを作成します。  
  
-   参照を追加する、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
-   キャッシュを初期化します。  
  
-   テキスト ファイルの内容を格納するキャッシュ エントリを追加します。  
  
-   キャッシュ エントリの削除ポリシーを提供します。  
  
-   キャッシュされたファイルのパスの監視と通知する、キャッシュ インスタンスは、監視対象のアイテムを変更します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]。  
  
-   少量のテキストを含むテキスト ファイル。 (テキスト ファイルの内容は、メッセージ ボックスに表示されます)。このチュートリアルで示すコードでは、次のファイルを使用することを前提としています。  
  
     `c:\cache\cacheText.txt`  
  
     ただし、テキスト ファイルを使用し、このチュートリアルのコードに小さな変更を加えることができます。  
  
## <a name="creating-a-wpf-application-project"></a>WPF アプリケーション プロジェクトを作成します。  
 WPF アプリケーション プロジェクトを作成することで始めます。  
  
#### <a name="to-create-a-wpf-application"></a>WPF アプリケーションを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **ファイル** メニューのをクリックして**新規**、クリックして**新しいプロジェクト**です。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  **インストールされたテンプレート**、使用するプログラミング言語を選択 (**Visual Basic**または**Visual c#**)。  
  
4.  **新しいプロジェクト**ダイアログ ボックスで、 **WPF アプリケーション**です。  
  
    > [!NOTE]
    >  表示されない場合、 **WPF アプリケーション**テンプレートのバージョンを対象にすることを確認してください、 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] WPF をサポートします。 **新しいプロジェクト**ダイアログ ボックスで、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]一覧からです。  
  
5.  **名前**テキスト ボックスに、プロジェクトの名前を入力します。 たとえば、入力**WPFCaching**です。  
  
6.  選択、**ソリューションのディレクトリを作成**チェック ボックスをオンします。  
  
7.  **[OK]** をクリックします。  
  
     WPF デザイナーで開きます**デザイン**を表示し、MainWindow.xaml ファイルを表示します。 Visual Studio によって作成、 **My Project**フォルダー、Application.xaml ファイル、および、MainWindow.xaml ファイル。  
  
## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>.NET Framework を対象として、キャッシュのアセンブリへの参照を追加します。  
 既定では、WPF アプリケーションのターゲット、[!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]です。 使用する、 <xref:System.Runtime.Caching> WPF アプリケーションの名前空間は、アプリケーションを対象にする、 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (されません、 [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) 名前空間への参照を含める必要があります。  
  
 したがって、次の手順は、.NET Framework のターゲットを変更しへの参照を追加、<xref:System.Runtime.Caching>名前空間。  
  
> [!NOTE]
>  .NET Framework のターゲットを変更する手順は Visual c# プロジェクトおよび Visual Basic プロジェクトでは異なります。  
  
#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>Visual Basic での .NET Framework のターゲットを変更するには  
  
1.  **ソリューション エクスプ ローラー**プロジェクト名を右クリックし、クリックして**プロパティ**です。  
  
     アプリケーションのプロパティ ウィンドウが表示されます。  
  
2.  **[コンパイル]** タブをクリックします。  
  
3.  ウィンドウの下部には、をクリックして**詳細コンパイル オプション**.  
  
     **コンパイラ設定の高度な** ダイアログ ボックスが表示されます。  
  
4.  **ターゲット フレームワーク (すべての構成)** 一覧で、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。 (選択しないでください[!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)])。  
  
5.  **[OK]** をクリックします。  
  
     **ターゲット フレームワークの変更** ダイアログ ボックスが表示されます。  
  
6.  **ターゲット フレームワークの変更**ダイアログ ボックスで、をクリックして**はい**です。  
  
     プロジェクトが閉じられ、再び開いたです。  
  
7.  次の手順でキャッシュのアセンブリへの参照を追加します。  
  
    1.  **ソリューション エクスプ ローラー**プロジェクトの名前を右クリックし、クリックして**参照の追加**です。  
  
    2.  選択、 **.NET** ] タブで [ `System.Runtime.Caching`、クリックして **[ok]** です。  
  
#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>Visual c# プロジェクトのターゲットの .NET Framework を変更するには  
  
1.  **ソリューション エクスプ ローラー**プロジェクト名を右クリックし、クリックして**プロパティ**です。  
  
     アプリケーションのプロパティ ウィンドウが表示されます。  
  
2.  **[アプリケーション]** タブをクリックします。  
  
3.  **ターゲット フレームワーク**一覧で、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。 (選択しないでください **.NET Framework 4 Client Profile**)。  
  
4.  次の手順でキャッシュのアセンブリへの参照を追加します。  
  
    1.  右クリックし、**参照**フォルダーをクリックして**参照の追加**です。  
  
    2.  選択、 **.NET** ] タブで [ `System.Runtime.Caching`、クリックして **[ok]** です。  
  
## <a name="adding-a-button-to-the-wpf-window"></a>WPF ウィンドウへボタンの追加  
 次に、ボタン コントロールを追加し、ボタンのイベント ハンドラーを作成`Click`イベント。 後で、テキスト ファイルの内容がキャッシュされ、表示されるボタンをクリックすると、コードを追加します。  
  
#### <a name="to-add-a-button-control"></a>ボタン コントロールを追加するには  
  
1.  **ソリューション エクスプ ローラー**、MainWindow.xaml ファイルを開くをダブルクリックします。  
  
2.  **ツールボックス****共通の WPF コントロール**、ドラッグ、`Button`コントロールを`MainWindow`ウィンドウです。  
  
3.  **プロパティ**ウィンドウで、設定、`Content`のプロパティ、`Button`に制御を**取得キャッシュ**です。  
  
## <a name="initializing-the-cache-and-caching-an-entry"></a>キャッシュの初期化とエントリをキャッシュ  
 次に、次のタスクを実行するコードを追加します。  
  
-   キャッシュ クラスのインスタンスを作成する: つまりはインスタンス化する新しい<xref:System.Runtime.Caching.MemoryCache>オブジェクト。  
  
-   キャッシュが使用するように指定、<xref:System.Runtime.Caching.HostFileChangeMonitor>のテキスト ファイルの変更を監視するオブジェクト。  
  
-   テキスト ファイルの読み取りおよびキャッシュ エントリとしてその内容をキャッシュします。  
  
-   キャッシュされたテキスト ファイルの内容を表示します。  
  
#### <a name="to-create-the-cache-object"></a>キャッシュ オブジェクトを作成するには  
  
1.  MainWindow.xaml.cs または MainWindow.Xaml.vb ファイルで、イベント ハンドラーを作成するために追加したボタンをダブルクリックします。  
  
2.  (宣言の前に、クラス) ファイルの上部には、次のコードを追加`Imports`(Visual Basic) または`using`(c#) ステートメント。  
  
    ```csharp  
    using System.Runtime.Caching;  
    using System.IO;  
    ```  
  
    ```vb  
    Imports System.Runtime.Caching  
    Imports System.IO  
    ```  
  
3.  イベント ハンドラーでは、キャッシュ オブジェクトをインスタンス化する次のコードを追加します。  
  
    ```csharp  
    ObjectCache cache = MemoryCache.Default;  
    ```  
  
    ```vb  
    Dim cache As ObjectCache = MemoryCache.Default  
    ```  
  
     <xref:System.Runtime.Caching.ObjectCache>クラスは、メモリ内のオブジェクトのキャッシュを提供する組み込みクラスです。  
  
4.  という名前のキャッシュ エントリの内容を読み取るには、次のコードを追加`filecontents`:  
  
    ```vb  
    Dim fileContents As String = TryCast(cache("filecontents"), String)  
    ```  
  
    ```csharp  
    string fileContents = cache["filecontents"] as string;  
    ```  
  
5.  キャッシュ エントリが名前付きかどうかを確認するには、次のコードを追加`filecontents`が存在します。  
  
    ```vb  
    If fileContents Is Nothing Then  
  
    End If  
    ```  
  
    ```csharp  
    if (fileContents == null)  
    {  
  
    }  
    ```  
  
     指定されたキャッシュ エントリが存在しない場合は、テキスト ファイルの読み取りし、キャッシュ エントリとしてキャッシュに追加する必要があります。  
  
6.  `if/then`ブロックして、新たに作成するのには、次のコードを追加するには、<xref:System.Runtime.Caching.CacheItemPolicy>に 10 秒後に、キャッシュ エントリが期限切れを指定するオブジェクト。  
  
    ```vb  
    Dim policy As New CacheItemPolicy()  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)  
    ```  
  
    ```csharp  
    CacheItemPolicy policy = new CacheItemPolicy();  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);  
    ```  
  
     削除または有効期限の情報が指定されていない場合、既定値は<xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>、キャッシュ エントリは決して期限切れに基づいて絶対時間にのみです。 代わりに、キャッシュ エントリには、メモリ負荷がかかっている場合にのみが期限切れです。 ベスト プラクティスとしては、常に明示的に、絶対または側線有効期限を指定する必要があります。  
  
7.  内部、`if/then`をブロックし、前の手順で追加したコードの後に、監視、し、テキスト ファイルのパスをコレクションに追加するファイルのパスのコレクションを作成する次のコードを追加します。  
  
    ```vb  
    Dim filePaths As New List(Of String)()  
    filePaths.Add("c:\cache\cacheText.txt")  
    ```  
  
    ```csharp  
    List<string> filePaths = new List<string>();  
    filePaths.Add("c:\\cache\\cacheText.txt");  
    ```  
  
    > [!NOTE]
    >  かどうかに使用するテキスト ファイルは`c:\cache\cacheText.txt`、テキスト ファイルが使用するパスを指定します。  
  
8.  新しいを追加する次のコードを追加する前の手順で追加したコードを次<xref:System.Runtime.Caching.HostFileChangeMonitor>キャッシュ エントリの変更のコレクションにオブジェクトを監視します。  
  
    ```vb  
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))  
    ```  
  
    ```csharp  
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));  
    ```  
  
     <xref:System.Runtime.Caching.HostFileChangeMonitor>オブジェクトは、テキスト ファイルのパスを監視し、変更が発生する場合は、キャッシュに通知します。 この例では、キャッシュ エントリの有効期限、ファイルの内容が変更された場合。  
  
9. 前の手順で追加したコードの後に、テキスト ファイルの内容を読み取るには、次のコードを追加します。  
  
    ```vb  
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()  
    ```  
  
    ```csharp  
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + + "\n" + DateTime.Now;   
    ```  
  
     キャッシュ エントリの有効期限が切れるときに表示できるように、日付と時刻のタイムスタンプが追加されます。  
  
10. としてキャッシュ オブジェクトに、ファイルの内容を挿入する次のコードを追加する前の手順で追加したコードの後、<xref:System.Runtime.Caching.CacheItem>インスタンス。  
  
    ```vb  
    cache.Set("filecontents", fileContents, policy)  
    ```  
  
    ```csharp  
    cache.Set("filecontents", fileContents, policy);  
    ```  
  
     渡すことによって、キャッシュ エントリを削除する方法に関する情報を指定する、<xref:System.Runtime.Caching.CacheItemPolicy>をパラメーターとして、先ほど作成したオブジェクト。  
  
11. 後に、`if/then`ブロックは、メッセージ ボックスに、キャッシュされたファイルの内容を表示する次のコードを追加します。  
  
    ```vb  
    MessageBox.Show(fileContents)  
    ```  
  
    ```csharp  
    MessageBox.Show(fileContents);  
    ```  
  
12. **ビルド** メニューのをクリックして**ビルド WPFCaching**プロジェクトをビルドします。  
  
## <a name="testing-caching-in-the-wpf-application"></a>WPF アプリケーションでキャッシュのテスト  
 アプリケーションをテストすることができます。  
  
#### <a name="to-test-caching-in-the-wpf-application"></a>WPF アプリケーションでキャッシュをテストするには  
  
1.  Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。  
  
     `MainWindow`ウィンドウが表示されます。  
  
2.  をクリックして**キャッシュを取得する**です。  
  
     テキスト ファイルからキャッシュされたコンテンツは、メッセージ ボックスに表示されます。 ファイルのタイムスタンプに注目してください。  
  
3.  メッセージ ボックスを閉じ、をクリックして**取得キャッシュ**再度**です。**  
  
     タイムスタンプは変更されません。 これは、キャッシュされたコンテンツの表示を示します。  
  
4.  クリックして、10 秒以上待機**取得キャッシュ**もう一度です。  
  
     この時刻に新しいタイムスタンプが表示されます。 これは、ポリシーが期限切れのキャッシュ エントリを任せることと、新しいキャッシュされたコンテンツが表示されることを示します。  
  
5.  テキスト エディターで作成したテキスト ファイルを開きます。 すべての変更をまだくださいしないでください。  
  
6.  メッセージ ボックスを閉じ、をクリックして**取得キャッシュ**再度**です。**  
  
     タイムスタンプをもう一度確認します。  
  
7.  テキスト ファイルに変更を加えるし、ファイルを保存します。  
  
8.  メッセージ ボックスを閉じ、をクリックして**取得キャッシュ**もう一度です。  
  
     このメッセージ ボックスには、新しいタイムスタンプやテキスト ファイルから更新されたコンテンツが含まれています。 ホスト ファイルの変更モニター削除すること、キャッシュ エントリ、ファイルを変更したときにすぐに、絶対のタイムアウト期間の有効期限が切れていない場合でもこれを示します。  
  
    > [!NOTE]
    >  ファイルを変更するための時間を 20 秒以上削除時間を増やすことができます。  
  
## <a name="code-example"></a>コード例  
 このチュートリアルを完了した後に作成したプロジェクトのコードが次の例のようになります。  
  
 [!code-csharp[CachingWPFApplications#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.Caching.MemoryCache>  
 <xref:System.Runtime.Caching.ObjectCache>  
 <xref:System.Runtime.Caching>  
 [.NET Framework アプリケーションでのキャッシュ](../../../../docs/framework/performance/caching-in-net-framework-applications.md)
