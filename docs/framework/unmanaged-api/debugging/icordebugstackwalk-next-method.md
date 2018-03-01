---
title: "ICorDebugStackWalk::Next メソッド"
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
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a776f215d67c381a1c08416927cabd3ccb40afa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="78429-102">ICorDebugStackWalk::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="78429-102">ICorDebugStackWalk::Next Method</span></span>
<span data-ttu-id="78429-103">移動、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)次のフレームにオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="78429-103">Moves the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78429-104">構文</span><span class="sxs-lookup"><span data-stu-id="78429-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="78429-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="78429-105">Return Value</span></span>  
 <span data-ttu-id="78429-106">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="78429-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="78429-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78429-107">HRESULT</span></span>|<span data-ttu-id="78429-108">説明</span><span class="sxs-lookup"><span data-stu-id="78429-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78429-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="78429-109">S_OK</span></span>|<span data-ttu-id="78429-110">ランタイムが正常に次のフレームをアンワインド (「解説」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="78429-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="78429-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78429-111">E_FAIL</span></span>|<span data-ttu-id="78429-112">`ICorDebugStackWalk`オブジェクトを advanced されませんでした。</span><span class="sxs-lookup"><span data-stu-id="78429-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="78429-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="78429-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="78429-114">このアンワインドの結果として、スタックの終わりに達しました。</span><span class="sxs-lookup"><span data-stu-id="78429-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="78429-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="78429-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="78429-116">フレーム ポインターはスタックの最後に、既にそのため、追加のフレームにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="78429-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="78429-117">例外</span><span class="sxs-lookup"><span data-stu-id="78429-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78429-118">コメント</span><span class="sxs-lookup"><span data-stu-id="78429-118">Remarks</span></span>  
 <span data-ttu-id="78429-119">`Next`強化され、メソッド、`ICorDebugStackWalk`オブジェクト呼び出し元のフレームにのみ、ランタイムは、現在のフレームをアンワインドできます。</span><span class="sxs-lookup"><span data-stu-id="78429-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="78429-120">それ以外の場合、オブジェクトは、ランタイムはアンワインドすることが次のフレームを進めます。</span><span class="sxs-lookup"><span data-stu-id="78429-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78429-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="78429-121">Requirements</span></span>  
 <span data-ttu-id="78429-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="78429-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78429-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78429-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78429-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78429-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78429-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78429-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78429-126">参照</span><span class="sxs-lookup"><span data-stu-id="78429-126">See Also</span></span>  
 [<span data-ttu-id="78429-127">ICorDebugStackWalk インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78429-127">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [<span data-ttu-id="78429-128">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78429-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="78429-129">デバッグ</span><span class="sxs-lookup"><span data-stu-id="78429-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
