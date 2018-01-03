---
title: "ICorDebugProcess5::EnumerateHandles メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHandles
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c9bf9f1a4d565e0af4f3ee34a2805116407027d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="78f18-102">ICorDebugProcess5::EnumerateHandles メソッド</span><span class="sxs-lookup"><span data-stu-id="78f18-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="78f18-103">プロセスで、オブジェクト ハンドルの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="78f18-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f18-104">構文</span><span class="sxs-lookup"><span data-stu-id="78f18-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78f18-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="78f18-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="78f18-106">[in]ビットごとの組み合わせ[CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)コレクションに含めるへのハンドルの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="78f18-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="78f18-107">[out]アドレスへのポインター、 [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)つまりする列挙子オブジェクトのガベージ コレクションします。</span><span class="sxs-lookup"><span data-stu-id="78f18-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78f18-108">コメント</span><span class="sxs-lookup"><span data-stu-id="78f18-108">Remarks</span></span>  
 <span data-ttu-id="78f18-109">`EnumerateHandles`ハンドル テーブルの検査をサポートするヘルパー関数です。</span><span class="sxs-lookup"><span data-stu-id="78f18-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="78f18-110">に似ていますが、 [icordebugprocess 5::enumerategcreferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)点を除いて、メソッドを設定するのではなく、 [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)ガベージ コレクション、すべてのオブジェクトを使用して、コレクション、ハンドル テーブルからハンドルを持つオブジェクトだけが含まれます。</span><span class="sxs-lookup"><span data-stu-id="78f18-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="78f18-111">`types`パラメーターがコレクションに含めるハンドルの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="78f18-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="78f18-112">`types`次の 3 つのメンバーのいずれかを指定できます、 [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="78f18-112">`types` can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
-   <span data-ttu-id="78f18-113">`CorHandleStrongOnly`(ハンドルを厳密な参照のみ)。</span><span class="sxs-lookup"><span data-stu-id="78f18-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
-   <span data-ttu-id="78f18-114">`CorHandleWeakOnly`(弱参照のみを処理)。</span><span class="sxs-lookup"><span data-stu-id="78f18-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
-   <span data-ttu-id="78f18-115">`CorHandleAll`(すべてのハンドル)。</span><span class="sxs-lookup"><span data-stu-id="78f18-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78f18-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="78f18-116">Requirements</span></span>  
 <span data-ttu-id="78f18-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="78f18-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78f18-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78f18-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78f18-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78f18-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78f18-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78f18-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f18-121">参照</span><span class="sxs-lookup"><span data-stu-id="78f18-121">See Also</span></span>  
 [<span data-ttu-id="78f18-122">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="78f18-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="78f18-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="78f18-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
