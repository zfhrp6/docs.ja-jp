---
title: "データ サービスのバージョン管理 (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 545096292f34566b4bb6c3c44bb20ddac426af26
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="data-service-versioning-wcf-data-services"></a>データ サービスのバージョン管理 (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]クライアントは、Uri を使用して、データ モデルに基づいたリソースとしてデータをアクセスできるように、データ サービスを作成することができます。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] では、サービス操作の定義もサポートしています。 ビジネス ニーズの変化、情報テクノロジの要件、その他の問題への対処などのさまざまな理由により、サービスの初期導入後と、場合によっては有効期間中に数回、これらのデータ サービスを変更することが必要になる場合があります。 既存のデータ サービスに変更を加える場合は、新しいバージョンのデータ サービスを定義する必要性や、既存のクライアント アプリケーションへの影響を最小限に抑える最善の方法を検討する必要があります。 ここでは、新しいバージョンのデータ サービスをいつどのように作成するかに関するガイダンスを示します。 さらに、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] が [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルの異なるバージョンをサポートするクライアントとデータ サービスの間の交換どのように処理するかについても説明します。  
  
## <a name="versioning-a-wcf-data-service"></a>WCF Data Service のバージョン管理  
 データ サービスが配置され、データが使用されている状況では、データ サービスに変更を加えることで、既存のクライアント アプリケーションとの間に互換性の問題が発生する可能性があります。 ただし、サービスの全体的なビジネス ニーズを受けて変更が求められることも多いため、クライアント アプリケーションへの影響を最小限に抑えながらデータ サービスの新しいバージョンをいつどのように作成するかを検討する必要があります。  
  
### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>新しいバージョンのデータ サービスが推奨されるデータ モデルの変更  
 データ サービスの新しいバージョンを発行するかどうかを検討する際は、さまざまな種類の変更がクライアント アプリケーションに与える影響を理解することが重要です。 データ サービスの新しいバージョンを作成する必要があるデータ サービスへの変更は、次の 2 つのカテゴリに分類できます。  
  
-   サービス コントラクトに対する変更。これには、サービス操作の更新、エンティティ セット (フィード) のアクセシビリティへの変更、バージョンの変更、およびサービスの動作に対するその他の変更が含まれます。  
  
-   データ コントラクトに対する変更。これには、データ モデル、フィード形式、またはフィードのカスタマイズが含まれます。  
  
 次の表に、データ サービスの新しいバージョンの発行を考慮する必要がある変更の種類を示します。  
  
|変更の種類|新しいバージョンが必要|新しいバージョンは不要|  
|--------------------|----------------------------|----------------------------|  
|サービス操作|新しいパラメーターを追加します。<br />戻り値の型の変更<br />-サービス操作を削除します。|-既存のパラメーターを削除します。<br />-新しいサービス操作を追加します。|  
|サービスの動作|-カウント要求を無効にします。<br />-投影のサポートを無効にします。<br />-必要なデータ サービス バージョンを増やす|-カウント要求を有効にします。<br />-投影のサポートを有効にします。<br />-必要なデータ サービス バージョンを減らす|  
|エンティティ セットのアクセス許可|-エンティティ セットのアクセス許可を制限します。<br />-応答コードを変更する (新しい最初の桁の値) <sup>1</sup>|-エンティティ セットのアクセス許可を緩和します。<br />-応答コードを変更する (同じ最初の桁の値)|  
|エンティティのプロパティ|-既存のプロパティまたはリレーションシップを削除します。<br />-Null 非許容のプロパティを追加します。<br />-既存のプロパティを変更します。|Null 許容のプロパティを追加<sup>2</sup>|  
|エンティティ セット|-エンティティ セットを削除します。|-派生型を追加します。<br />基本型を変更します。<br />エンティティ セットを追加します。|  
|フィードのカスタマイズ|-エンティティ プロパティのマッピングを変更します。||  
  
 <sup>1</sup>これが固有のエラー コードを受け取ると、クライアント アプリケーションが依存しているどの程度厳密に依存しています。  
  
 <sup>2</sup>設定することができます、<xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A>プロパティを`true`にクライアントがクライアントで定義されていないデータ サービスによって送信された新しいプロパティを無視します。 ただし、挿入の場合、クライアントによって POST 要求に含められていないプロパティは既定値に設定されます。 更新の場合、クライアントが識別できないプロパティ内の既存のデータは、既定値で上書きされます。 この場合は、更新を MERGE 要求として送信する必要があります (これは既定の動作です)。 詳細については、次を参照してください。[データ サービス コンテキストを管理する](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)です。  
  
### <a name="how-to-version-a-data-service"></a>データ サービスのバージョンの管理  
 必要に応じて、サービス コントラクトまたはデータ モデルが更新されたサービスの新しいインスタンスを作成して、データ サービスの新しいバージョンを定義します。 次に、この新しいサービスを、以前のバージョンと区別する新しい URI エンドポイントを使用して公開します。 次に例を示します。  
  
-   古いバージョン: `http://services.odata.org/Northwind/v1/Northwind.svc/`  
  
-   新しいバージョン: `http://services.odata.org/Northwind/v2/Northwind.svc/`  
  
 データ サービスをアップグレードした場合、新しいルート URI を使用するには、新しいデータ サービス メタデータに基づいてクライアントも更新する必要があります。 可能な場合は、新しいバージョンを使用するためのアップグレードが行われていないクライアントをサポートするために、データ サービスの以前のバージョンを保持してください。 データ サービスの古いバージョンは、必要でなくなった時点で削除できます。 データ サービスのエンドポイント URI を外部の構成ファイルに保持することを検討する必要があります。  
  
## <a name="odata-protocol-versions"></a>OData プロトコルのバージョン  
 新しいバージョンとして[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]がリリースされると、クライアント アプリケーションは使用されないものと同じバージョンの[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]データ サービスによってサポートされているプロトコルです。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] の新しいバージョンをサポートするデータ サービスにアクセスできる古いクライアント アプリケーションもあります。 クライアント アプリケーションが、新しいバージョンを使用しても可能性があります、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]のより新しいバージョンをサポートするクライアント ライブラリ[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]アクセスされているデータ サービス バージョンよりもします。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]によって提供されるサポートを利用[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]このようなバージョン管理シナリオを処理します。 生成して、クライアントが別のバージョンを使用する場合、クライアント データ サービス クラスを作成するデータ モデルのメタデータを使用してサポートされて[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]データ サービスを使用します。 詳細については、次を参照してください。 [OData: プロトコルのバージョン管理](http://go.microsoft.com/fwlink/?LinkId=186071)です。  
  
### <a name="version-negotiation"></a>バージョンのネゴシエーション  
 最新バージョンを定義するデータ サービスを構成することができます、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]クライアントから要求されたバージョンに関係なく、サービスによって使用されるプロトコル。 こうことを指定して、<xref:System.Data.Services.Common.DataServiceProtocolVersion>値を<xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A>のプロパティ、<xref:System.Data.Services.DataServiceBehavior>データ サービスで使用します。 詳細については、次を参照してください。[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)です。  
  
 アプリケーションで [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリを使用してデータ サービスにアクセスする場合、アプリケーションで使用している [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] のバージョンと機能により、ライブラリでは自動的にこれらのヘッダーに正しい値が指定されます。 既定では、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]要求された操作をサポートする最も低いプロトコルのバージョンを使用します。  
  
 次の表に、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] プロトコルの特定のバージョンに対する [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] のサポートが用意されている [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] および [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] のバージョンを示します。  
  
