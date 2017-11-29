---
title: "ICorDebugStackWalk::GetFrame メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.GetFrame Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bef8cfc13727913e9311b5ce847190fe5544dc18
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="a1b26-102">ICorDebugStackWalk::GetFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="a1b26-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="a1b26-103">内の現在のフレームを取得、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a1b26-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1b26-104">構文</span><span class="sxs-lookup"><span data-stu-id="a1b26-104">Syntax</span></span>  
  
```  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1b26-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a1b26-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="a1b26-106">[in]現在のスタック フレームを表す作成されたフレーム オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a1b26-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1b26-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="a1b26-107">Return Value</span></span>  
 <span data-ttu-id="a1b26-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="a1b26-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a1b26-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1b26-109">HRESULT</span></span>|<span data-ttu-id="a1b26-110">説明</span><span class="sxs-lookup"><span data-stu-id="a1b26-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1b26-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1b26-111">S_OK</span></span>|<span data-ttu-id="a1b26-112">ランタイムには、現在のフレームが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="a1b26-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="a1b26-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1b26-113">E_FAIL</span></span>|<span data-ttu-id="a1b26-114">現在のフレームは返されませんでした。</span><span class="sxs-lookup"><span data-stu-id="a1b26-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="a1b26-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a1b26-115">S_FALSE</span></span>|<span data-ttu-id="a1b26-116">現在のフレームは、ネイティブ スタック フレームです。</span><span class="sxs-lookup"><span data-stu-id="a1b26-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="a1b26-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a1b26-117">E_INVALIDARG</span></span>|<span data-ttu-id="a1b26-118">`pFrame` が null です。</span><span class="sxs-lookup"><span data-stu-id="a1b26-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="a1b26-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="a1b26-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="a1b26-120">フレーム ポインターはスタックの最後に、既にそのため、追加のフレームにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="a1b26-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="a1b26-121">例外</span><span class="sxs-lookup"><span data-stu-id="a1b26-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1b26-122">コメント</span><span class="sxs-lookup"><span data-stu-id="a1b26-122">Remarks</span></span>  
 <span data-ttu-id="a1b26-123">`ICorDebugStackWalk`実際のスタック フレームのみを返します。</span><span class="sxs-lookup"><span data-stu-id="a1b26-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="a1b26-124">使用して、 [icordebugthread 3::getactiveinternalframes](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)内部フレームを返します。</span><span class="sxs-lookup"><span data-stu-id="a1b26-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="a1b26-125">(内部フレームは、データ構造体が一時的なデータを格納する、ランタイムによってスタックにプッシュします。)</span><span class="sxs-lookup"><span data-stu-id="a1b26-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1b26-126">要件</span><span class="sxs-lookup"><span data-stu-id="a1b26-126">Requirements</span></span>  
 <span data-ttu-id="a1b26-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a1b26-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1b26-128">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1b26-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1b26-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1b26-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1b26-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1b26-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1b26-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1b26-131">See Also</span></span>  
 [<span data-ttu-id="a1b26-132">ICorDebugStackWalk インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1b26-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [<span data-ttu-id="a1b26-133">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1b26-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a1b26-134">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a1b26-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
