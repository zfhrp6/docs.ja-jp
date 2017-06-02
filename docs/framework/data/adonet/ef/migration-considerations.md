---
title: "移行に関する注意事項 (Entity Framework) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# 移行に関する注意事項 (Entity Framework)
[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] Entity Framework には、既存のアプリケーションにとっていくつかの利点があります。  特に重要な利点の 1 つが、概念モデルを使用して、アプリケーションで使用するデータ構造をデータ ソースのスキーマから分離できることです。  これにより、ストレージ モデルやデータ ソース自体の将来の変更が容易になり、その変更を補うための変更をアプリケーションに加える必要がなくなります。  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を使用するメリットについては,「[エンティティ フレームワークの概要](../../../../../docs/framework/data/adonet/ef/overview.md)」および「[Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md)」を参照してください。  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] の利点を活用するために既存のアプリケーションを [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] に移行することができます。  移行作業の一部はすべてのアプリケーションに共通です。  こうした共通の作業には、[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Version 3.5 Service Pack 1 \(SP1\) 以降を使用するようにアプリケーションをアップグレードする作業のほか、モデルおよびマッピングの定義や Entity Framework の構成などが含まれます。  そのほか、アプリケーションを [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] に移行する際には、  移行するアプリケーションの種類やアプリケーションの特定の機能に依存する注意点もあります。  このトピックでは、既存のアプリケーションをアップグレードする際に最適な方法を選択するために役立つ情報を紹介します。  
  
## 全般的な移行の注意点  
 アプリケーションを [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] に移行する際には次の点に注意してください。  
  
-   [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Version 3.5 SP1 以降を使用しているアプリケーションはどれでも Entity Framework に移行できますが、アプリケーションが使用するデータ ソースのデータ プロバイダーで Entity Framework がサポートされている必要があります。  
  
-   データ ソース プロバイダーが Entity Framework をサポートしていても、そのプロバイダーのすべての機能が Entity Framework でサポートされるとは限りません。  
  
-   大規模なアプリケーションや複雑なアプリケーションの場合、アプリケーション全体を一度に Entity Framework に移行する必要はありません。  ただし、Entity Framework を使用しない部分がアプリケーションにある場合、それらの部分については、データ ソースが変更された場合に変更が必要になります。  
  
-   [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] データ プロバイダーを使用してデータ ソースにアクセスするため、Entity Framework が使用するデータ プロバイダー接続をアプリケーションの他の部分と共有できます   \(たとえば、Entity Framework は SqlClient プロバイダーを使用して SQL Server データベースにアクセスします\)。  詳細については、「[Entity Framework 用の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)」を参照してください。  
  
## 共通の移行作業  
 既存アプリケーションの [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] への移行パスは、アプリケーションの種類と既存のデータ アクセス計画の両方に依存します。  ただし、以下の作業は、既存のアプリケーションを [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] に移行する際に常に実行する必要があります。  
  
> [!NOTE]
>  [!INCLUDE[vsOrcas](../../../../../includes/vsorcas-md.md)] 以降で Entity Data Model ツールを使用すると、これらの作業はすべて自動的に実行されます。  詳細については、「[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/ja-jp/dadb058a-c5d9-4c5c-8b01-28044112231d)」を参照してください。  
  
1.  アプリケーションをアップグレードします。  
  
     以前のバージョンの [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] と [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] を使用して作成したプロジェクトは、[!INCLUDE[vsOrcas](../../../../../includes/vsorcas-md.md)] SP1 と [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Version 3.5 SP1 以降を使用するようにアップグレードする必要があります。  
  
2.  モデルおよびマッピングを定義します。  
  
     モデル ファイルとマッピング ファイルでは、概念モデルのエンティティ、データ ソースの構造 \(テーブル、ストアド プロシージャ、ビューなど\)、およびエンティティとデータ ソース構造との間のマッピングを定義します。  詳細については、「[How to: Manually Define the Model and Mapping Files](http://msdn.microsoft.com/ja-jp/d4fd6864-f2a1-48f0-aa32-1e318775a99a)」を参照してください。  
  
     ストレージ モデルに定義されている型は、データ ソースのオブジェクトと名前が一致している必要があります。  また、既存のアプリケーションでデータがオブジェクトとして公開されている場合は、概念モデルに定義するエンティティおよびプロパティの名前を既存のデータ クラスおよびプロパティの名前に一致させる必要があります。  詳細については、「[How to: Customize Modeling and Mapping Files to Work with Custom Objects](http://msdn.microsoft.com/ja-jp/bb40c4db-0121-4e45-a167-8fb06707a708)」を参照してください。  
  
    > [!NOTE]
    >  Entity Data Model デザイナーを使用すると、概念モデルのエンティティの名前を既存のオブジェクトに合わせて変更できます。  詳細については、「[Entity Data Model Designer](http://msdn.microsoft.com/ja-jp/4ccd7ad6-b934-4f7c-82a0-cfd2d4a95faf)」を参照してください。  
  
3.  接続文字列を定義します。  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] で概念モデルに対してクエリを実行する際には特殊な形式の接続文字列を使用します。  この接続文字列は、モデル ファイルとマッピング ファイルに関する情報とデータ ソースへの接続に関する情報をカプセル化したものです。  詳細については、「[接続文字列を定義する方法](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)」を参照してください。  
  
4.  [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] プロジェクトを構成します。  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] アセンブリへの参照とモデル ファイルおよびマッピング ファイルを [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] プロジェクトに追加する必要があります。  これらのマッピング ファイルをプロジェクトに追加することで、接続文字列で指定された場所にアプリケーションと共に配置されるようにすることができます。  詳細については、「[How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/ja-jp/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)」を参照してください。  
  
## 既存のオブジェクトを含むアプリケーションの注意点  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 4 以降では、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は POCO \("plain old" CLR object、永続化非依存オブジェクトとも呼ばれます\) をサポートしています。  ほとんどの場合、既存のオブジェクトを少し変更すれば [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] で使用できます。  詳細については、「[Working with POCO Entities](http://msdn.microsoft.com/ja-jp/5e0fb82a-b6d1-41a1-b37b-c12db61629d3)」を参照してください。アプリケーションを [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] に移行し、Entity Framework ツールによって生成されたデータ クラスを使用することもできます。  詳細については、「[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/ja-jp/dadb058a-c5d9-4c5c-8b01-28044112231d)」を参照してください。  
  
## ADO.NET プロバイダーを使用するアプリケーションの注意点  
 SqlClient などの [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] プロバイダーを使用すると、データ ソースに対するクエリを実行して表形式のデータを取得できます。  データを [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] DataSet に読み込むこともできます。  以下は、既存の [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] プロバイダーを使用するアプリケーションをアップグレードする場合の注意点です。  
  
 データ リーダーを使用して表形式のデータを表示している場合  
 EntityClient プロバイダーを使用して [!INCLUDE[esql](../../../../../includes/esql-md.md)] クエリを実行して、返された <xref:System.Data.EntityClient.EntityDataReader> オブジェクトを列挙処理することも考えられますが、  この方法を使用するのは、データ リーダーを使用して表形式のデータを表示するアプリケーションで、データをオブジェクトに具体化したり、変更を追跡したり、更新を行ったりするための [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] の機能が不要である場合だけにしてください。データ ソースを更新する既存のデータ アクセス コードも引き続き使用できますが、<xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> の <xref:System.Data.EntityClient.EntityConnection> プロパティから既存の接続にアクセスできます。  詳細については、「[Entity Framework 用の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)」を参照してください。  
  
 DataSet を使用している場合  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は、メモリへの保持、変更の追跡、データ バインド、オブジェクトの XML データとしてのシリアル化など、DataSet によって提供される機能の多くを提供します。  詳細については、「[オブジェクトの使用](../../../../../docs/framework/data/adonet/ef/working-with-objects.md)」を参照してください。  
  
 アプリケーションで必要な DataSet の機能が [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] によって提供されない場合も、[!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] を使用して LINQ クエリを活用することができます。  詳細については、「[LINQ to DataSet](../../../../../docs/framework/data/adonet/linq-to-dataset.md)」を参照してください。  
  
## データをコントロールにバインドするアプリケーションの注意点  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] では、データをデータ ソース \(DataSet や [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] データ ソース コントロールなど\) にカプセル化して、それらのデータ コントロールにユーザー インターフェイス要素をバインドすることができます。  以下は、コントロールを Entity Framework データにバインドする場合の注意点です。  
  
 コントロールへのデータ バインド  
 概念モデルに対してクエリを実行すると、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] によって、エンティティ型のインスタンスであるオブジェクトとしてデータが返されます。  それらのオブジェクトは直接コントロールにバインドでき、そのバインドで更新がサポートされます。したがって、<xref:System.Windows.Forms.DataGridView> メソッドが呼び出されると、コントロールのデータ \(<xref:System.Data.Objects.ObjectContext.SaveChanges%2A> の行など\) に対する変更が自動的にデータベースに保存されます。  
  
 クエリの結果を列挙して、データ バインドをサポートする <xref:System.Windows.Forms.DataGridView> などのコントロールにデータを表示するアプリケーションは、そのコントロールを <xref:System.Data.Objects.ObjectQuery%601> の結果にバインドするように変更できます。  
  
 詳細については、「[Binding Objects to Controls](http://msdn.microsoft.com/ja-jp/2fd34855-929b-4303-a91e-4bb69d958f2b)」を参照してください。  
  
 [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] データ ソース コントロール  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] には、[!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] Web アプリケーションのデータ バインドを単純化するために作られたデータ ソース コントロールが含まれています。  詳細については、「[Entity Framework データ ソース コントロール](../Topic/EntityDataSource%20Web%20Server%20Control%20Overview.md)」を参照してください。  
  
## その他の注意事項  
 以下は、特定の種類のアプリケーションを Entity Framework に移行する場合の注意点です。  
  
 データ サービスを公開するアプリケーション  
 Windows Communication Foundation \(WCF\) をベースとする Web サービスやアプリケーションは、XML 要求\/応答メッセージ形式を使用して基になるデータ ソースのデータを公開します。  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] では、バイナリ、XML、または WCF データ コントラクトのシリアル化を使用してエンティティ オブジェクトをシリアル化できます。  バイナリ シリアル化と WCF シリアル化ではオブジェクト グラフの完全なシリアル化がサポートされています。  詳細については、「[Building N\-Tier Applications](http://msdn.microsoft.com/ja-jp/9439d2ba-6b5f-44e8-be65-8a442d922cbb)」を参照してください。  
  
 XML データを使用するアプリケーション  
 オブジェクトのシリアル化を使用すると、  XML データを使用するアプリケーション \(AJAX ベースのインターネット アプリケーションなど\) にデータを提供する  データ サービスを作成できます。  このような場合は [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)] の使用を検討してください。  これらのデータ サービスは Entity Data Model に基づいており、GET、PUT、POST などの標準の Representational State Transfer \(REST\) HTTP アクションを使用したエンティティ データへの動的アクセスを提供します。  詳細については、「[WCF Data Services 4.5](../../../../../docs/framework/data/wcf/index.md)」を参照してください。  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] はネイティブ XML データ型をサポートしていません。  そのため、XML 列を持つテーブルにエンティティをマップすると、その XML 列に対応するエンティティ プロパティは文字列になります。  このような場合は、オブジェクトを切断して XML としてシリアル化することができます。  詳細については、「[Serializing Objects](http://msdn.microsoft.com/ja-jp/06c77f9b-5b2e-4c78-b3e3-8c148ba0ea99)」を参照してください。  
  
 アプリケーションで XML データのクエリ機能が必要な場合も、LINQ to XML を使用して LINQ クエリを活用することができます。  詳細については、「[LINQ to XML](../../../../../ocs/visual-basic/programming-guide/concepts/linq/linq-to-xml.md)」を参照してください。  
  
 状態を保持するアプリケーション  
 [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] Web アプリケーションでは、Web ページやユーザー セッションの状態を保持しなければならないことがよくあります。  <xref:System.Data.Objects.ObjectContext> インスタンス内のオブジェクトは、クライアントのビュー ステートやサーバーのセッション状態に格納できます。格納したオブジェクトを取得して新しいオブジェクト コンテキストに再アタッチすることもできます。  詳細については、「[Attaching and Detaching Objects](http://msdn.microsoft.com/ja-jp/41d5c1ef-1b78-4502-aa10-7e1438d62d23)」を参照してください。  
  
## 参照  
 [配置に関する注意事項](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)   
 [Entity Framework の用語](../../../../../docs/framework/data/adonet/ef/terminology.md)