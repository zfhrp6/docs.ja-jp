---
title: DeliveryRequirementsAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e297bfc0499ea3ee8d3dd8395165ca22b2baa1de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="2962f-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="2962f-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="2962f-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="2962f-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2962f-104">構文</span><span class="sxs-lookup"><span data-stu-id="2962f-104">Syntax</span></span>  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2962f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="2962f-105">Methods</span></span>  
 <span data-ttu-id="2962f-106">DeliveryRequirementsAttribute クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="2962f-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2962f-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2962f-107">Properties</span></span>  
 <span data-ttu-id="2962f-108">DeliveryRequirementsAttribute クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="2962f-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="2962f-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="2962f-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="2962f-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="2962f-110">Data type: string</span></span>  
  
 <span data-ttu-id="2962f-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="2962f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2962f-112">サービスのバインドがコントラクトをサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2962f-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="2962f-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="2962f-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="2962f-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="2962f-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="2962f-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="2962f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2962f-116">バインディングが順序付きメッセージをサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2962f-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="2962f-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="2962f-117">TargetContract</span></span>  
 <span data-ttu-id="2962f-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="2962f-118">Data type: string</span></span>  
  
 <span data-ttu-id="2962f-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="2962f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2962f-120">適用先となるコントラクトです。</span><span class="sxs-lookup"><span data-stu-id="2962f-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2962f-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="2962f-121">Requirements</span></span>  
  
|<span data-ttu-id="2962f-122">MOF</span><span class="sxs-lookup"><span data-stu-id="2962f-122">MOF</span></span>|<span data-ttu-id="2962f-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="2962f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2962f-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="2962f-124">Namespace</span></span>|<span data-ttu-id="2962f-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="2962f-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2962f-126">参照</span><span class="sxs-lookup"><span data-stu-id="2962f-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
