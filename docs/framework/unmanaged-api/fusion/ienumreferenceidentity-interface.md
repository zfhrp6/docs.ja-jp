---
title: IEnumReferenceIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ebc9fe36955bac8b93ec95e9a55fc8ac1197d9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429122"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="a31aa-102">IEnumReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a31aa-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="a31aa-103">コレクションの列挙子の役割を果たす`IReferenceIdentity`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a31aa-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a31aa-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a31aa-104">Methods</span></span>  
  
|<span data-ttu-id="a31aa-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a31aa-105">Method</span></span>|<span data-ttu-id="a31aa-106">説明</span><span class="sxs-lookup"><span data-stu-id="a31aa-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="a31aa-107">新しいインターフェイス ポインターを取得`IEnumReferenceIdentity`これと同じメンバーを格納している`IEnumReferenceIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="a31aa-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="a31aa-108">指定した数を取得`IReferenceIdentity`オブジェクト、現在の位置で開始します。</span><span class="sxs-lookup"><span data-stu-id="a31aa-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="a31aa-109">これの先頭に、命令ポインターを移動`IEnumReferenceIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="a31aa-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="a31aa-110">指定した数の現在位置の要素では、命令ポインターを前方を移動します。</span><span class="sxs-lookup"><span data-stu-id="a31aa-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a31aa-111">要件</span><span class="sxs-lookup"><span data-stu-id="a31aa-111">Requirements</span></span>  
 <span data-ttu-id="a31aa-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a31aa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a31aa-113">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="a31aa-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="a31aa-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a31aa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a31aa-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a31aa-115">See Also</span></span>  
 [<span data-ttu-id="a31aa-116">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a31aa-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="a31aa-117">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a31aa-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
