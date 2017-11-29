---
title: "ICorDebugThread3::CreateStackWalk メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3.CreateStackWalk Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 022b60b50c5e38a776b9076fd4faa62a3c373b06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="20413-102">ICorDebugThread3::CreateStackWalk メソッド</span><span class="sxs-lookup"><span data-stu-id="20413-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="20413-103">作成、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)のスレッドがスタックをアンワインドするオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="20413-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20413-104">構文</span><span class="sxs-lookup"><span data-stu-id="20413-104">Syntax</span></span>  
  
```  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20413-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20413-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="20413-106">[out]アドレスへのポインター、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)のスレッドがスタックをアンワインドするオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="20413-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20413-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="20413-107">Return Value</span></span>  
 <span data-ttu-id="20413-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="20413-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="20413-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20413-109">HRESULT</span></span>|<span data-ttu-id="20413-110">説明</span><span class="sxs-lookup"><span data-stu-id="20413-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20413-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="20413-111">S_OK</span></span>|<span data-ttu-id="20413-112">`ICorDebugStackWalk`オブジェクトが正常に作成します。</span><span class="sxs-lookup"><span data-stu-id="20413-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="20413-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="20413-113">E_FAIL</span></span>|<span data-ttu-id="20413-114">`ICorDebugStackWalk`オブジェクトは作成されませんでした。</span><span class="sxs-lookup"><span data-stu-id="20413-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="20413-115">例外</span><span class="sxs-lookup"><span data-stu-id="20413-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20413-116">コメント</span><span class="sxs-lookup"><span data-stu-id="20413-116">Remarks</span></span>  
 <span data-ttu-id="20413-117">場合、`CreateStackWalk`メソッドが成功した、返された`ICorDebugStackWalk`オブジェクトのコンテキストが、スレッドの現在のコンテキストに設定します。</span><span class="sxs-lookup"><span data-stu-id="20413-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20413-118">要件</span><span class="sxs-lookup"><span data-stu-id="20413-118">Requirements</span></span>  
 <span data-ttu-id="20413-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="20413-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20413-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20413-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20413-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20413-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20413-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20413-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20413-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="20413-123">See Also</span></span>  
 [<span data-ttu-id="20413-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="20413-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="20413-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="20413-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
