---
title: ICorDebugEval2::RudeAbort メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0aabff090634f1ecdeec5636336ad1fb77b8b81c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412579"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="4b34f-102">ICorDebugEval2::RudeAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="4b34f-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="4b34f-103">計算の中止この`ICorDebugEval2`は現在を実行します。</span><span class="sxs-lookup"><span data-stu-id="4b34f-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b34f-104">構文</span><span class="sxs-lookup"><span data-stu-id="4b34f-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4b34f-105">コメント</span><span class="sxs-lookup"><span data-stu-id="4b34f-105">Remarks</span></span>  
 <span data-ttu-id="4b34f-106">`RudeAbort` 安全でない状態のまま、デバッグ セッションにそのため、エバリュエーターを保持しているすべてのロックは解放されません。</span><span class="sxs-lookup"><span data-stu-id="4b34f-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="4b34f-107">十分注意してこのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4b34f-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b34f-108">要件</span><span class="sxs-lookup"><span data-stu-id="4b34f-108">Requirements</span></span>  
 <span data-ttu-id="4b34f-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4b34f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b34f-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b34f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b34f-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b34f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b34f-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b34f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
