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
ms.workload: dotnet
ms.openlocfilehash: 6c095afd0513360876e5330a130a4d938e30f8db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="a4c27-102">ICorDebugStackWalk::GetFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="a4c27-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="a4c27-103">内の現在のフレームを取得、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a4c27-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4c27-104">構文</span><span class="sxs-lookup"><span data-stu-id="a4c27-104">Syntax</span></span>  
  
```  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4c27-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a4c27-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="a4c27-106">[in]現在のスタック フレームを表す作成されたフレーム オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a4c27-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4c27-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="a4c27-107">Return Value</span></span>  
 <span data-ttu-id="a4c27-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="a4c27-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a4c27-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a4c27-109">HRESULT</span></span>|<span data-ttu-id="a4c27-110">説明</span><span class="sxs-lookup"><span data-stu-id="a4c27-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a4c27-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4c27-111">S_OK</span></span>|<span data-ttu-id="a4c27-112">ランタイムには、現在のフレームが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="a4c27-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="a4c27-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a4c27-113">E_FAIL</span></span>|<span data-ttu-id="a4c27-114">現在のフレームは返されませんでした。</span><span class="sxs-lookup"><span data-stu-id="a4c27-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="a4c27-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a4c27-115">S_FALSE</span></span>|<span data-ttu-id="a4c27-116">現在のフレームは、ネイティブ スタック フレームです。</span><span class="sxs-lookup"><span data-stu-id="a4c27-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="a4c27-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a4c27-117">E_INVALIDARG</span></span>|<span data-ttu-id="a4c27-118">`pFrame` が null です。</span><span class="sxs-lookup"><span data-stu-id="a4c27-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="a4c27-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="a4c27-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="a4c27-120">フレーム ポインターはスタックの最後に、既にそのため、追加のフレームにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="a4c27-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="a4c27-121">例外</span><span class="sxs-lookup"><span data-stu-id="a4c27-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4c27-122">コメント</span><span class="sxs-lookup"><span data-stu-id="a4c27-122">Remarks</span></span>  
 <span data-ttu-id="a4c27-123">`ICorDebugStackWalk`実際のスタック フレームのみを返します。</span><span class="sxs-lookup"><span data-stu-id="a4c27-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="a4c27-124">使用して、 [icordebugthread 3::getactiveinternalframes](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)内部フレームを返します。</span><span class="sxs-lookup"><span data-stu-id="a4c27-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="a4c27-125">(内部フレームは、データ構造体が一時的なデータを格納する、ランタイムによってスタックにプッシュします。)</span><span class="sxs-lookup"><span data-stu-id="a4c27-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4c27-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="a4c27-126">Requirements</span></span>  
 <span data-ttu-id="a4c27-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a4c27-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4c27-128">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4c27-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4c27-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4c27-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4c27-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4c27-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c27-131">参照</span><span class="sxs-lookup"><span data-stu-id="a4c27-131">See Also</span></span>  
 [<span data-ttu-id="a4c27-132">ICorDebugStackWalk インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4c27-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [<span data-ttu-id="a4c27-133">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4c27-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a4c27-134">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a4c27-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
