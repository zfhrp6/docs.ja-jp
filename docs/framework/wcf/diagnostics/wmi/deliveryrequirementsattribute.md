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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 40bdc27337daae02795137fc3ac67575787018c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="936b9-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="936b9-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="936b9-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="936b9-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="936b9-104">構文</span><span class="sxs-lookup"><span data-stu-id="936b9-104">Syntax</span></span>  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="936b9-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="936b9-105">Methods</span></span>  
 <span data-ttu-id="936b9-106">DeliveryRequirementsAttribute クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="936b9-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="936b9-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="936b9-107">Properties</span></span>  
 <span data-ttu-id="936b9-108">DeliveryRequirementsAttribute クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="936b9-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="936b9-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="936b9-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="936b9-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="936b9-110">Data type: string</span></span>  
  
 <span data-ttu-id="936b9-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="936b9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="936b9-112">サービスのバインドがコントラクトをサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="936b9-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="936b9-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="936b9-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="936b9-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="936b9-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="936b9-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="936b9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="936b9-116">バインディングが順序付きメッセージをサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="936b9-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="936b9-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="936b9-117">TargetContract</span></span>  
 <span data-ttu-id="936b9-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="936b9-118">Data type: string</span></span>  
  
 <span data-ttu-id="936b9-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="936b9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="936b9-120">適用先となるコントラクトです。</span><span class="sxs-lookup"><span data-stu-id="936b9-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="936b9-121">要件</span><span class="sxs-lookup"><span data-stu-id="936b9-121">Requirements</span></span>  
  
|<span data-ttu-id="936b9-122">MOF</span><span class="sxs-lookup"><span data-stu-id="936b9-122">MOF</span></span>|<span data-ttu-id="936b9-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="936b9-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="936b9-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="936b9-124">Namespace</span></span>|<span data-ttu-id="936b9-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="936b9-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="936b9-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="936b9-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
