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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 712f8a7a153d7255275ff7ebaa647d5a624f8ae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a><span data-ttu-id="5c26b-102">COM+ と ServiceModel でのトランザクションの比較</span><span class="sxs-lookup"><span data-stu-id="5c26b-102">Comparing Transactions in COM+ and ServiceModel</span></span>
<span data-ttu-id="5c26b-103">このトピックでは、トランザクション COM+ サービスの動作を、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 名前空間で定義された <xref:System.ServiceModel> 属性を使用してシミュレートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c26b-103">This topic discusses how to simulate the behavior of a transactional COM+ service using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
## <a name="emulating-com-using-servicemodel-attributes"></a><span data-ttu-id="5c26b-104">ServiceModel 属性を使った COM+ のエミュレート</span><span class="sxs-lookup"><span data-stu-id="5c26b-104">Emulating COM+ Using ServiceModel Attributes</span></span>  
 <span data-ttu-id="5c26b-105">次の表では、<xref:System.EnterpriseServices.TransactionOption> トランザクションの生成に使用される `EnterpriseServices` 列挙体の各値を比較し、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 名前空間で定義された <xref:System.ServiceModel> 属性との関連を示します。</span><span class="sxs-lookup"><span data-stu-id="5c26b-105">The following table compares the <xref:System.EnterpriseServices.TransactionOption> enumeration used to create an `EnterpriseServices` transaction and how they correlate to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
|<span data-ttu-id="5c26b-106">COM+ 属性</span><span class="sxs-lookup"><span data-stu-id="5c26b-106">COM+ attribute</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="5c26b-107"> 属性</span><span class="sxs-lookup"><span data-stu-id="5c26b-107"> attributes</span></span>|  
|---------------------|------------------------------------------------------------------------|  
|<span data-ttu-id="5c26b-108">RequiresNew</span><span class="sxs-lookup"><span data-stu-id="5c26b-108">RequiresNew</span></span>|<span data-ttu-id="5c26b-109"><xref:System.ServiceModel.TransactionFlowAttribute> が <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5c26b-109"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span></span><br /><br /> <span data-ttu-id="5c26b-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> は `true` です。</span><span class="sxs-lookup"><span data-stu-id="5c26b-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="5c26b-111">バインド要素の `TransactionFlow` 属性は `false` です。</span><span class="sxs-lookup"><span data-stu-id="5c26b-111">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="5c26b-112">必須</span><span class="sxs-lookup"><span data-stu-id="5c26b-112">Required</span></span>|<span data-ttu-id="5c26b-113"><xref:System.ServiceModel.TransactionFlowAttribute> が <xref:System.ServiceModel.TransactionFlowOption.Allowed> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5c26b-113"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.Allowed>.</span></span><br /><br /> <span data-ttu-id="5c26b-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> は `true` です。</span><span class="sxs-lookup"><span data-stu-id="5c26b-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="5c26b-115">バインド要素の `TransactionFlow` 属性は `true` です。</span><span class="sxs-lookup"><span data-stu-id="5c26b-115">The `TransactionFlow` attribute in the binding element is `true`.</span></span>|  
|<span data-ttu-id="5c26b-116">サポート状況</span><span class="sxs-lookup"><span data-stu-id="5c26b-116">Supported</span></span>|<span data-ttu-id="5c26b-117">同等の属性はありません。</span><span class="sxs-lookup"><span data-stu-id="5c26b-117">There is no direct equivalent.</span></span> <span data-ttu-id="5c26b-118">一般に、`Required` を指定した場合の動作を採用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5c26b-118">In general, you should adopt the behavior specified for `Required` instead.</span></span>|  
|<span data-ttu-id="5c26b-119">NotSupported</span><span class="sxs-lookup"><span data-stu-id="5c26b-119">NotSupported</span></span>|<span data-ttu-id="5c26b-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> は `false` です。</span><span class="sxs-lookup"><span data-stu-id="5c26b-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `false`.</span></span><br /><br /> <span data-ttu-id="5c26b-121">バインド要素の `TransactionFlow` 属性は `false` です。</span><span class="sxs-lookup"><span data-stu-id="5c26b-121">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="5c26b-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="5c26b-122">Disabled</span></span>|<span data-ttu-id="5c26b-123">同等の属性はありません。</span><span class="sxs-lookup"><span data-stu-id="5c26b-123">There is no direct equivalent.</span></span> <span data-ttu-id="5c26b-124">一般に、`NotSupported` を指定した場合の動作を採用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5c26b-124">In general, you should adopt the behavior specified for `NotSupported` instead.</span></span>|
