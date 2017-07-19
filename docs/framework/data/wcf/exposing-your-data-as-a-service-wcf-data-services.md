---
title: "サービスとしてのデータの公開 (WCF Data Services) | Microsoft Docs"
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
  - "概要, WCF Data Services"
  - "WCF Data Services, 構成"
  - "WCF Data Services, 概要"
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# サービスとしてのデータの公開 (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を Visual Studio に統合すると、サービスを簡単に定義してデータを [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] フィードとして公開できます。  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを公開するデータ サービスを作成するには、次のような基本的な手順を実行します。  
  
1.  **データ モデルを定義します。** [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) に基づくデータ モデルをネイティブでサポートしています。  詳細については、「[方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)」を参照してください。  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、<xref:System.Linq.IQueryable%601> インターフェイスのインスタンスを返す共通言語ランタイム \(CLR\) オブジェクトに基づくデータ モデルもサポートします。  そのため、.NET Framework のリスト、配列、およびコレクションに基づいてデータ サービスを配置できます。これらのデータ構造での作成、更新、および削除操作を有効にするには、<xref:System.Data.Services.IUpdatable> インターフェイスも実装する必要があります。  詳細については、「[方法: リフレクション プロバイダーを使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)」を参照してください。  
  
     より高度なシナリオの場合、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] には、遅延バインディング データ型に基づいてデータ モデルを定義できるプロバイダーのセットが含まれています。  詳細については、「[カスタム データ サービス プロバイダー](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)」を参照してください。  
  
2.  **データ サービスを作成します。**最も基本的なデータ サービスでは、<xref:System.Data.Services.DataService%601> クラスを継承するクラスを `T` 型 \(エンティティ コンテナーの名前空間修飾名\) と一緒に公開します。  詳細については、「[WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)」を参照してください。  
  
3.  **データ サービスを構成します。**既定では、エンティティ コンテナーによって公開されているリソースへのアクセスは、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] によって無効にされます。<xref:System.Data.Services.DataServiceConfiguration> インターフェイスを使用すると、リソースとサービス操作へのアクセスの構成、サポートされる [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] のバージョンの指定、およびサービス全体のその他の動作 \(バッチ動作、1 つの応答で返すことができるエンティティの最大数など\) の定義を行うことができます。詳細については、「[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)」を参照してください。  
  
 Northwind サンプル データベースに基づく単純なデータ サービスを作成する方法の例については、「[クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)」を参照してください。  
  
## 参照  
 [概要](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)   
 [概要](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)