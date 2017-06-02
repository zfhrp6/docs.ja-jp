---
title: "データ サービスのバージョン管理 (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "バージョン管理 [WCF Data Services]"
  - "バージョン管理, WCF Data Services"
  - "WCF Data Services, バージョン管理"
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# データ サービスのバージョン管理 (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] では、データ サービスを作成できます。これにより、クライアントは、データ モデルに基づく URI を使用してリソースとしてのデータにアクセスできます。  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] では、サービス操作の定義もサポートしています。  ビジネス ニーズの変化、情報テクノロジの要件、その他の問題への対処などのさまざまな理由により、サービスの初期導入後と、場合によっては有効期間中に数回、これらのデータ サービスを変更することが必要になる場合があります。  既存のデータ サービスに変更を加える場合は、新しいバージョンのデータ サービスを定義する必要性や、既存のクライアント アプリケーションへの影響を最小限に抑える最善の方法を検討する必要があります。  ここでは、新しいバージョンのデータ サービスをいつどのように作成するかに関するガイダンスを示します。  さらに、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] が [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルの異なるバージョンをサポートするクライアントとデータ サービスの間の交換どのように処理するかについても説明します。  
  
## WCF Data Service のバージョン管理  
 データ サービスが配置され、データが使用されている状況では、データ サービスに変更を加えることで、既存のクライアント アプリケーションとの間に互換性の問題が発生する可能性があります。  ただし、サービスの全体的なビジネス ニーズを受けて変更が求められることも多いため、クライアント アプリケーションへの影響を最小限に抑えながらデータ サービスの新しいバージョンをいつどのように作成するかを検討する必要があります。  
  
### 新しいバージョンのデータ サービスが推奨されるデータ モデルの変更  
 データ サービスの新しいバージョンを発行するかどうかを検討する際は、さまざまな種類の変更がクライアント アプリケーションに与える影響を理解することが重要です。  データ サービスの新しいバージョンを作成する必要があるデータ サービスへの変更は、次の 2 つのカテゴリに分類できます。  
  
-   サービス コントラクトに対する変更。これには、サービス操作の更新、エンティティ セット \(フィード\) のアクセシビリティへの変更、バージョンの変更、およびサービスの動作に対するその他の変更が含まれます。  
  
-   データ コントラクトに対する変更。これには、データ モデル、フィード形式、またはフィードのカスタマイズが含まれます。  
  
 次の表に、データ サービスの新しいバージョンの発行を考慮する必要がある変更の種類を示します。  
  
|変更の種類|新しいバージョンが必要|新しいバージョンは不要|  
|-----------|-----------------|-----------------|  
|サービス操作|-   新しいパラメーターの追加<br />-   戻り値の型を変更する<br />-   サービス操作を削除する|-   既存のパラメーターを削除する<br />-   新しいサービス操作を追加する|  
|サービスの動作|-   カウント要求を無効にする<br />-   投影のサポートを無効にする<br />-   必要なデータ サービスのバージョンを引き上げる|-   カウント要求を有効にする<br />-   投影のサポートを有効にする<br />-   必要なデータ サービスのバージョンを引き下げる|  
|エンティティ セットのアクセス許可|-   エンティティ セットのアクセス許可を制限する<br />-   応答コードを変更する \(新しい最初の桁の値\)<sup>1</sup>|-   エンティティ セットのアクセス許可の制限を解除する<br />-   応答コードを変更する \(同じ最初の桁の値\)|  
|エンティティのプロパティ|-   既存のプロパティまたはリレーションシップを削除する<br />-   null 非許容のプロパティを追加する<br />-   既存のプロパティを変更する|-   null 許容のプロパティを追加する<sup>2</sup>|  
|エンティティ セット|-   エンティティ セットを削除する|-   派生型を追加する<br />-   基本データ型を変更する<br />-   エンティティ セットを追加する|  
|フィードのカスタマイズ|-   エンティティ プロパティのマッピングを変更する||  
  
 <sup>1</sup> 特定のエラー コードを受信することにクライアント アプリケーションがどの程度厳密に依存しているかによって異なります。  
  
 <sup>2</sup> <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> プロパティを `true` に設定すると、クライアントは、データ サービスによって送信された、クライアント上で定義されていない新しいプロパティを無視します。  ただし、挿入の場合、クライアントによって POST 要求に含められていないプロパティは既定値に設定されます。  更新の場合、クライアントが識別できないプロパティ内の既存のデータは、既定値で上書きされます。  この場合は、更新を MERGE 要求として送信する必要があります \(これは既定の動作です\)。  詳細については、「[データ サービス コンテキストの管理](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)」を参照してください。  
  
