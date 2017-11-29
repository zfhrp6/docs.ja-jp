---
title: "CorGCReferenceType 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorGCReferenceType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorGCReferenceType
helpviewer_keywords: CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45ca1e9c6123a4b22a1645d151e49a0dd65addbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="14a12-102">CorGCReferenceType 列挙型</span><span class="sxs-lookup"><span data-stu-id="14a12-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="14a12-103">ガベージ コレクトされる必要のあるオブジェクトのソースを識別します。</span><span class="sxs-lookup"><span data-stu-id="14a12-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14a12-104">構文</span><span class="sxs-lookup"><span data-stu-id="14a12-104">Syntax</span></span>  
  
```  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a><span data-ttu-id="14a12-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="14a12-105">Members</span></span>  
  
|<span data-ttu-id="14a12-106">メンバー名</span><span class="sxs-lookup"><span data-stu-id="14a12-106">Member name</span></span>|<span data-ttu-id="14a12-107">説明</span><span class="sxs-lookup"><span data-stu-id="14a12-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="14a12-108">オブジェクト ハンドル テーブルからの強い参照へのハンドル。</span><span class="sxs-lookup"><span data-stu-id="14a12-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="14a12-109">オブジェクト ハンドル テーブルから固定された強い参照へのハンドル。</span><span class="sxs-lookup"><span data-stu-id="14a12-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="14a12-110">オブジェクト ハンドル テーブルからの弱い参照へのハンドル。</span><span class="sxs-lookup"><span data-stu-id="14a12-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="14a12-111">オブジェクト ハンドル テーブルから弱参照カウント オブジェクトへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="14a12-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="14a12-112">オブジェクト ハンドル テーブルから、参照カウント オブジェクトへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="14a12-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="14a12-113">オブジェクト ハンドル テーブルから、依存するオブジェクトへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="14a12-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="14a12-114">オブジェクト ハンドル テーブルからの非同期固定オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="14a12-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="14a12-115">ガベージ コレクション時に、すべてのオブジェクトおよびオブジェクト ルートの集合的なクロージャの概算サイズを保持する強力なハンドル。</span><span class="sxs-lookup"><span data-stu-id="14a12-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="14a12-116">マネージ スタックからの参照。</span><span class="sxs-lookup"><span data-stu-id="14a12-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="14a12-117">ファイナライザー キューからの参照。</span><span class="sxs-lookup"><span data-stu-id="14a12-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="14a12-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="14a12-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="14a12-119">ハンドル テーブルから強力な参照のみを返します。</span><span class="sxs-lookup"><span data-stu-id="14a12-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="14a12-120">この値を使用して、 [icordebugprocess 5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)メソッドのみです。</span><span class="sxs-lookup"><span data-stu-id="14a12-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="14a12-121">ハンドル テーブルからの弱い参照のみを返します。</span><span class="sxs-lookup"><span data-stu-id="14a12-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="14a12-122">この値を使用して、 [icordebugprocess 5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)メソッドのみです。</span><span class="sxs-lookup"><span data-stu-id="14a12-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="14a12-123">ハンドル テーブルからすべての参照を返します。</span><span class="sxs-lookup"><span data-stu-id="14a12-123">Return all references from the handle table.</span></span> <span data-ttu-id="14a12-124">この値を使用して、 [icordebugprocess 5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)メソッドのみです。</span><span class="sxs-lookup"><span data-stu-id="14a12-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14a12-125">コメント</span><span class="sxs-lookup"><span data-stu-id="14a12-125">Remarks</span></span>  
 <span data-ttu-id="14a12-126">`CorGCReferenceType`列挙体は次のように使用します。</span><span class="sxs-lookup"><span data-stu-id="14a12-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
-   <span data-ttu-id="14a12-127">値として、`type`のフィールド、 [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)構造体、参照、またはハンドルのソースを示します。</span><span class="sxs-lookup"><span data-stu-id="14a12-127">As the value of the `type` field of the [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
-   <span data-ttu-id="14a12-128">として、`types`への引数、 [icordebugprocess 5::enumeratehandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)メソッドを指定した列挙体に含めるハンドルの種類。</span><span class="sxs-lookup"><span data-stu-id="14a12-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14a12-129">要件</span><span class="sxs-lookup"><span data-stu-id="14a12-129">Requirements</span></span>  
 <span data-ttu-id="14a12-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="14a12-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14a12-131">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14a12-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14a12-132">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14a12-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14a12-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14a12-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14a12-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="14a12-134">See Also</span></span>  
 [<span data-ttu-id="14a12-135">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="14a12-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
