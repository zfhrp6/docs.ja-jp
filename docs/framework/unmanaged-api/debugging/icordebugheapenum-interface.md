---
title: "ICorDebugHeapEnum インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapEnum
helpviewer_keywords: ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbc97aec2fc9758df17767188c6b4d044b5016fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="fcbbb-102">ICorDebugHeapEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fcbbb-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="fcbbb-103">マネージ ヒープのオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="fcbbb-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="fcbbb-104">このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="fcbbb-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fcbbb-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="fcbbb-105">Methods</span></span>  
  
|<span data-ttu-id="fcbbb-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="fcbbb-106">Method</span></span>|<span data-ttu-id="fcbbb-107">説明</span><span class="sxs-lookup"><span data-stu-id="fcbbb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fcbbb-108">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="fcbbb-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="fcbbb-109">指定した数を取得[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)マネージ ヒープ オブジェクトに関する情報を格納するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="fcbbb-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcbbb-110">コメント</span><span class="sxs-lookup"><span data-stu-id="fcbbb-110">Remarks</span></span>  
 <span data-ttu-id="fcbbb-111">`ICorDebugHeapEnum`インターフェイスは ICorDebugEnum インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="fcbbb-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="fcbbb-112">`ICorDebugHeapEnum`インスタンスが格納されます[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)を呼び出してインスタンス、 [icordebugprocess 5::enumerateheap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="fcbbb-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="fcbbb-113">各[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)コレクション内のインスタンスは、ヒープにライブ オブジェクトまたはオブジェクトでルートが指定されていませんが、ガベージ コレクターによって収集されていないオブジェクトのいずれかを表します。</span><span class="sxs-lookup"><span data-stu-id="fcbbb-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="fcbbb-114">[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)呼び出すことによって、コレクション内のオブジェクトを列挙することができます、 [icordebugheapenum::next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="fcbbb-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcbbb-115">要件</span><span class="sxs-lookup"><span data-stu-id="fcbbb-115">Requirements</span></span>  
 <span data-ttu-id="fcbbb-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fcbbb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcbbb-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fcbbb-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcbbb-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcbbb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcbbb-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcbbb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcbbb-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="fcbbb-120">See Also</span></span>  
 [<span data-ttu-id="fcbbb-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="fcbbb-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
