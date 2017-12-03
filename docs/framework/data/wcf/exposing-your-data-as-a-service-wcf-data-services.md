---
title: "サービスとしてのデータの公開 (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0c2d664166d9c0b750f6aecf9588a63b8705f0d1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="exposing-your-data-as-a-service-wcf-data-services"></a>サービスとしてのデータの公開 (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]簡単としてデータを公開するサービスを定義するために Visual Studio と統合し、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]フィードします。 公開データ サービスを作成する、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードには、次の基本的な手順が含まれます。  
  
1.  **定義****データ モデル**です。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]基づくデータ モデルをネイティブにサポート、 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)です。 詳細については、次を参照してください。[する方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)です。  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、<xref:System.Linq.IQueryable%601> インターフェイスのインスタンスを返す共通言語ランタイム (CLR) オブジェクトに基づくデータ モデルもサポートします。 そのため、.NET Framework のリスト、配列、およびコレクションに基づいてデータ サービスを配置できます。 これらのデータ構造での作成、更新、および削除操作を有効にするには、<xref:System.Data.Services.IUpdatable> インターフェイスも実装する必要があります。 詳細については、次を参照してください。[する方法: リフレクション プロバイダーを使用してデータ サービスを作成](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)です。  
  
     高度なシナリオは、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]遅延バインディング データ型に基づいてデータ モデルを定義できるプロバイダーのセットが含まれています。 詳細については、次を参照してください。[カスタム データ サービス プロバイダー](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)です。  
  
2.  **データ サービスを作成します。** 最も基本的なデータ サービスでは、 <xref:System.Data.Services.DataService%601> クラスを継承するクラスを `T` 型 (エンティティ コンテナーの名前空間修飾名) と一緒に公開します。 詳細については、「 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)の開発と配置について説明します。  
  
3.  **データ サービスを構成します。** 既定では、 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、エンティティ コンテナーによって公開されているリソースへのアクセスは無効になります。 <xref:System.Data.Services.DataServiceConfiguration> インターフェイスを使用すると、リソースとサービス操作へのアクセスの構成、サポートされる [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] のバージョンの指定、およびサービス全体のその他の動作 (バッチ動作や 1 つの応答で返すことができるエンティティの最大数など) を定義できます。 詳細については、次を参照してください。[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)です。  
  
 Northwind サンプル データベースに基づく単純なデータ サービスを作成する方法の例は、次を参照してください。[クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)です。  
  
## <a name="see-also"></a>関連項目  
 [はじめに](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [概要](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)
