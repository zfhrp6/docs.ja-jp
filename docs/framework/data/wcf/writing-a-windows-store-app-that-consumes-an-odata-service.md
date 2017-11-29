---
title: "OData サービスを利用する Windows ストア アプリの開発"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: csharp
ms.assetid: 9917a0e9-ec93-49e5-a366-fd39b892eb8b
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0c1e2b9092abd54fd62848f58e2385bee5058553
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="writing-a-windows-store-app-that-consumes-an-odata-service"></a>OData サービスを利用する Windows ストア アプリの開発
Windows 8 アプリケーションの新しい型が導入されています。 Windows ストア アプリ。 まったく新しい外観を備え、さまざまなデバイス上で実行される Windows ストア アプリは、Windows ストアで入手できます。 このトピックでは、特に NetFlix のカタログで公開されている OData サービスを中心に、OData サービスを利用する Windows ストア アプリの開発方法を説明します。 Windows ストア アプリの詳細については、「 [Windows ストア アプリの概要](http://msdn.microsoft.com/library/windows/apps/br211386.aspx)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
  
1.  [Microsoft Windows 8](http://go.microsoft.com/fwlink/p/?LinkId=266654)  
  
2.  [Microsoft Visual Studio 2012](http://go.microsoft.com/fwlink/p/?LinkId=266655)  
  
3.  [WCF Data Services](http://msdn.microsoft.com/data/bb931106)  
  
#### <a name="creating-the-default-windows-store-grid-application"></a>既定の Windows ストア グリッド アプリケーションの作成  
  
1.  C# と XAML を使用して、新しい Windows ストア グリッド アプリケーションを作成します。 アプリケーションに OData.WindowsStore.NetflixDemo という名前を付けます。  
  
     ![新しいプロジェクト ダイアログ](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")  
  
2.  Package.appxmanifest を開き、[表示名] テキスト ボックスに表示名を入力します。 これによって、Windows 8 の検索機能で使用されるアプリケーション名が指定されます。  
  
     ![アプリケーション マニフェスト ファイル](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")  
  
3.  フレンドリ名を入力、 \<AppName > App.xaml ファイル内の要素。 これによってアプリケーションの起動時に表示されるアプリケーション名が設定されます。  
  
     ![App.xaml ファイル](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")  
  
4.  アプリケーションをビルドして起動します。 アプリケーションのスプラッシュ スクリーンが最初に表示されます。 以下のスクリーンショットは既定のスプラッシュ スクリーンを示しています。 使用される画像はプロジェクトの Assets フォルダーに格納されています。  
  
     ![既定のアプリのスプラッシュ スクリーン](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")  
  
     次にアプリケーション ウィザードが表示されます。  
  
     ![既定のアプリケーション](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")  
  
     既定のアプリケーションは、SampleDataSource.cs: SampleDataGroup と SampleDataItem 内のクラスのセットを定義します。これらはいずれも SampleDataCommon から派生しており、SampleDataCommon 自体は BindableBase から派生しています。 SampleDataGroup と SampleDataItem は既定の GridView にバインドされています。 SampleDataSource.cs は NetflixDemo プロジェクトの DataModel フォルダーにあります。 このアプリケーションにはグループ化されたコレクションが表示されます。 各グループには任意の数の項目が含まれており、これらの項目は SampleDataGroup と SampleDataItem によってぞれぞれ表されます。 前のスクリーンショットには、Group Title 1 というグループと、このグループ内のすべての項目が同時に表示されています。  
  
     アプリケーションのメイン ページは GroupedItemsPage.xaml です。 このファイルに含まれる GridView に、SampleDataSource.cs クラスが作成するサンプル データが表示されます。 GroupedItemsPage は、rootFrame.Navigate への呼び出しを通して App.xaml.cs によって読み込まれます。  
  
    ```csharp  
    if (!rootFrame.Navigate(typeof(GroupedItemsPage), "AllGroups"))  
    {  
        throw new Exception("Failed to create initial page");  
    }  
    ```  
  
     これによって GroupedItemsPage がインストールされ、LoadState メソッドが呼び出されます。 LoadState によって静的な SampleDataSource インスタンスが作成され、これによって SampleDataGroup オブジェクトのコレクションが作成されます。 SampleDataGroup オブジェクトには SampleDataItem オブジェクトのコレクションが含まれます。 LoadState は、SampleDataGroup オブジェクトのコレクションを DefaultViewModel に格納します。  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     次に DefaultViewModel が GridView にバインドされます。 これは、データ バインドの構成時に GroupedItemsPage.xaml ファイル内で参照されます。  
  
    ```xaml
    <CollectionViewSource  
                x:Name="groupedItemsViewSource"  
                Source="{Binding Groups}"  
                IsSourceGrouped="true"  
                ItemsPath="TopItems"  
                d:Source="{Binding AllGroups, Source={d:DesignInstance Type=data:SampleDataSource, IsDesignTimeCreatable=True}}"/>  
    ```  
  
     CollectionViewSource は、グループ化されたコレクションの処理時にプロキシとして使用されます。 バインドが発生すると、SampleDataGroup オブジェクトのコレクションを反復処理することによって GridView を設定します。  ItemsPath 属性は、格納されている SampleDataItems の検索に使用する SampleDataGroup のプロパティを CollectionViewSource に指定します。 この場合、各 SampleDataGroup オブジェクトには SampleDataItem オブジェクトの TopItems コレクションが含まれます。  
  
     Netflix の場合、ムービーはジャンルでグループ化されます。 このため、アプリケーションはジャンルの数とジャンル内のムービーの一覧を表示します。  
  
#### <a name="add-a-service-reference-to-the-netflix-odata-service"></a>Netflix OData サービスへのサービス参照の追加  
  
1.  Netflix OData サービスへの呼び出しを実行する前に、サービス参照を追加する必要があります。 ソリューション エクスプローラーでプロジェクトを右クリックし、[サービス参照の追加] をクリックします。  
  
     ![サービス参照 ダイアログ ボックスを追加](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")  
  
2.  Netflix OData サービスの URL をアドレス バーに入力し、[移動] をクリックします。 Netflix へのサービス参照の名前空間を設定し、[OK] をクリックします。  
  
     ![参照の追加サービス エラー](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")  
  
    > [!NOTE]
    >  まだインストールしていない場合[WCF データ サービス ツール for Windows Store Apps](http://go.microsoft.com/fwlink/p/?LinkId=266652)、上記のようなメッセージで求められます。 続行するには、リンクで参照されているツールをダウンロードしてインストールする必要があります。  
  
 サービス参照を追加すると、厳密に型指定されたクラスが生成されます。WCF Data Services はこのクラスを使用して Netflix OData サービスが返す OData を解析します。 SampleDataSource.cs で定義されるクラスは GridView にバインドできます。このため、生成される OData クライアント クラスのデータを、SampleDataSource.cs で定義されるバインド可能なクラスに転送する必要があります。  これを実行するには、SampleDataSource.cs で定義されるデータ モデルにいくつかの変更を加える必要があります。  
  
#### <a name="update-the-data-model-for-the-application"></a>アプリケーションで使用するデータ モデルの更新  
  
1.  コードを sampledatasource.cs ファイル内の既存のコードを置き換える[この gist](https://gist.github.com/3419288)です。 更新されたコードにより LoadMovies メソッドが (SampleDataSource クラスに) 追加されます。このメソッドによって Netflix OData にクエリが実行されることで、ジャンルの一覧が設定され、各ジャンルにムービーの一覧が設定されます。 SampleDataGroup クラスはジャンルを表すために使用され、SampleDataItem クラスはムービーを表すために使用されます。  
  
    ```csharp  
    public static async void LoadMovies()  
    {  
        IEnumerable<Title> titles = await ((DataServiceQuery<Title>)Context.Titles  
            .Expand("Genres,AudioFormats,AudioFormats/Language,Awards,Cast")  
            .Where(t => t.Rating == "PG")  
            .OrderByDescending(t => t.ReleaseYear)  
            .Take(300)).ExecuteAsync();  
  
        foreach (Title title in titles)  
        {  
            foreach (Genre netflixGenre in title.Genres)  
            {  
                SampleDataGroup genre = GetGroup(netflixGenre.Name);  
                if (genre == null)  
                {  
                    genre = new SampleDataGroup(netflixGenre.Name, netflixGenre.Name, String.Empty, title.BoxArt.LargeUrl, String.Empty);  
                    Instance.AllGroups.Add(genre);  
                }  
                var content = new StringBuilder();  
                // Write additional things to content here if you want them to display in the item detail.  
                genre.Items.Add(new SampleDataItem(title.Id, title.Name, String.Format("{0}rnrn{1} ({2})", title.Synopsis, title.Rating, title.ReleaseYear), title.BoxArt.HighDefinitionUrl ?? title.BoxArt.LargeUrl, "Description", content.ToString()));  
            }  
        }  
    }  
    ```  
  
     [タスク ベースの非同期パターン](http://go.microsoft.com/fwlink/p/?LinkId=266651)(TAP) を使用して、300 (Take) 最近 (OrderByDescending) を非同期で取得 pg 指定 (Where) の映画が Netflix からバックアップします。 コードの残りの部分は、OData フィードで返されるエンティティの SimpleDataItems と SimpleDataGroups で構成されます。  
  
     SampleDataSource クラスは、シンプルな検索手法も実装します。 この場合は、読み込まれたムービーのシンプルなインメモリ検索を実行します。  
  
    ```csharp  
    public static IEnumerable<SampleDataItem> Search(string searchString)  
    {  
            var regex = new Regex(searchString, RegexOptions.CultureInvariant | RegexOptions.IgnoreCase | RegexOptions.IgnorePatternWhitespace);  
            return Instance.AllGroups  
                .SelectMany(g => g.Items)  
                .Where(m => regex.IsMatch(m.Title) || regex.IsMatch(m.Subtitle))  
                    .Distinct(new SampleDataItemComparer());  
    }  
    ```  
  
     SampleDataSource.cs には ExtensionMethods というクラスも定義されています。 これらの拡張メソッドでは、TAP パターンを使用することで、UI のブロックが発生しない SampleDataSource による OData のクエリを可能にしています。 たとえば以下のコードでは、Task.Factory.FromAsync メソッドを使用して TAP を実装しています。  
  
    ```csharp  
    public static async Task<IEnumerable<T>> ExecuteAsync<T>(this DataServiceQuery<T> query)  
    {  
        return await Task.Factory.FromAsync<IEnumerable<T>>(query.BeginExecute(null, null), query.EndExecute);  
    }  
    ```  
  
     既定のアプリケーションと同様、アプリケーションのメイン ページは GroupedItemsPage となります。 ただし今回は、Netflix から取得され、ジャンル別にグループ化されたムービーが表示されます。  GroupedItemsPage がインストールされると、LoadState メソッドが呼び出されます。 前述のとおり、LoadState によって静的な SampleDataSource インスタンスが作成され、Netflix OData サービスへの呼び出しが実行されます。 LoadState は、ジャンル (SampleDataGroup オブジェクト) のコレクションを DefaultViewModel に格納します。  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     前述のとおり、次に DefaultViewModel を使用して GridView にデータがバインドされます。  
  
#### <a name="add-a-search-contract-to-allow-the-application-to-participate-in-windows-search"></a>検索コントラクトの追加による、アプリケーションの Windows 検索への参加  
  
1.  アプリケーションに検索コントラクトを追加します。 これによってアプリケーションと Windows 8 の検索エクスペリエンスを統合できるようになります。 検索コントラクトに SearchResultsPage.xaml という名前を付けます。  
  
     ![検索コントラクトの追加](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")  
  
2.  queryText の周囲に埋め込まれた引用符を削除して、SearchResultsPage.xaml.cs の 58 行目を変更します。  
  
    ```csharp  
    // Communicate results through the view model  
    this.DefaultViewModel["QueryText"] = queryText;  
    this.DefaultViewModel["Filters"] = filterList;  
    this.DefaultViewModel["ShowFilters"] = filterList.Count > 1;  
    ```  
  
3.  検索結果を取得するには、以下の 2 行のコードを SearchResultsPage.xaml.cs の 81 行目に挿入します。  
  
    ```csharp  
    // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                    //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                    var searchValue = (string)this.DefaultViewModel["QueryText"];  
                    this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
    ```  
  
 ユーザーが Windows 検索を起動し、検索用語を入力して、検索バーで Netflix デモ アプリのアイコンをタッチすると、SearchResultsPage の LoadState メソッドが実行されます。 クエリのテキストは LoadState に送信されるナビゲーション パラメーターに含まれています。 次に、Filter_SelectionChanged メソッドが呼び出され、このメソッドによって SampleDataSource クラスで Search メソッドが呼び出されます。 結果が返され、SearchResultsPage.xaml ページに表示されます。  
  
```csharp  
/// <summary>  
        /// Invoked when a filter is selected using the ComboBox in snapped view state.  
        /// </summary>  
        /// <param name="sender">The ComboBox instance.</param>  
        /// <param name="e">Event data describing how the selected filter was changed.</param>  
        void Filter_SelectionChanged(object sender, SelectionChangedEventArgs e)  
        {  
            // Determine what filter was selected  
            var selectedFilter = e.AddedItems.FirstOrDefault() as Filter;  
            if (selectedFilter != null)  
            {  
                // Mirror the results into the corresponding Filter object to allow the  
                // RadioButton representation used when not snapped to reflect the change  
                selectedFilter.Active = true;  
  
                // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                var searchValue = (string)this.DefaultViewModel["QueryText"];  
                this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
  
                // Ensure results are found  
                object results;  
                ICollection resultsCollection;  
                if (this.DefaultViewModel.TryGetValue("Results", out results) &&  
                    (resultsCollection = results as ICollection) != null &&  
                    resultsCollection.Count != 0)  
                {  
                    VisualStateManager.GoToState(this, "ResultsFound", true);  
                    return;  
                }  
            }  
  
            // Display informational text when there are no search results.  
            VisualStateManager.GoToState(this, "NoResultsFound", true);  
        }  
```  
  
 アプリケーション参照の場合への検索の統合の詳細については[検索: Windows 8 の検索エクスペリエンスに統合する](http://go.microsoft.com/fwlink/p/?LinkId=266650)です。  
  
## <a name="run-the-application"></a>アプリケーションの実行  
 F5 キーを押してアプリケーションを起動します。 アプリケーションの起動時には、画像の読み込みに数秒かかります。 また、最初の検索では結果がまったく返されない場合があります。 実際のアプリケーションでは、これらの問題の両方に対処する必要があります。  
  
 アプリケーションは、Netflix OData サービスを呼び出し、生成される OData クライアント クラスでデータを受け取り、バインド可能なデータ クラス (SampleDataSource、SampleDataGroup、および SampleDataItem) にこのデータを転送します。 これらのバインド可能なクラスが使用され、データが GridView にバインドされます。 XAML のデータ バインドを参照してくださいの動作方法に慣れていない場合[リストまたはグリッド (C #/VB/C + + と XAML を使った Windows ストア アプリ) でアイテムをグループ化方法](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627)です。
