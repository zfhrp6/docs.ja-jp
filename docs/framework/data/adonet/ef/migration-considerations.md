---
title: "移行に関する注意事項 (Entity Framework)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: da287ea76e2300abf1b00f3bbab5897520eb0828
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="migration-considerations-entity-framework"></a>移行に関する注意事項 (Entity Framework)
[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] Entity Framework には、既存のアプリケーションにとっていくつかの利点があります。 特に重要な利点の 1 つが、概念モデルを使用して、アプリケーションで使用するデータ構造をデータ ソースのスキーマから分離できることです。 これにより、ストレージ モデルやデータ ソース自体の将来の変更が容易になり、その変更を補うための変更をアプリケーションに加える必要がなくなります。 使用する利点の詳細についての[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]を参照してください[Entity Framework の概要](../../../../../docs/framework/data/adonet/ef/overview.md)と[Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md)です。  
  
 利点を活用するために、 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]、既存のアプリケーションを移行することができます、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]です。 移行作業の一部はすべてのアプリケーションに共通です。 使用するアプリケーションをアップグレードする一般的なタスクが含まれます、 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 3.5 Service Pack 1 (SP1) 以降のバージョンで、モデルの定義、マッピング、および Entity Framework の構成します。 そのほか、アプリケーションを [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] に移行する際には、 移行するアプリケーションの種類やアプリケーションの特定の機能に依存する注意点もあります。 このトピックでは、既存のアプリケーションをアップグレードする際に最適な方法を選択するために役立つ情報を紹介します。  
  
## <a name="general-migration-considerations"></a>全般的な移行の注意点  
 アプリケーションを [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] に移行する際には次の点に注意してください。  
  
-   使用するアプリケーション、 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] version 3.5 SP1 以降に移行できる、Entity Framework アプリケーションで使用されるデータ ソースのデータ プロバイダーが Entity Framework をサポートしている限り、します。  
  
-   データ ソース プロバイダーが Entity Framework をサポートしていても、そのプロバイダーのすべての機能が Entity Framework でサポートされるとは限りません。  
  
-   大規模なアプリケーションや複雑なアプリケーションの場合、アプリケーション全体を一度に Entity Framework に移行する必要はありません。 ただし、Entity Framework を使用しない部分がアプリケーションにある場合、それらの部分については、データ ソースが変更された場合に変更が必要になります。  
  
-   [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] データ プロバイダーを使用してデータ ソースにアクセスするため、Entity Framework が使用するデータ プロバイダー接続をアプリケーションの他の部分と共有できます  (たとえば、Entity Framework は SqlClient プロバイダーを使用して SQL Server データベースにアクセスします)。 詳細については、次を参照してください。 [Entity Framework の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)です。  
  
## <a name="common-migration-tasks"></a>共通の移行タスク  
 既存アプリケーションの [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] への移行パスは、アプリケーションの種類と既存のデータ アクセス計画の両方に依存します。 ただし、以下の作業は、既存のアプリケーションを [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] に移行する際に常に実行する必要があります。  
  
> [!NOTE]
>  [!INCLUDE[vsOrcas](../../../../../includes/vsorcas-md.md)] 以降で Entity Data Model ツールを使用すると、これらの作業はすべて自動的に実行されます。 詳細については、次を参照してください。[する方法: Entity Data Model ウィザードを使用して](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)です。  
  
1.  アプリケーションをアップグレードします。  
  
     以前のバージョンを使用して作成されたプロジェクト[!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)]と[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]を使用してにアップグレードする必要があります[!INCLUDE[vsOrcas](../../../../../includes/vsorcas-md.md)]SP1 および[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]version 3.5 SP1 以降をします。  
  
