---
title: "ICorDebugHeapEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a15637f925401f23f9da34e33583c9bc5c014dd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="27d90-102">ICorDebugHeapEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="27d90-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="27d90-103">指定した数を取得[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)マネージ ヒープ オブジェクトに関する情報を格納するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="27d90-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27d90-104">構文</span><span class="sxs-lookup"><span data-stu-id="27d90-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27d90-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="27d90-105">Parameters</span></span>  
 <span data-ttu-id="27d90-106">celt</span><span class="sxs-lookup"><span data-stu-id="27d90-106">celt</span></span>  
 <span data-ttu-id="27d90-107">[in] 取得するオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="27d90-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="27d90-108">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="27d90-108">objects</span></span>  
 <span data-ttu-id="27d90-109">[out]それぞれが指すポインターの配列、 [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)マネージ ヒープのオブジェクトに関する情報を提供するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="27d90-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="27d90-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="27d90-110">pceltFetched</span></span>  
 <span data-ttu-id="27d90-111">[out]数へのポインター [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)で実際に返されたオブジェクト`objects`です。</span><span class="sxs-lookup"><span data-stu-id="27d90-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="27d90-112">`celt` が 1 の場合、この値は`null` になることがあります。</span><span class="sxs-lookup"><span data-stu-id="27d90-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27d90-113">コメント</span><span class="sxs-lookup"><span data-stu-id="27d90-113">Remarks</span></span>  
 <span data-ttu-id="27d90-114">`COR_HEAPOBJECT.type` フィールドは、入れ子になった参照カウントの COM インターフェイスの識別子です。</span><span class="sxs-lookup"><span data-stu-id="27d90-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="27d90-115">この参照は、`ICorDebugHeapEnum::Next` の呼び出し元によって解放される必要があります。</span><span class="sxs-lookup"><span data-stu-id="27d90-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27d90-116">要件</span><span class="sxs-lookup"><span data-stu-id="27d90-116">Requirements</span></span>  
 <span data-ttu-id="27d90-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="27d90-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27d90-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27d90-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27d90-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27d90-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27d90-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27d90-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d90-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="27d90-121">See Also</span></span>  
 [<span data-ttu-id="27d90-122">ICorDebugHeapEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27d90-122">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 [<span data-ttu-id="27d90-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="27d90-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
