---
title: "プロパティ昇格アクティビティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# プロパティ昇格アクティビティ
このサンプルでは、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 昇格機能をワークフロー作成に直接統合するエンド ツー エンドのソリューションを示します。昇格機能の使用を単純化する構成要素、ワークフロー アクティビティ、およびワークフロー拡張機能のコレクションが用意されています。また、サンプルには、このコレクションの使用方法を示す簡単なワークフローが含まれています。  
  
> [!NOTE]
>  サンプルは、演習目的で利用するためにのみ提供されています。サンプルを運用環境で使用することは想定されていないため、運用環境でのサンプルのテストは行われていません。Microsoft では、これらのサンプルに関する製品サポート情報を提供していません。  
  
## 前提条件  
  
-   初期化された <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> データベース  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## サンプル プロジェクト  
  
-   **PropertyPromotionActivity** プロジェクトには、昇格固有の構成要素、ワークフロー アクティビティ、およびワークフロー拡張機能に関連するファイルが含まれています。  
  
-   **CounterServiceApplication** プロジェクトには、**SqlWorkflowInstanceStorePromotion** プロジェクトを使用するサンプル ワークフローが含まれています。  
  
-   <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> データベースに対して実行される必要がある SQL スクリプト \(PropertyPromotionActivitySQLSample.sql\)。  
  
-   2 つの [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] プロジェクトをリンクするソリューション ファイル \(`PropertyPromotionActivity.sln`\)。  
  
## サンプルをセットアップおよび実行するには  
  
1.  ワークフロー永続化データベースを初期化します。  
  
    1.  サンプル ディレクトリ \(\\WF\\Basic\\Persistence\\PropertyPromotionActivity\) に移動して、CreateInstanceStore.cmd を実行します。  
  
    2.  管理特権がない場合は、SQL Server ログインを作成します。SQL Server Management Studio で **\[セキュリティ\]**、**\[ログイン\]** に移動します。**\[ログイン\]** を右クリックして新しいログインを作成します。**\[データベース\]**、**\[InstanceStore\]**、**\[セキュリティ\]** を開いて、自分の ACL ユーザーを SQL ロールに追加します。**\[ユーザー\]** を右クリックして **\[新しいユーザー\]** をクリックします。**\[ログイン名\]** を、上記で作成したユーザーに設定します。そのユーザーを、System.Activities.DurableInstancing.InstanceStoreUsers \(およびその他\) のデータベース ロールのメンバーシップに追加します。ユーザーが既に存在している場合もあります \(ユーザー dbo など\)。  
  
2.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で PropertyPromotionActivity.sln ソリューション ファイルを開きます。  
  
3.  ローカルの SQL Server Express 以外のデータベースにインスタンス ストアを作成した場合は、データベース接続文字列を更新する必要があります。手順 1. で初期化された永続化データベースをポイントするように `sqlWorkflowInstanceStorePromotion` ノードの `connectionString` 属性の値を設定して、**CounterServiceApplication** の下の App.config ファイルを変更します。  
  
4.  ソリューションをビルドして実行します。これにより、カウンター WF サービスが開始され、ワークフロー インスタンスが自動的に開始されます。  
  
5.  永続化データベースの \[dbo\].\[CounterService\] ビューですべての行をすばやく選択します \(このビューは、手順 1. の CreateInstanceStore.cmd の実行により追加されました\)。以下と同様の結果セットが生成されます。  
  
    |InstanceId|CounterValue|CounterValueLastUpdated|  
    |----------------|------------------|-----------------------------|  
    |2FA2C302\-929E\-4C0D\-8C25\-768A3DA20CE5|12|2010\-02\-18 22:48:01.740|  
  
     ビューの更新を続行すると、CounterValue および CounterValueLastUpdated が 2 秒ごとに変更されます。これは、カウンターがカウンター自身を更新する間隔です。CounterValue と CounterValueLastUpdated は、このワークフローの昇格されたプロパティを表します。  
  
## サンプルを削除するには  
  
