---
title: "ICorDebugHeapSegmentEnum インターフェイス"
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
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b477631b5920401127d34b2304485bd32c3d78f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="6036b-102">ICorDebugHeapSegmentEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6036b-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="6036b-103">マネージ ヒープのメモリ領域の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="6036b-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="6036b-104">このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="6036b-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6036b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6036b-105">Methods</span></span>  
  
|<span data-ttu-id="6036b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="6036b-106">Method</span></span>|<span data-ttu-id="6036b-107">説明</span><span class="sxs-lookup"><span data-stu-id="6036b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6036b-108">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="6036b-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="6036b-109">指定した数を取得[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)マネージ ヒープの領域についての情報が含まれているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="6036b-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6036b-110">コメント</span><span class="sxs-lookup"><span data-stu-id="6036b-110">Remarks</span></span>  
 <span data-ttu-id="6036b-111">`ICorDebugHeapSegmentEnum`インターフェイスは ICorDebugEnum インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="6036b-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="6036b-112">`ICorDebugHeapSegmentEnum`インスタンスが格納されます[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)を呼び出してインスタンス、 [icordebugprocess 5::enumerateheapregions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="6036b-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="6036b-113">[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)呼び出すことによって、コレクション内のオブジェクトを列挙することができます、 [icordebugheapsegmentenum::next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="6036b-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="6036b-114">`ICorDebugHeapSegmentEnum`コレクション オブジェクトを管理対象のオブジェクトを含む可能性のあるすべてのメモリ領域を列挙しますが、管理対象オブジェクトがそれらの地域で実際に常駐させることは保証されません。</span><span class="sxs-lookup"><span data-stu-id="6036b-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="6036b-115">これには、空または予約済みのメモリ領域に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6036b-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6036b-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="6036b-116">Requirements</span></span>  
 <span data-ttu-id="6036b-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6036b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6036b-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6036b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6036b-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6036b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6036b-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6036b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6036b-121">参照</span><span class="sxs-lookup"><span data-stu-id="6036b-121">See Also</span></span>  
 [<span data-ttu-id="6036b-122">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6036b-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