|[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルのバージョン|サポートが用意されているバージョン|  
|-----------------------------------------------------------------------------------|----------------------------|  
|バージョン 1|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]Service Pack 1 (SP1)<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)]バージョン 3|  
|バージョン 2|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-更新プログラムを[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]SP1。 ダウンロードしてから、更新プログラムをインストールすることができます、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkId=158125)です。<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)]バージョン 4|  
|バージョン 3|-ダウンロードしてインストールをサポートするプレリリース バージョン[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]からバージョン 3、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkId=203885)です。|  
  
### <a name="metadata-versions"></a>メタデータのバージョン  
 既定では、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ではデータ モデルを表すために CSDL のバージョン 1.1 が使用されます。 リフレクション プロバイダーまたはカスタム データ サービス プロバイダーに基づくデータ モデルの場合は、常にこの CSDL バージョンが使用されます。 ただし、[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] を使用してデータ モデルを定義している場合は、返される CSDL のバージョンは [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] で使用されるバージョンと同じになります。 CSDL のバージョンはの名前空間によって決定されます、[スキーマ要素](http://msdn.microsoft.com/en-us/396074d8-f99c-4f50-a073-68bce848224f)です。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]仕様[ \[MC-CSDL\]: 概念スキーマ定義ファイル形式](http://go.microsoft.com/fwlink/?LinkId=159072)です。  
  
 返されたメタデータの `DataServices` 要素には `DataServiceVersion` 属性も含まれます。この属性は、応答メッセージの `DataServiceVersion` ヘッダーの値と同じです。 クライアント アプリケーションなど、**サービス参照の追加** ダイアログ ボックスで[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]、この情報を使用してクライアント データ サービス クラスのバージョンで正常に機能を生成する[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]データ サービスをホストします。 詳細については、次を参照してください。 [OData: プロトコルのバージョン管理](http://go.microsoft.com/fwlink/?LinkId=186071)です。  
  
## <a name="see-also"></a>関連項目  
 [データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