-   サンプル ディレクトリ \(\\WF\\Basic\\Persistence\\PropertyPromotionActivity\) で RemoveInstanceStore.cmd を実行します。  
  
## このサンプルについて  
 サンプルには、次の 2 つのプロジェクトと SQL ファイルが含まれています。  
  
-   **CounterServiceApplication** は、単純なカウンター WF サービスをホストするコンソール アプリケーションです。`Start` エンドポイントを通して一方向のメッセージを受信すると、ワークフローは 0 から 29 までをカウントし、2 秒ごとにカウンター変数がインクリメントされます。カウンターがインクリメントされるたびに、ワークフローが永続化され、昇格されたプロパティは \[dbo\].\[CounterService\] ビューで更新されます。コンソール アプリケーションが実行されると、WF サービスをホストし、メッセージを `Start` エンドポイントに送信して、カウンター WF インスタンスを作成します。  
  
-   **PropertyPromotionActivity** は、**CounterServiceApplication** が使用する構成要素、ワークフロー アクティビティ、およびワークフロー拡張機能を含むクラス ライブラリです。  
  
-   **PropertyPromotionActivitySQLSample.sql** は、ビュー \[dbo\].\[CounterService\] を作成し、データベースに追加します。  
  
### CounterServiceApplication  
  
#### SqlWorkflowInstanceStorePromotion 構成要素の使用  
 `SqlWorkflowInstanceStorePromotion` 構成要素は `SqlWorkflowInstanceStore` 構成要素から継承されますが、`promotionSets` という追加の構成要素が追加されます。`promotionSets` 要素は、ユーザーが構成を通して昇格されたプロパティを指定できるようにします。これは、サンプルで使用される構成ファイルです。  
  
```xml  
<sqlWorkflowInstanceStorePromotion connectionString ="Data Source=.;Initial Catalog=SqlWorkflowInstanceStoreTest;Integrated Security=True;">  
  <promotionSets>  
    <promotionSet name="CounterService">  
      <promotedValue propertyName="Count"/>  
      <promotedValue propertyName="LastIncrementedAt"/>  
    </promotionSet>  
  </promotionSets>  
</sqlWorkflowInstanceStorePromotion>  
```  
  
 \[dbo\].\[CounterService\] ビューの定義を確認します。  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
  
