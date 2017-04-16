---
title: "Entity Framework プロバイダー (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services, プロバイダー"
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Entity Framework プロバイダー (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] と同様に、ADO.NET Entity Framework は、エンティティ リレーションシップ モデルの型である Entity Data Model をベースにしています。  Entity Framework は、Entity Data Model の実装 \(*概念モデル*\) に対する操作をデータ ソースに対する同等の操作に変換します。  このことから、Entity Framework はリレーショナル データに基づくデータ サービスの理想的なプロバイダーとして使用でき、また、Entity Framework をサポートするデータ プロバイダーが存在するデータベースであれば、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で使用できます。  現在エンティティ フレームワークをサポートしているデータ ソースのリストについては、「[エンティティ フレームワークのサード パーティ プロバイダー](http://go.microsoft.com/fwlink/?LinkId=143699)」を参照してください。  
  
 概念モデルでは、エンティティ コンテナーはサービスのルートです。  データ サービスでデータを公開する前に、Entity Framework で概念モデルを定義する必要があります。  詳細については、「[方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)」を参照してください。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、エンティティの同時実行トークンを定義できるようにすることで、オプティミスティック同時実行制御モデルをサポートしています。  この同時実行トークンは、エンティティの 1 つ以上のプロパティが含まれており、要求、更新、または削除されているデータに対して行われた変更があるかどうかを判断するためにデータ サービスによって使用されます。  要求内の eTag から取得したトークンの値がエンティティの現在の値と異なる場合、データ サービスで例外が発生します。  プロパティが同時実行トークンの一部であることを示す場合、[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] プロバイダーで定義されているデータ モデルに属性 `ConcurrencyMode="Fixed"` を適用する必要があります。  同時実行トークンには、キー プロパティまたはナビゲーション プロパティを含めることはできません。詳細については、「[データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)」を参照してください。  
  
 Entity Framework の詳細については、「[エンティティ フレームワークの概要](../../../../docs/framework/data/adonet/ef/overview.md)」を参照してください。  
  
## 参照  
 [データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)   
 [リフレクション プロバイダー](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)