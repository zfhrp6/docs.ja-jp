---
title: "Windows Presentation Foundation クライアントでのデータ バインディング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# Windows Presentation Foundation クライアントでのデータ バインディング
このサンプルでは、Windows Presentation Foundation \(WPF\) クライアントでのデータ バインディングの使用方法を示します。  このサンプルでは、アルバムの配列をランダムに生成してクライアントに返す [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスを使用します。  各アルバムには、名前、価格、およびアルバム トラックの一覧が含まれます。  アルバム トラックには、名前と継続時間が含まれます。  サービスによって返される情報は、[!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] クライアントが提供するユーザー インターフェイス \(UI\) に自動的にバインドされます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 データ バインディングでは、データ ソースを自動的に UI にバインドすることができます。  これによってプログラミング モデルが簡素化されます。プログラムを使って、各 UI 要素をデータ オブジェクトまたはデータ オブジェクトの配列からのデータで更新する必要がないためです。  単一の UI 要素にオブジェクトをバインドしたり、複数の入力情報を取得する `ListBox` などのコントロールに配列をバインドしたりできます。  データを UI 要素の `DataContext` にバインドする方法を次のコードに示します。  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
  
```  
  
 前のサンプルでは、`myPanel` という `grid` レイアウト要素の `DataContext` が、`GetAlbumList` メソッドによって返されるデータに設定されます。  `DataContext` では、バインディングに使用されるデータ ソースやその他のバインディング特性 \(パスなど\) に関する情報を、要素が親要素から継承できます。  このコード行は、サーバー上のデータが更新されるたびに実行する必要があります。  たとえば、ウィンドウが初期化されたり新しいアルバムが追加されたりするときに実行します。  
  
 次の XAML サンプル コードでは、`ListBox` に `ItemsSource="{Binding }"` を指定します。  
  
```  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
  
```  
  
 これは、最上位の UI 要素にバインドされるデータは、このコントロール \(アルバムの配列\) にもバインドされることを示します。  また、`ItemTemplate="{StaticResource AlbumStyle}"` では、データ テンプレートが `ListBox` の各項目で使用されるように指定されます。  データの書式設定方法を指定するデータ テンプレートを定義することもできます。  こうしたデータ テンプレートは、アプリケーション内の他の UI 要素で再使用できます。この利点は、データ テンプレートを 1 つの場所で定義および維持できることです。  
  
 `AlbumStyle` データ テンプレートでは、2 つの並列の `TextBlock` を伴ってグリッドが配置されます。  このうちの 1 つはアルバムの名前を指定し、もう 1 つはアルバムのトラック数を指定します。  
  
```  
<DataTemplate x:Key="AlbumStyle">  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="260" />  
            <ColumnDefinition Width="60" />  
        </Grid.ColumnDefinitions>  
        <TextBlock Grid.Column="0" TextContent="{Binding Path=Title}" />  
        <TextBlock Grid.Column="1" TextContent="{Binding Path=Tracks#.Count}" HorizontalAlignment="Right" />  
    </Grid>  
</DataTemplate>  
  
```  
  
 2 つ目の `ListBox` を作成する XAML コードを次に示します。  
  
```  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
  
```  
  
 このコードは、`ItemsSource` のパスを指定します。  これは、このコントロールにバインドされるデータは最上位のデータではなく、`Tracks` という最上位データのプロパティであることを示します。  このプロパティは、アルバムに含まれるトラックの配列を表します。  さらに、`TrackStyle` という別の `DataTemplate` が指定されています。  `TrackStyle` テンプレートのレイアウトは `AlbumStyle` テンプレートのレイアウトに似ていますが、`TextBlock` は別々のプロパティにバインドされます。  これは、2 つのテンプレートが異なるデータ オブジェクトで使用されるためです。  
  
### サンプルをセットアップ、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  単一コンピューター構成か複数コンピューター構成かに応じて、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。  続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。  このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
  
## 参照