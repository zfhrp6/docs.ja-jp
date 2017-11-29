---
title: "IEnumReferenceIdentity インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumReferenceIdentity
helpviewer_keywords: IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 49e1425e8e7e3d09dc36915916b887d2887dccff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="03524-102">IEnumReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="03524-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="03524-103">コレクションの列挙子の役割を果たす`IReferenceIdentity`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="03524-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="03524-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="03524-104">Methods</span></span>  
  
|<span data-ttu-id="03524-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="03524-105">Method</span></span>|<span data-ttu-id="03524-106">説明</span><span class="sxs-lookup"><span data-stu-id="03524-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="03524-107">新しいインターフェイス ポインターを取得`IEnumReferenceIdentity`これと同じメンバーを格納している`IEnumReferenceIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="03524-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="03524-108">指定した数を取得`IReferenceIdentity`オブジェクト、現在の位置で開始します。</span><span class="sxs-lookup"><span data-stu-id="03524-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="03524-109">これの先頭に、命令ポインターを移動`IEnumReferenceIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="03524-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="03524-110">指定した数の現在位置の要素では、命令ポインターを前方を移動します。</span><span class="sxs-lookup"><span data-stu-id="03524-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03524-111">要件</span><span class="sxs-lookup"><span data-stu-id="03524-111">Requirements</span></span>  
 <span data-ttu-id="03524-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="03524-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03524-113">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="03524-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="03524-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03524-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03524-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="03524-115">See Also</span></span>  
 [<span data-ttu-id="03524-116">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="03524-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="03524-117">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="03524-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