### データ サービスのバージョンの管理  
 必要に応じて、サービス コントラクトまたはデータ モデルが更新されたサービスの新しいインスタンスを作成して、データ サービスの新しいバージョンを定義します。  次に、この新しいサービスを、以前のバージョンと区別する新しい URI エンドポイントを使用して公開します。  次に例を示します。  
  
-   古いバージョン: `http://services.odata.org/Northwind/v1/Northwind.svc/`  
  
-   新しいバージョン: `http://services.odata.org/Northwind/v2/Northwind.svc/`  
  
 データ サービスをアップグレードした場合、新しいルート URI を使用するには、新しいデータ サービス メタデータに基づいてクライアントも更新する必要があります。  可能な場合は、新しいバージョンを使用するためのアップグレードが行われていないクライアントをサポートするために、データ サービスの以前のバージョンを保持してください。  データ サービスの古いバージョンは、必要でなくなった時点で削除できます。  データ サービスのエンドポイント URI を外部の構成ファイルに保持することを検討する必要があります。  
  
## OData プロトコルのバージョン  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] の新しいバージョンがリリースされると、データ サービスでサポートされている [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルの同バージョンがクライアント アプリケーションで使用されていない可能性がでてきます。  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] の新しいバージョンをサポートするデータ サービスにアクセスできる古いクライアント アプリケーションもあります。  また、アクセス先のデータ サービスよりも新しいバージョンの [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] をサポートする、新しいバージョンの [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリを使用しているクライアント アプリケーションもあります。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、これらのバージョン管理シナリオを処理するために [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] で提供されるサポートを利用しています。  さらに、データ サービスが使用する [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] のバージョンとは異なるバージョンがクライアントで指定されている場合に、データ モデル メタデータを生成および使用してクライアント データ サービス クラスを作成するためのサポートも備えられています。  詳細については、「[OData: プロトコルのバージョン指定](http://go.microsoft.com/fwlink/?LinkId=186071)」を参照してください。  
  
### バージョンのネゴシエーション  
 クライアントが要求するバージョンにかかわらず、サービスによって使用される [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルの最高バージョンを定義するようにデータ サービスを構成できます。  そのためには、データ サービスで使用される <xref:System.Data.Services.DataServiceBehavior> の <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> プロパティに <xref:System.Data.Services.Common.DataServiceProtocolVersion> の値を指定します。  詳細については、「[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)」を参照してください。  
  
 アプリケーションで [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリを使用してデータ サービスにアクセスする場合、アプリケーションで使用している [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] のバージョンと機能により、ライブラリでは自動的にこれらのヘッダーに正しい値が指定されます。  既定では、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では要求された操作をサポートする最も低いプロトコル バーションが使用されます。  
  
 次の表に、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルの特定のバージョンに対する [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] のサポートが用意されている [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] および [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] のバージョンを示します。  
  
|[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルのバージョン|サポートが用意されているバージョン|  
|------------------------------------------------------------------------------|-----------------------|  
|バージョン 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Service Pack 1 \(SP1\)<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] Version 3|  
|バージョン 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] SP1 の更新プログラム。  更新プログラムは、[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkId=158125) からダウンロードし、インストールできます。<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] Version 4|  
|バージョン 3|-   [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] バージョン 3 をサポートするプレリリース版は、[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkId=203885)からダウンロードし、インストールできます。|  
  
### メタデータのバージョン  
 既定では、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ではデータ モデルを表すために CSDL のバージョン 1.1 が使用されます。  リフレクション プロバイダーまたはカスタム データ サービス プロバイダーに基づくデータ モデルの場合は、常にこの CSDL バージョンが使用されます。  ただし、[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] を使用してデータ モデルを定義している場合は、返される CSDL のバージョンは [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] で使用されるバージョンと同じになります。  CSDL のバージョンは、[スキーマ要素](http://msdn.microsoft.com/ja-jp/396074d8-f99c-4f50-a073-68bce848224f)の名前空間によって決定されます。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] 仕様 [\[MC\-CSDL\]: 概念スキーマ定義ファイル形式](http://go.microsoft.com/fwlink/?LinkId=159072)。  
  
 返されたメタデータの `DataServices` 要素には `DataServiceVersion` 属性も含まれます。この属性は、応答メッセージの `DataServiceVersion` ヘッダーの値と同じです。  [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] の **\[サービス参照の追加\]** ダイアログ ボックスなどのクライアント アプリケーションでは、この情報を使用して、データ サービスをホストする [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] のバージョンと正しく連動するクライアント データ サービス クラスを生成します。  詳細については、「[OData: プロトコルのバージョン指定](http://go.microsoft.com/fwlink/?LinkId=186071)」を参照してください。  
  
## 参照  
 [データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)   
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)