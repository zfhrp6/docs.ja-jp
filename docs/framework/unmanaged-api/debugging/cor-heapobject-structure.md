---
title: "COR_HEAPOBJECT 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_HEAPOBJECT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_HEAPOBJECT
helpviewer_keywords: COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bcd971853707349bf0d60459cb46b0fea1e8a97b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="corheapobject-structure"></a><span data-ttu-id="99be9-102">COR_HEAPOBJECT 構造体</span><span class="sxs-lookup"><span data-stu-id="99be9-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="99be9-103">マネージ ヒープ上のオブジェクトに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="99be9-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99be9-104">構文</span><span class="sxs-lookup"><span data-stu-id="99be9-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="99be9-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="99be9-105">Members</span></span>  
  
|<span data-ttu-id="99be9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="99be9-106">Member</span></span>|<span data-ttu-id="99be9-107">説明</span><span class="sxs-lookup"><span data-stu-id="99be9-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="99be9-108">メモリ内のオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="99be9-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="99be9-109">(バイト単位)、オブジェクトの合計サイズ。</span><span class="sxs-lookup"><span data-stu-id="99be9-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="99be9-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)オブジェクトの型を表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="99be9-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99be9-111">コメント</span><span class="sxs-lookup"><span data-stu-id="99be9-111">Remarks</span></span>  
 <span data-ttu-id="99be9-112">`COR_HEAPOBJECT`インスタンスを列挙することによって取得できる、 [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)インターフェイス オブジェクトの呼び出しによって設定される、 [icordebugprocess 5::enumerateheap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="99be9-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="99be9-113">A`COR_HEAPOBJECT`インスタンスは、いずれか、マネージ ヒープ上のライブ オブジェクトまたはオブジェクトでルートが指定されていませんが、ガベージ コレクターによって収集されていないオブジェクトに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="99be9-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="99be9-114">パフォーマンス向上のため、`COR_HEAPOBJECT.address`フィールドは、 `CORDB_ADDRESS` ICorDebugValue ではなく、値のインターフェイス デバッグ API の多くで使用される値。</span><span class="sxs-lookup"><span data-stu-id="99be9-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="99be9-115">指定したオブジェクトのアドレスの ICorDebugValue オブジェクトを取得するを渡すことができます、`CORDB_ADDRESS`値を[icordebugprocess 5::getobject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="99be9-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="99be9-116">パフォーマンス向上のため、`COR_HEAPOBJECT.type`フィールドは、 `COR_TYPEID` ICorDebugType ではなく、値のインターフェイス デバッグ API の多くで使用される値。</span><span class="sxs-lookup"><span data-stu-id="99be9-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="99be9-117">指定された型の ID で ICorDebugType オブジェクトを取得することができますを渡します、`COR_TYPEID`値を[icordebugprocess 5::gettypefortypeid](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="99be9-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="99be9-118">`COR_HEAPOBJECT`構造体には、参照カウントの COM インターフェイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="99be9-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="99be9-119">取得する場合、`COR_HEAPOBJECT`を呼び出して列挙子からのインスタンス、 [icordebugheapenum::next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)メソッドを後で参照を解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99be9-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99be9-120">要件</span><span class="sxs-lookup"><span data-stu-id="99be9-120">Requirements</span></span>  
 <span data-ttu-id="99be9-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="99be9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99be9-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99be9-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99be9-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99be9-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99be9-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99be9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99be9-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="99be9-125">See Also</span></span>  
 [<span data-ttu-id="99be9-126">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="99be9-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="99be9-127">デバッグ</span><span class="sxs-lookup"><span data-stu-id="99be9-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