```  
  
 ワークフロー インスタンスが永続化されると、構成で定義された各 `PromotionSet` の `InstancePromotedProperties` ビューに行が挿入されます。この行には、`PromotionSet` のすべての昇格されたプロパティが含まれます \(列ごとに 1 つの昇格されたプロパティ\)。この `PromotionSet` は、`InstanceId, PromotionName` のタプルによってキー指定されます。このサンプルには、名前属性が `CounterService` である構成で定義されている 1 つの `PromotionSet` があります。`PromotionName` 列の値が `PromotionSet` 要素の名前属性と等しいことがわかります。  
  
 `promotedValue` 要素の順序は、`InstancePromotedProperties` ビューの昇格されたプロパティの位置と相関しています。`Count` は最初の `promotedValue` 要素です。その結果、`InstancePromotedProperties` ビューの `Value1` 列にマップされます。`LastIncrementedAt` は 2 番目の `promotedValue` 要素です。その結果、`InstancePromotedProperties` ビューの `Value2` 列にマップされます。  
  
#### PromoteValue アクティビティの使用  
 [!INCLUDE[wf2](../../../../includes/wf2-md.md)] デザイナーで CounterService.xamlx ファイルを確認します。WF の定義には、`PromoteValue<DateTime>` および `PromoteValue<Int32>` の 2 つの特別なアクティビティがあります。  
  
 `PromoteValue<Int32>` アクティビティには、`Count` として定義されているその `Name` メンバーがあります。これは、構成の最初の `promotedValue` 要素と一致し、`Counter` ワークフロー変数として定義されているその `Value` があります。ワークフローが永続化されると、`Counter` ワークフロー変数は昇格されたプロパティとして `InstancePromotedProperties` ビューの `Value1` 列に保存されます。  
  
 `PromoteValue<DateTime>` アクティビティには、`LastIncrementedAt` として定義されているその `Name` メンバーがあります。これは、構成の 2 番目の `promotedValue` 要素と一致し、`TimeLastIncremented` ワークフロー変数として定義されているその `Value` があります。これは、ワークフローが永続化されると、`TimeLastIncremented` ワークフロー変数の値が昇格されたプロパティとして `InstancePromotedProperties` ビューの  `Value2` 列に保存されることを意味します。  
  
 `PromotedValue` アクティビティには、`ClearExistingPromotedData` というブール型のメンバーもあります。このメンバーを `true` に設定すると、ワークフローのその時点までのすべての昇格されたプロパティ値が消去されます。たとえば、Sequence アクティビティが次のように定義されているとします。  
  
1.  PromoteValue { Name \= “Count”, Value \= 3}  
  
2.  PromoteValue {Name \= “LastIncrementedAt”, Value \= 1\-1\-2000 }  
  
3.  永続化  
  
4.  PromoteValue {Name \= “Count”, Value \= 4, ClearExistingPromotedData \= true}  
  
5.  永続化  
  
 2 番目の永続化では、`Count` の昇格された値は 4 になります。ただし、`LastIncrementedAt` の昇格された値は `NULL` になります。手順 4. で `ClearExistingPromotedData` を `true` に設定しなかった場合は、2 番目の永続化の後、Count の昇格された値は 4 になります。その結果、`LastIncrementedAt` の昇格された値は 1\-1\-2000 のままです。  
  
### PropertyPromotionActivity  
 このクラス ライブラリには、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 昇格機能の使用を単純化する次のパブリック クラスが含まれています。  
  
#### PromoteValue クラス  
 このクラスは 1 つのプロパティを昇格します。昇格されたプロパティの名前は、構成の `promotedValue` 要素の名前属性と同じである必要があります。このアクティビティは、ワークフロー デザイナーで使用できます。使用例については、「CounterServiceApplication」を参照してください。  
  
```csharp  
public class PromoteValue<T> : CodeActivity  
{  
    public PromoteValue()  
    {  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public string Name { get; set; }  
    public InArgument<T> Value { get; set; }  
}  
  
```  
  
 ClearExistingPromotedData \(Bool\)  
 このアクティビティの前に昇格されたすべての値を消去します。  
  
 Name \(string\)  
 このプロパティを表す名前。これは、構成の \<promotedValue\> 要素の名前属性と同じである必要があります。  
  
 Value \(InArgument\<T\>\)  
 列に格納する変数\/値。  
  
#### PromoteValues クラス  
 複数のプロパティを昇格します。昇格されたプロパティの名前は、構成の `promotedValue` 要素のすべての名前属性と同じである必要があります。使用方法は、`PromoteValue` アクティビティと似ていますが、複数のプロパティを同時に昇格できる点が異なります。このアクティビティは、ワークフロー デザイナーでは使用できません。  
  
```  
public class PromoteValues : CodeActivity  
{  
    public PromoteValues()  
    {  
        this.ValuesToPromote = new Dictionary<string, InArgument>();  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public IDictionary<string, InArgument> ValuesToPromote { get; set; }  
}  
```  
  
#### SqlWorkflowInstanceStorePromotionBehavior  
 `SqlWorkflowInstanceStoreBehavior` から派生します。この派生クラスは、カスタムの永続化参加要素 \(このライブラリの一部でもあります\) をワークフロー拡張機能として追加します。前の 2 つのワークフロー アクティビティの実装は、このカスタムの永続化参加要素に依存しています。  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
  
```  
  
 このクラス ライブラリには、`SqlWorkflowInstanceStorePromotionElement` の `ConfigurationElement` 実装と前の昇格アクティビティで使用されたカスタムの永続化参加要素も含まれています。  
  
### PropertyPromotionActivitySQLSample  
 この SQL ファイルでは、CounterService 昇格セットを持つすべてのインスタンスをクエリするために `[InstancePromotedProperties]` ビューのほかに `[dbo].[CounterService]` ビューも作成されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## 参照  
 [AppFabric のホストおよび永続化のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)