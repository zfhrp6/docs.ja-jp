---
title: "System.ServiceModel でのトランザクション サポート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7e54ed3-d1e5-4aa7-a653-1300c6b304eb
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3e01f24af2b6853c7a43377bc0b7f7d338195472
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="transactional-support-in-systemservicemodel"></a><span data-ttu-id="230bc-102">System.ServiceModel でのトランザクション サポート</span><span class="sxs-lookup"><span data-stu-id="230bc-102">Transactional Support in System.ServiceModel</span></span>
<span data-ttu-id="230bc-103">このセクションのトピックでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] が提供するトランザクション機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="230bc-103">The topics in this section describe the transactional functionalities [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] provides.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="230bc-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="230bc-104">In This Section</span></span>  
 [<span data-ttu-id="230bc-105">ServiceModel トランザクションの属性</span><span class="sxs-lookup"><span data-stu-id="230bc-105">ServiceModel Transaction Attributes</span></span>](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 <span data-ttu-id="230bc-106"><xref:System.ServiceModel> サービス用のトランザクションの動作を構成可能な 2 つの標準的な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="230bc-106">Describes the two standard <xref:System.ServiceModel> attributes that enable you to configure the behavior of transactions for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 [<span data-ttu-id="230bc-107">ServiceModel トランザクションの構成</span><span class="sxs-lookup"><span data-stu-id="230bc-107">ServiceModel Transaction Configuration</span></span>](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)  
 <span data-ttu-id="230bc-108">サービスのトランザクションを有効にするために使用できるさまざまな構成設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="230bc-108">Describes the various configuration settings that can be used to enable transaction for a service.</span></span>  
  
 [<span data-ttu-id="230bc-109">トランザクション フローの有効化</span><span class="sxs-lookup"><span data-stu-id="230bc-109">Enabling Transaction Flow</span></span>](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)  
 <span data-ttu-id="230bc-110">トランザクション フローを有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="230bc-110">Describes how to enable transaction flow.</span></span>  
  
 [<span data-ttu-id="230bc-111">方法 : トランザクション サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="230bc-111">How to: Create a Transactional Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-transactional-service.md)  
 <span data-ttu-id="230bc-112">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でトランザクション サービスを作成する実例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="230bc-112">Demonstrates how to create a transactional service in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="230bc-113">トランザクション アプリケーションの診断</span><span class="sxs-lookup"><span data-stu-id="230bc-113">Diagnosing Transactional Applications</span></span>](../../../../docs/framework/wcf/feature-details/diagnosing-transactional-applications.md)  
 <span data-ttu-id="230bc-114">トランザクション アプリケーションをトラブルシューティングするために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に用意されている管理機能および診断機能の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="230bc-114">Describes how to use the management and diagnostics feature in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to troubleshoot your transactional application.</span></span>  
  
 [<span data-ttu-id="230bc-115">COM+ と ServiceModel でのトランザクションの比較</span><span class="sxs-lookup"><span data-stu-id="230bc-115">Comparing Transactions in COM+ and ServiceModel</span></span>](../../../../docs/framework/wcf/feature-details/comparing-transactions-in-com-and-servicemodel.md)  
 <span data-ttu-id="230bc-116">トランザクション COM+ サービスの動作を、<xref:System.ServiceModel> 名前空間に定義されている属性を使用してシミュレートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="230bc-116">Describes how to simulate the behavior of a transactional COM+ service using the attributes provided by the <xref:System.ServiceModel> namespace.</span></span>  
  
 [<span data-ttu-id="230bc-117">エンタープライズ サービスのトランザクション コンポーネントの統合</span><span class="sxs-lookup"><span data-stu-id="230bc-117">Integrating Enterprise Services Transactional Components</span></span>](../../../../docs/framework/wcf/feature-details/integrating-enterprise-services-transactional-components.md)  
 <span data-ttu-id="230bc-118">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のサービスを、エンタープライズ サービスを使用するコードと統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="230bc-118">Describes how to integrate your [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services with code that uses enterprise service.</span></span>
