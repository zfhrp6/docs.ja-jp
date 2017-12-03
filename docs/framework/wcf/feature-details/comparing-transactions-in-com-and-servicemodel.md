---
title: "COM+ と ServiceModel でのトランザクションの比較"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5229c872c4843df916cf538b7f2e88e451dc6b9d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a><span data-ttu-id="bb5d8-102">COM+ と ServiceModel でのトランザクションの比較</span><span class="sxs-lookup"><span data-stu-id="bb5d8-102">Comparing Transactions in COM+ and ServiceModel</span></span>
<span data-ttu-id="bb5d8-103">このトピックでは、トランザクション COM+ サービスの動作を、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 名前空間で定義された <xref:System.ServiceModel> 属性を使用してシミュレートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb5d8-103">This topic discusses how to simulate the behavior of a transactional COM+ service using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
## <a name="emulating-com-using-servicemodel-attributes"></a><span data-ttu-id="bb5d8-104">ServiceModel 属性を使った COM+ のエミュレート</span><span class="sxs-lookup"><span data-stu-id="bb5d8-104">Emulating COM+ Using ServiceModel Attributes</span></span>  
 <span data-ttu-id="bb5d8-105">次の表では、<xref:System.EnterpriseServices.TransactionOption> トランザクションの生成に使用される `EnterpriseServices` 列挙体の各値を比較し、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 名前空間で定義された <xref:System.ServiceModel> 属性との関連を示します。</span><span class="sxs-lookup"><span data-stu-id="bb5d8-105">The following table compares the <xref:System.EnterpriseServices.TransactionOption> enumeration used to create an `EnterpriseServices` transaction and how they correlate to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
|<span data-ttu-id="bb5d8-106">COM+ 属性</span><span class="sxs-lookup"><span data-stu-id="bb5d8-106">COM+ attribute</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="bb5d8-107"> 属性</span><span class="sxs-lookup"><span data-stu-id="bb5d8-107"> attributes</span></span>|  
|---------------------|------------------------------------------------------------------------|  
|<span data-ttu-id="bb5d8-108">RequiresNew</span><span class="sxs-lookup"><span data-stu-id="bb5d8-108">RequiresNew</span></span>|<span data-ttu-id="bb5d8-109"><xref:System.ServiceModel.TransactionFlowAttribute> が <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bb5d8-109"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span></span><br /><br /> <span data-ttu-id="bb5d8-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> は `true` です。</span><span class="sxs-lookup"><span data-stu-id="bb5d8-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="bb5d8-111">バインド要素の `TransactionFlow` 属性は `false` です。</span><span class="sxs-lookup"><span data-stu-id="bb5d8-111">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="bb5d8-112">必須</span><span class="sxs-lookup"><span data-stu-id="bb5d8-112">Required</span></span>|<span data-ttu-id="bb5d8-113"><xref:System.ServiceModel.TransactionFlowAttribute> が <xref:System.ServiceModel.TransactionFlowOption.Allowed> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bb5d8-113"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.Allowed>.</span></span><br /><br /> <span data-ttu-id="bb5d8-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> は `true` です。</span><span class="sxs-lookup"><span data-stu-id="bb5d8-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="bb5d8-115">バインド要素の `TransactionFlow` 属性は `true` です。</span><span class="sxs-lookup"><span data-stu-id="bb5d8-115">The `TransactionFlow` attribute in the binding element is `true`.</span></span>|  
|<span data-ttu-id="bb5d8-116">サポート状況</span><span class="sxs-lookup"><span data-stu-id="bb5d8-116">Supported</span></span>|<span data-ttu-id="bb5d8-117">同等の属性はありません。</span><span class="sxs-lookup"><span data-stu-id="bb5d8-117">There is no direct equivalent.</span></span> <span data-ttu-id="bb5d8-118">一般に、`Required` を指定した場合の動作を採用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bb5d8-118">In general, you should adopt the behavior specified for `Required` instead.</span></span>|  
|<span data-ttu-id="bb5d8-119">NotSupported</span><span class="sxs-lookup"><span data-stu-id="bb5d8-119">NotSupported</span></span>|<span data-ttu-id="bb5d8-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> は `false` です。</span><span class="sxs-lookup"><span data-stu-id="bb5d8-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `false`.</span></span><br /><br /> <span data-ttu-id="bb5d8-121">バインド要素の `TransactionFlow` 属性は `false` です。</span><span class="sxs-lookup"><span data-stu-id="bb5d8-121">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="bb5d8-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="bb5d8-122">Disabled</span></span>|<span data-ttu-id="bb5d8-123">同等の属性はありません。</span><span class="sxs-lookup"><span data-stu-id="bb5d8-123">There is no direct equivalent.</span></span> <span data-ttu-id="bb5d8-124">一般に、`NotSupported` を指定した場合の動作を採用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bb5d8-124">In general, you should adopt the behavior specified for `NotSupported` instead.</span></span>|