2.  モデルおよびマッピングを定義します。  
  
     モデル ファイルとマッピング ファイルでは、概念モデルのエンティティ、データ ソースの構造 (テーブル、ストアド プロシージャ、ビューなど)、およびエンティティとデータ ソース構造との間のマッピングを定義します。 詳細については、次を参照してください。[する方法: モデル ファイルとマッピング ファイルを手動で定義](http://msdn.microsoft.com/en-us/d4fd6864-f2a1-48f0-aa32-1e318775a99a)です。  
  
     ストレージ モデルに定義されている型は、データ ソースのオブジェクトと名前が一致している必要があります。 また、既存のアプリケーションでデータがオブジェクトとして公開されている場合は、概念モデルに定義するエンティティおよびプロパティの名前を既存のデータ クラスおよびプロパティの名前に一致させる必要があります。 詳細については、次を参照してください。[する方法: モデリングをカスタマイズし、カスタム オブジェクトを操作するマッピング ファイル](http://msdn.microsoft.com/en-us/bb40c4db-0121-4e45-a167-8fb06707a708)です。  
  
    > [!NOTE]
    >  Entity Data Model デザイナーを使用すると、概念モデルのエンティティの名前を既存のオブジェクトに合わせて変更できます。 詳細については、次を参照してください。 [Entity Data Model Designer](http://msdn.microsoft.com/en-us/4ccd7ad6-b934-4f7c-82a0-cfd2d4a95faf)です。  
  
3.  接続文字列を定義します。  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] で概念モデルに対してクエリを実行する際には特殊な形式の接続文字列を使用します。 この接続文字列は、モデル ファイルとマッピング ファイルに関する情報とデータ ソースへの接続に関する情報をカプセル化したものです。 詳細については、次を参照してください。[する方法: 接続文字列を定義](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)です。  
  
4.  [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] プロジェクトを構成します。  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] アセンブリへの参照とモデル ファイルおよびマッピング ファイルを [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] プロジェクトに追加する必要があります。 これらのマッピング ファイルをプロジェクトに追加することで、接続文字列で指定された場所にアプリケーションと共に配置されるようにすることができます。 詳細については、次を参照してください。[する方法: Entity Framework プロジェクトを手動で構成](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)です。  
  
## <a name="considerations-for-applications-with-existing-objects"></a>既存のオブジェクトを含むアプリケーションの注意点  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 4 以降では、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は POCO ("plain old" CLR object、永続化非依存オブジェクトとも呼ばれます) をサポートしています。 ほとんどの場合、既存のオブジェクトを少し変更すれば [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] で使用できます。 詳細については、次を参照してください。 [POCO エンティティの操作](http://msdn.microsoft.com/en-us/5e0fb82a-b6d1-41a1-b37b-c12db61629d3)です。 アプリケーションを移行することも、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]し、Entity Framework ツールによって生成されるデータ クラスを使用します。 詳細については、次を参照してください。[する方法: Entity Data Model ウィザードを使用して](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)です。  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>ADO.NET プロバイダーを使用するアプリケーションの注意点  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)]SqlClient などのプロバイダーを使用すると、表形式のデータを返すためのデータ ソースをクエリできます。 データを読み込むことも、[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)]データセット。 以下は、既存の [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] プロバイダーを使用するアプリケーションをアップグレードする場合の注意点です。  
  
 データ リーダーを使用して表形式のデータを表示している場合  
 実行することを検討、 [!INCLUDE[esql](../../../../../includes/esql-md.md)] EntityClient プロバイダーを使用して、返された列挙クエリ<xref:System.Data.EntityClient.EntityDataReader>オブジェクト。 この方法を使用するのは、データ リーダーを使用して表形式のデータを表示するアプリケーションで、データをオブジェクトに具体化したり、変更を追跡したり、更新を行ったりするための [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] の機能が不要である場合だけにしてください。 データ ソースを更新する既存のデータ アクセス コードも引き続き使用できますが、<xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> の <xref:System.Data.EntityClient.EntityConnection> プロパティから既存の接続にアクセスできます。 詳細については、次を参照してください。 [Entity Framework の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)です。  
  
 DataSet を使用している場合  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]追跡、データ バインディング、および XML データとしてオブジェクトをシリアル化に変更をメモリ内の永続化を含むデータセットによって提供される機能の多くを提供します。 詳細については、次を参照してください。[オブジェクトの操作](../../../../../docs/framework/data/adonet/ef/working-with-objects.md)です。  
  
 場合、 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 、機能は提供されない、アプリケーションで必要なデータセットのことができますも活用する LINQ クエリの利点を使用して[!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)]です。 詳細については、「[LINQ to DataSet](../../../../../docs/framework/data/adonet/linq-to-dataset.md)」を参照してください。  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>データをコントロールにバインドするアプリケーションの注意点  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] DataSet やなどのデータ ソース内のデータをカプセル化することができます[!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]データがソース管理、およびそれらのデータ コントロールにユーザー インターフェイス要素をバインドします。 以下は、コントロールを Entity Framework データにバインドする場合の注意点です。  
  
 コントロールへのデータ バインディング  
 概念モデルをクエリするとき、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]エンティティ型のインスタンスであるオブジェクトとしてデータを返します。 これらのオブジェクトは、コントロールに直接バインドすることができ、このバインディングは、更新プログラムをサポートします。 行など、コントロール内のデータを変更することを意味、 <xref:System.Windows.Forms.DataGridView>、自動的にデータベースに保存時に、<xref:System.Data.Objects.ObjectContext.SaveChanges%2A>メソッドが呼び出されます。  
  
 クエリの結果を列挙して、データ バインドをサポートする <xref:System.Windows.Forms.DataGridView> などのコントロールにデータを表示するアプリケーションは、そのコントロールを <xref:System.Data.Objects.ObjectQuery%601> の結果にバインドするように変更できます。  
  
 詳細については、次を参照してください。[コントロールへのバインド オブジェクト](http://msdn.microsoft.com/en-us/2fd34855-929b-4303-a91e-4bb69d958f2b)です。  
  
 [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] データ ソース コントロール  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]でのデータ バインディングを簡略化するためのデータ ソース コントロールが含まれています[!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]Web アプリケーションです。 詳細については、次を参照してください。 [Entity Framework データ ソース コントロール](http://msdn.microsoft.com/library/1f09af00-9578-4744-a029-765710a3c83f)です。  
  
## <a name="other-considerations"></a>その他の注意事項  
 以下は、特定の種類のアプリケーションを Entity Framework に移行する場合の注意点です。  
  
 データ サービスを公開するアプリケーション  
 Windows Communication Foundation (WCF) をベースとする Web サービスやアプリケーションは、XML 要求/応答メッセージ形式を使用して基になるデータ ソースのデータを公開します。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] では、バイナリ、XML、または WCF データ コントラクトのシリアル化を使用してエンティティ オブジェクトをシリアル化できます。 バイナリ シリアル化と WCF シリアル化ではオブジェクト グラフの完全なシリアル化がサポートされています。 詳細については、次を参照してください。 [N 層アプリケーションの構築](http://msdn.microsoft.com/en-us/9439d2ba-6b5f-44e8-be65-8a442d922cbb)です。  
  
 XML データを使用するアプリケーション  
 オブジェクトのシリアル化では、作成することができます[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]データ サービス。 XML データを使用するアプリケーション (AJAX ベースのインターネット アプリケーションなど) にデータを提供する  データ サービスを作成できます。 このような場合は [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)] の使用を検討してください。 これらのデータ サービスは、Entity Data Model に基づいている、標準の Representational State Transfer (REST) HTTP アクションを使用してエンティティ データへの動的アクセスを提供およびなど、GET、PUT、および投稿をします。 詳細については、次を参照してください。 [WCF データ サービス 4.5](../../../../../docs/framework/data/wcf/index.md)です。  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] はネイティブ XML データ型をサポートしていません。 そのため、XML 列を持つテーブルにエンティティをマップすると、その XML 列に対応するエンティティ プロパティは文字列になります。 このような場合は、オブジェクトを切断して XML としてシリアル化することができます。 詳細については、次を参照してください。[オブジェクトのシリアル化](http://msdn.microsoft.com/en-us/06c77f9b-5b2e-4c78-b3e3-8c148ba0ea99)です。  
  
 アプリケーションで XML データのクエリ機能が必要な場合も、LINQ to XML を使用して LINQ クエリを活用することができます。 詳細については、次を参照してください。 [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)です。  
  
 状態を保持するアプリケーション  
 [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]Web アプリケーションは、Web ページまたはユーザー セッションの状態を維持頻繁にする必要があります。 内のオブジェクト、<xref:System.Data.Objects.ObjectContext>インスタンスまたはサーバーで、セッション状態のクライアント ビュー ステートに格納し、後で取得して新しいオブジェクト コンテキストに再アタッチします。 詳細については、次を参照してください。[のアタッチとデタッチ オブジェクト](http://msdn.microsoft.com/en-us/41d5c1ef-1b78-4502-aa10-7e1438d62d23)です。  
  
## <a name="see-also"></a>参照  
 [配置に関する注意事項](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)  
 [Entity Framework の用語](../../../../../docs/framework/data/adonet/ef/terminology.md)
