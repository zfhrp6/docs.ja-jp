---
title: "チュートリアル: WPF アプリケーション内のアプリケーション データのキャッシュ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "キャッシュ [.NET Framework]"
  - "キャッシュ [WPF]"
  - "チュートリアル [WPF], キャッシュ"
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# チュートリアル: WPF アプリケーション内のアプリケーション データのキャッシュ
キャッシュを使用するとメモリにデータを格納しておくことができるのですぐにアクセスできます。  データに再度アクセスするとき、アプリケーションは元のソースからデータを取得する代わりにキャッシュからデータを取得できます。  これにより、パフォーマンスとスケーラビリティが向上します。  さらにキャッシュを使用するとデータ ソースが一時的に使用できない場合もデータが使用可能になります。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] は [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アプリケーションでキャッシュを使用できるクラスを提供します。  これらのクラスは <xref:System.Runtime.Caching> の名前空間にあります。  
  
> [!NOTE]
>  <xref:System.Runtime.Caching> 名前空間は [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] で新たに追加されました。  この名前空間を使用すると、すべての [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アプリケーションでキャッシュを使用できます。  以前のバージョンの [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] では、<xref:System.Web> 名前空間でしかキャッシュを使用できないため、ASP.NET クラスに対する依存関係が必要になります。  
  
 このチュートリアルでは、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] で使用可能なキャッシュ機能を [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションの一部として使用する方法について説明します。  チュートリアルではテキスト ファイルの内容をキャッシュします。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   WPF アプリケーション プロジェクトを作成します。  
  
-   [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] に参照を追加します。  
  
-   キャッシュを初期化します。  
  
-   テキスト ファイルの内容を格納しているキャッシュ エントリを追加します。  
  
-   キャッシュ エントリの削除ポリシーを指定します。  
  
-   キャッシュ ファイルのパスを監視し、監視対象の項目への変更についてキャッシュ インスタンスに通知します。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]  
  
-   少量のテキストを含むテキスト ファイル。  このテキスト ファイルの内容をメッセージ ボックスに表示します。 このチュートリアルに示すコードでは、次のファイルを使用していることを前提としています。  
  
     `c:\cache\cacheText.txt`  
  
     ただし、このチュートリアルでは、任意のテキスト ファイルを使用し、コードにわずかな変更を加えることができます。  
  
## WPF アプリケーション プロジェクトの作成  
 WPF アプリケーション プロジェクトを作成することから始めます。  
  
#### WPF アプリケーションを作成するには  
  
1.  [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をクリックし、**\[新しいプロジェクト\]** をクリックします。  
  
     **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
3.  **\[インストールされているテンプレート\]** で、使用するプログラミング言語 \(**\[Visual Basic\]** または **\[Visual C\#\]**\) をクリックします。  
  
4.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[WPF アプリケーション\]** をクリックします。  
  
    > [!NOTE]
    >  **\[WPF アプリケーション\]** テンプレートがない場合は、WPF をサポートしている [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] のバージョンを使用しているかどうかを確認してください。  **\[新しいプロジェクト\]** ダイアログ ボックスで、一覧から [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] を選択します。  
  
5.  **\[名前\]** ボックスにプロジェクトの名前を入力します。  たとえば、「WPFCaching」と入力できます。  
  
6.  **\[ソリューションのディレクトリを作成\]** チェック ボックスをオンにします。  
  
7.  **\[OK\]** をクリックします。  
  
     **デザイン** ビューに WPF デザイナーが開き、MainWindow.xaml ファイルが表示されます。  [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] では、**My Project** フォルダー、Application.xaml ファイル、および MainWindow.xaml ファイルを作成します。  
  
## .NET Framework を対象にすることおよびキャッシュ アセンブリへの参照の追加  
 既定では、WPF アプリケーションは [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)] を対象とします。  WPF アプリケーションで <xref:System.Runtime.Caching> 名前空間を使用するには、名前空間で [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] \([!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)] ではない\) を対象にして、名前空間への参照を含める必要があります。  
  
 そのため、次の手順では対象の .NET Framework を変更し、<xref:System.Runtime.Caching> 名前空間への参照を追加します。  
  
> [!NOTE]
>  Visual Basic プロジェクトと Visual C\# プロジェクトでは、対象の .NET Framework を変更する手順が異なります。  
  
#### Visual Basic で対象の .NET Framework を変更するには  
  
1.  **ソリューション エクスプローラー**で、プロジェクト名を右クリックし、**\[プロパティ\]** をクリックします。  
  
     アプリケーションのプロパティ ウィンドウが表示されます。  
  
2.  **\[コンパイル\]** タブをクリックします。  
  
3.  ウィンドウの下部にある **\[詳細コンパイル オプション\]** をクリックします。  
  
     **\[コンパイラの詳細設定\]** ダイアログ ボックスが表示されます。  
  
4.  **ターゲット フレームワーク （すべての構成）** の一覧の \[ [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。  （ [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]を選択しないでください）。  
  
5.  **\[OK\]** をクリックします。  
  
     **\[対象とする Framework の変更\]** ダイアログ ボックスが表示されます。  
  
6.  **\[対象とする Framework の変更\]** ダイアログ ボックスで、**\[はい\]** をクリックします。  
  
     プロジェクトが閉じてから再び開きます。  
  
7.  次の手順に従って、キャッシュ アセンブリへの参照を追加します。  
  
    1.  **ソリューション エクスプローラー**で、プロジェクトの名前を右クリックし、**\[参照の追加\]** をクリックします。  
  
    2.  **\[.NET\]** タブをクリックし、`System.Runtime.Caching` を選択して、**\[OK\]** をクリックします。  
  
#### Visual C\# プロジェクトで対象の .NET Framework を変更するには  
  
1.  **ソリューション エクスプローラー**で、プロジェクト名を右クリックし、**\[プロパティ\]** をクリックします。  
  
     アプリケーションのプロパティ ウィンドウが表示されます。  
  
2.  **\[アプリケーション\]** タブをクリックします。  
  
3.  **\[対象とする Framework\]** ボックスの一覧で、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] を選択します   \(**.NET Framework 4 Client Profile** は選択しないでください\)。  
  
4.  次の手順に従って、キャッシュ アセンブリへの参照を追加します。  
  
    1.  **\[参照設定\]** フォルダーを右クリックし、**\[参照の追加\]** をクリックします。  
  
    2.  **\[.NET\]** タブをクリックし、`System.Runtime.Caching` を選択して、**\[OK\]** をクリックします。  
  
## WPF ウィンドウへのボタンの追加  
 次に、ボタン コントロールを追加して、ボタンの `Click` イベントのイベント ハンドラーを作成します。  後でコードを追加し、ボタンをクリックしたときにテキスト ファイルの内容がキャッシュされて表示されるようにします。  
  
#### ボタン コントロールを追加するには  
  
1.  **ソリューション エクスプローラー**で、MainWindow.xaml ファイルをダブルクリックして開きます。  
  
2.  **\[ツールボックス\]** の **\[コモン WPF コントロール\]** で、`Button` コントロールを `MainWindow` ウィンドウにドラッグします。  
  
3.  **プロパティ** ウィンドウで、`Button` コントロールの `Content` プロパティを \[Get Cache\] に設定します。  
  
## キャッシュの初期化とエントリのキャッシュ  
 次に、次のタスクを行うコードを追加します。  
  
-   キャッシュ クラスのインスタンスを作成します。つまり、新しい <xref:System.Runtime.Caching.MemoryCache> オブジェクトのインスタンスを生成します。  
  
-   キャッシュが <xref:System.Runtime.Caching.HostFileChangeMonitor> オブジェクトを使用してテキスト ファイルの変更を監視するよう指定します。  
  
-   テキスト ファイルを読み取り、その内容をキャッシュ エントリとしてキャッシュします。  
  
-   キャッシュしたテキスト ファイルの内容を表示します。  
  
#### キャッシュ オブジェクトを作成するには  
  
1.  MainWindow.xaml.cs ファイルまたは MainWindow.Xaml.vb ファイルにイベント ハンドラーを作成するために、追加したボタンをダブルクリックします。  
  
2.  ファイルの上部 \(クラス宣言の前\) に次の `Imports` \(Visual Basic\) または `using` \(C\#\) ステートメントを追加します。  
  
    ```csharp  
    using System.Runtime.Caching;  
    using System.IO;  
    ```  
  
    ```vb  
    Imports System.Runtime.Caching  
    Imports System.IO  
    ```  
  
3.  キャッシュ オブジェクトのインスタンスを生成するためにイベント ハンドラーに次のコードを追加します。  
  
    ```csharp  
    ObjectCache cache = MemoryCache.Default;  
    ```  
  
    ```vb  
    Dim cache As ObjectCache = MemoryCache.Default  
    ```  
  
     <xref:System.Runtime.Caching.ObjectCache> クラスは、メモリ内オブジェクト キャッシュを提供する組み込みクラスです。  
  
4.  `filecontents` という名前のキャッシュ エントリの内容を読み取るために次のコードを追加します。  
  
    ```vb  
    Dim fileContents As String = TryCast(cache("filecontents"), String)  
    ```  
  
    ```csharp  
    string fileContents = cache["filecontents"] as string;  
    ```  
  
5.  `filecontents` という名前のキャッシュ エントリがあるかどうかを確認するために次のコードを追加します。  
  
    ```vb  
    If fileContents Is Nothing Then  
  
    End If  
    ```  
  
    ```csharp  
    if (fileContents == null)  
    {  
  
    }  
    ```  
  
     指定したキャッシュ エントリがない場合は、テキスト ファイルを読み取り、これをキャッシュ エントリとしてキャッシュに追加する必要があります。  
  
6.  キャッシュ エントリの有効期限が 10 秒後に切れるように指定する新しい <xref:System.Runtime.Caching.CacheItemPolicy> オブジェクトを作成するために、`if/then` ブロックに次のコードを追加します。  
  
    ```vb  
    Dim policy As New CacheItemPolicy()  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)  
    ```  
  
    ```csharp  
    CacheItemPolicy policy = new CacheItemPolicy();  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);  
    ```  
  
     削除情報や有効期限情報が指定されない場合、既定値は <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration> になり、キャッシュ エントリが絶対時間のみに基づいて有効期限切れになることはなくなります。  この場合はメモリ圧迫の状態にある場合にのみキャッシュ エントリが期限切れになります。  ベスト プラクティスとして、常に絶対有効期限またはスライド式有効期限を明示的に指定してください。  
  
7.  監視するファイル パスのコレクションを作成してテキスト ファイルのパスをコレクションに追加するために、`if/then` ブロック内の前の手順で追加したコードの後に次のコードを追加します。  
  
    ```vb  
    Dim filePaths As New List(Of String)()  
    filePaths.Add("c:\cache\cacheText.txt")  
    ```  
  
    ```csharp  
    List<string> filePaths = new List<string>();  
    filePaths.Add("c:\\cache\\cacheText.txt");  
    ```  
  
    > [!NOTE]
    >  使用しようとするテキスト ファイルが `c:\cache\cacheText.txt` でない場合は、そのテキスト ファイルのパスを指定します。  
  
8.  キャッシュ エントリの変更監視機能のコレクションに新しい <xref:System.Runtime.Caching.HostFileChangeMonitor> オブジェクトを追加するために、前の手順で追加したコードの後に次のコードを追加します。  
  
    ```vb  
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))  
    ```  
  
    ```csharp  
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));  
    ```  
  
     <xref:System.Runtime.Caching.HostFileChangeMonitor> オブジェクトはテキスト ファイルのパスを監視し、変更が発生するとキャッシュに通知します。  この例のキャッシュ エントリは、ファイルの内容に変更があると有効期限が切れます。  
  
9. テキスト ファイルの内容を読み取るために、前の手順で追加したコードの後に次のコードを追加します。  
  
    ```vb  
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()  
    ```  
  
    ```csharp  
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + + "\n" + DateTime.Now;   
    ```  
  
     キャッシュ エントリの有効期限を確認できるように、日付と時刻のタイムスタンプが追加されます。  
  
10. ファイルの内容を <xref:System.Runtime.Caching.CacheItem> インスタンスとしてキャッシュ オブジェクトに挿入するために、前の手順で追加したコードの後に次のコードを追加します。  
  
    ```vb  
    cache.Set("filecontents", fileContents, policy)  
    ```  
  
    ```csharp  
    cache.Set("filecontents", fileContents, policy);  
    ```  
  
     キャッシュ エントリの削除方法に関する情報を指定するために、前に作成した <xref:System.Runtime.Caching.CacheItemPolicy> オブジェクトをパラメーターとして渡します。  
  
11. キャッシュしたファイルの内容をメッセージ ボックスに表示するために、`if/then` ブロックの後に次のコードを追加します。  
  
    ```vb  
    MessageBox.Show(fileContents)  
    ```  
  
    ```csharp  
    MessageBox.Show(fileContents);  
    ```  
  
12. **\[ビルド\]** メニューの **\[WPFCaching のビルド\]** をクリックし、プロジェクトをビルドします。  
  
## WPF アプリケーションでのキャッシュのテスト  
 これで、アプリケーションをテストできるようになりました。  
  
#### WPF アプリケーションでのキャッシュをテストするには  
  
1.  Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。  
  
     `MainWindow` ウィンドウが表示されます。  
  
2.  **\[Get Cache\]** をクリックします。  
  
     テキスト ファイルのキャッシュされた内容がメッセージ ボックスに表示されます。  ファイルにタイムスタンプがあることを確認します。  
  
3.  メッセージ ボックスを閉じてから、**\[Get Cache\]** を再度クリックします。  
  
     タイムスタンプは変わりません。  これは、キャッシュされた内容が表示されていることを示します。  
  
4.  10 秒以上待機してから、**\[Get Cache\]** を再度クリックします。  
  
     今度は新しいタイムスタンプが表示されます。  これはポリシーによってキャッシュ エントリの有効期限が切れ、キャッシュされた新しい内容が表示されていることを示します。  
  
5.  テキスト エディターで、作成したテキスト ファイルを開きます。  まだ変更は加えないでください。  
  
6.  メッセージ ボックスを閉じてから、**\[Get Cache\]** を再度クリックします。  
  
     タイムスタンプを再度確認します。  
  
7.  テキスト ファイルに変更を加え、ファイルを保存します。  
  
8.  メッセージ ボックスを閉じてから、**\[Get Cache\]** を再度クリックします。  
  
     このメッセージ ボックスには、テキスト ファイルの更新された内容と新しいタイムスタンプが格納されます。  これは、絶対タイムアウト期間が期限切れではない場合でも、ファイルを変更したときにホスト ファイルの変更監視機能によってキャッシュ エントリが直ちに削除されたことを示します。  
  
    > [!NOTE]
    >  削除時間を 20 秒以上に長くすると、ファイルに変更を加える時間を長くすることができます。  
  
## コード例  
 このチュートリアルを完了すると、作成したプロジェクトのコードは次の例のようになります。  
  
 [!code-csharp[CachingWPFApplications#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]  
  
## 参照  
 <xref:System.Runtime.Caching.MemoryCache>   
 <xref:System.Runtime.Caching.ObjectCache>   
 <xref:System.Runtime.Caching>   
 [.NET Framework アプリケーションでのキャッシュ](../../../../docs/framework/performance/caching-in-net-framework-applications.md)