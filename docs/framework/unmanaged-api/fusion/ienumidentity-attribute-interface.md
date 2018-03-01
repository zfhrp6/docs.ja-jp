---
title: "IEnumIDENTITY_ATTRIBUTE インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fc77f2106f5063b8db25f375c354a15f9f936e78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ienumidentityattribute-interface"></a><span data-ttu-id="25b59-102">IEnumIDENTITY_ATTRIBUTE インターフェイス</span><span class="sxs-lookup"><span data-stu-id="25b59-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="25b59-103">現在のスコープ内のコード オブジェクトの属性の列挙子として機能します。</span><span class="sxs-lookup"><span data-stu-id="25b59-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25b59-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="25b59-104">Methods</span></span>  
  
|<span data-ttu-id="25b59-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="25b59-105">Method</span></span>|<span data-ttu-id="25b59-106">説明</span><span class="sxs-lookup"><span data-stu-id="25b59-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="25b59-107">新しいインターフェイス ポインターを取得`IEnumIDENTITY_ATTRIBUTE`これと同じメンバーを格納している`IEnumIDENTITY_ATTRIBUTE`です。</span><span class="sxs-lookup"><span data-stu-id="25b59-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="25b59-108">この要素に含まれるデータを書き込みます`IEnumIDENTITY_ATTRIBUTE`指定されたデータ バッファーにします。</span><span class="sxs-lookup"><span data-stu-id="25b59-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="25b59-109">指定した数の現在の位置以降にある属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="25b59-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="25b59-110">これの先頭に、命令ポインターを移動`IEnumIDENTITY_ATTRIBUTE`です。</span><span class="sxs-lookup"><span data-stu-id="25b59-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="25b59-111">指定した数の現在位置の要素では、命令ポインターを前方を移動します。</span><span class="sxs-lookup"><span data-stu-id="25b59-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25b59-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="25b59-112">Requirements</span></span>  
 <span data-ttu-id="25b59-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="25b59-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25b59-114">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="25b59-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="25b59-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25b59-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b59-116">参照</span><span class="sxs-lookup"><span data-stu-id="25b59-116">See Also</span></span>  
 [<span data-ttu-id="25b59-117">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="25b59-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
