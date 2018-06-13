---
title: ICorDebugHeapEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25f352a3a6dfae69116d6cda2497d55485b951cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417064"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="98997-102">ICorDebugHeapEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98997-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="98997-103">マネージ ヒープのオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="98997-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="98997-104">このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="98997-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98997-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="98997-105">Methods</span></span>  
  
|<span data-ttu-id="98997-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="98997-106">Method</span></span>|<span data-ttu-id="98997-107">説明</span><span class="sxs-lookup"><span data-stu-id="98997-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98997-108">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="98997-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="98997-109">指定した数を取得[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)マネージ ヒープ オブジェクトに関する情報を格納するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="98997-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98997-110">コメント</span><span class="sxs-lookup"><span data-stu-id="98997-110">Remarks</span></span>  
 <span data-ttu-id="98997-111">`ICorDebugHeapEnum`インターフェイスは ICorDebugEnum インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="98997-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="98997-112">`ICorDebugHeapEnum`インスタンスが格納されます[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)を呼び出してインスタンス、 [icordebugprocess 5::enumerateheap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="98997-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="98997-113">各[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)コレクション内のインスタンスは、ヒープにライブ オブジェクトまたはオブジェクトでルートが指定されていませんが、ガベージ コレクターによって収集されていないオブジェクトのいずれかを表します。</span><span class="sxs-lookup"><span data-stu-id="98997-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="98997-114">[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)呼び出すことによって、コレクション内のオブジェクトを列挙することができます、 [icordebugheapenum::next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="98997-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98997-115">要件</span><span class="sxs-lookup"><span data-stu-id="98997-115">Requirements</span></span>  
 <span data-ttu-id="98997-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="98997-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98997-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98997-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98997-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98997-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98997-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98997-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98997-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="98997-120">See Also</span></span>  
 [<span data-ttu-id="98997-121">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98997-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
