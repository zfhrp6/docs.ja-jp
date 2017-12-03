---
title: "Entity Framework プロバイダー (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26c054e3cc9dbf920ab280df43d97acdb90ca055
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="entity-framework-provider-wcf-data-services"></a><span data-ttu-id="46078-102">Entity Framework プロバイダー (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="46078-102">Entity Framework Provider (WCF Data Services)</span></span>
<span data-ttu-id="46078-103">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] と同様に、ADO.NET Entity Framework は、エンティティ リレーションシップ モデルの型である Entity Data Model をベースにしています。</span><span class="sxs-lookup"><span data-stu-id="46078-103">Like [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], the ADO.NET Entity Framework is based on the Entity Data Model, which is a type of entity-relationship model.</span></span> <span data-ttu-id="46078-104">Entity Framework と呼ばれる、Entity Data Model の実装に対して操作を変換する、*概念モデル*、データ ソースに対する同等の操作にします。</span><span class="sxs-lookup"><span data-stu-id="46078-104">The Entity Framework translates operations against its implementation of the Entity Data Model, which is called the *conceptual model*, into equivalent operations against a data source.</span></span> <span data-ttu-id="46078-105">このことから、Entity Framework はリレーショナル データに基づくデータ サービスの理想的なプロバイダーとして使用でき、また、Entity Framework をサポートするデータ プロバイダーが存在するデータベースであれば、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で使用できます。</span><span class="sxs-lookup"><span data-stu-id="46078-105">This makes the Entity Framework an ideal provider for data services that are based on relational data, and any database that has a data provider that supports the Entity Framework can be used with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span> <span data-ttu-id="46078-106">現在、Entity Framework をサポートするデータ ソースの一覧は、次を参照してください。 [Entity Framework 用のサード パーティ プロバイダー](http://go.microsoft.com/fwlink/?LinkId=143699)です。</span><span class="sxs-lookup"><span data-stu-id="46078-106">For a list of the data sources that currently support the Entity Framework, see [Third-Party Providers for the Entity Framework](http://go.microsoft.com/fwlink/?LinkId=143699).</span></span>  
  
 <span data-ttu-id="46078-107">概念モデルでは、エンティティ コンテナーはサービスのルートです。</span><span class="sxs-lookup"><span data-stu-id="46078-107">In a conceptual model, the entity container is the root of the service.</span></span> <span data-ttu-id="46078-108">データ サービスでデータを公開する前に、Entity Framework で概念モデルを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46078-108">You must define a conceptual model in the Entity Framework before the data can be exposed by a data service.</span></span> <span data-ttu-id="46078-109">詳細については、次を参照してください。[する方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)です。</span><span class="sxs-lookup"><span data-stu-id="46078-109">For more information, see [How to: Create a Data Service Using an ADO.NET Entity Framework Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="46078-110">有効にすると、エンティティの同時実行トークンを定義するには、オプティミスティック同時実行制御モデルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="46078-110"> supports the optimistic concurrency model by enabling you to define a concurrency token for an entity.</span></span> <span data-ttu-id="46078-111">この同時実行トークンは、エンティティの 1 つ以上のプロパティが含まれており、要求、更新、または削除されているデータに対して行われた変更があるかどうかを判断するためにデータ サービスによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="46078-111">This concurrency token, which includes one or more properties of the entity, is used by the data service to determine whether a change has occurred in the data that is being requested, updated, or deleted.</span></span> <span data-ttu-id="46078-112">要求内の eTag から取得したトークンの値がエンティティの現在の値と異なる場合、データ サービスで例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="46078-112">When token values obtained from the eTag in the request differ from the current values of the entity, an exception is raised by the data service.</span></span> <span data-ttu-id="46078-113">プロパティが同時実行トークンの一部であることを示す場合、`ConcurrencyMode="Fixed"` プロバイダーで定義されているデータ モデルに属性 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46078-113">To indicate that a property is part of the concurrency token, you must apply the attribute `ConcurrencyMode="Fixed"` in the data model defined by the [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] provider.</span></span> <span data-ttu-id="46078-114">同時実行トークンには、キー プロパティまたはナビゲーション プロパティを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="46078-114">The concurrency token cannot include a key property or a navigation property.</span></span> <span data-ttu-id="46078-115">詳細については、次を参照してください。[データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="46078-115">For more information, see [Updating the Data Service](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="46078-116">Entity Framework の詳細については、次を参照してください。 [Entity Framework の概要](../../../../docs/framework/data/adonet/ef/overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="46078-116">To learn more about the Entity Framework, see [Entity Framework Overview](../../../../docs/framework/data/adonet/ef/overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46078-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="46078-117">See Also</span></span>  
 [<span data-ttu-id="46078-118">データ サービス プロバイダー</span><span class="sxs-lookup"><span data-stu-id="46078-118">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="46078-119">リフレクション プロバイダー</span><span class="sxs-lookup"><span data-stu-id="46078-119">Reflection Provider</span></span>](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)  
 [<span data-ttu-id="46078-120">エンティティ データ モデル</span><span class="sxs-lookup"><span data-stu-id="46078-120">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
