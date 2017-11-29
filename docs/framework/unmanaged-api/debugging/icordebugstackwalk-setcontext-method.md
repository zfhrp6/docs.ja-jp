---
title: "ICorDebugStackWalk::SetContext メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.SetContext Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 374092c500d4263a172219c38cbc1b2f0ce293a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="39756-102">ICorDebugStackWalk::SetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="39756-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="39756-103">セット、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)オブジェクトの現在のコンテキストのスレッドの有効なコンテキストにします。</span><span class="sxs-lookup"><span data-stu-id="39756-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39756-104">構文</span><span class="sxs-lookup"><span data-stu-id="39756-104">Syntax</span></span>  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39756-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="39756-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="39756-106">[in]A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)コンテキストは、スタック上のアクティブなフレームからまたはスタックのアンワインドによりコンテキストを取得するかどうかを示すフラグです。</span><span class="sxs-lookup"><span data-stu-id="39756-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="39756-107">[in]割り当てサイズ、`CONTEXT`バッファー。</span><span class="sxs-lookup"><span data-stu-id="39756-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="39756-108">[in]`CONTEXT`バッファー。</span><span class="sxs-lookup"><span data-stu-id="39756-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39756-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="39756-109">Return Value</span></span>  
 <span data-ttu-id="39756-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="39756-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="39756-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="39756-111">HRESULT</span></span>|<span data-ttu-id="39756-112">説明</span><span class="sxs-lookup"><span data-stu-id="39756-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="39756-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="39756-113">S_OK</span></span>|<span data-ttu-id="39756-114">`ICorDebugStackWalk`オブジェクトのコンテキストが正常に設定します。</span><span class="sxs-lookup"><span data-stu-id="39756-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="39756-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="39756-115">E_FAIL</span></span>|<span data-ttu-id="39756-116">`ICorDebugStackWalk`オブジェクトのコンテキストが設定されませんでした。</span><span class="sxs-lookup"><span data-stu-id="39756-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="39756-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="39756-117">E_INVALIDARG</span></span>|<span data-ttu-id="39756-118">コンテキストが null です。</span><span class="sxs-lookup"><span data-stu-id="39756-118">The context is null.</span></span>|  
|<span data-ttu-id="39756-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="39756-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="39756-120">コンテキスト バッファーが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="39756-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="39756-121">例外</span><span class="sxs-lookup"><span data-stu-id="39756-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39756-122">コメント</span><span class="sxs-lookup"><span data-stu-id="39756-122">Remarks</span></span>  
 <span data-ttu-id="39756-123">このメソッドは、スレッドの現在のコンテキストを変更しません。</span><span class="sxs-lookup"><span data-stu-id="39756-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="39756-124">無効なコンテキストを現在のコンテキストに設定すると、スタック ウォーカーにより予期しない結果があります可能性。</span><span class="sxs-lookup"><span data-stu-id="39756-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="39756-125">このコンテキストの正確なビットごとのコピーを取得するには、すぐに呼び出して、 [icordebugstackwalk::getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="39756-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39756-126">要件</span><span class="sxs-lookup"><span data-stu-id="39756-126">Requirements</span></span>  
 <span data-ttu-id="39756-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="39756-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39756-128">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39756-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39756-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39756-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39756-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39756-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39756-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="39756-131">See Also</span></span>  
 [<span data-ttu-id="39756-132">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="39756-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="39756-133">デバッグ</span><span class="sxs-lookup"><span data-stu-id="39756-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
