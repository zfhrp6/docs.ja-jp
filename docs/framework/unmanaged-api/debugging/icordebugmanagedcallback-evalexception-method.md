---
title: ICorDebugManagedCallback::EvalException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalException
helpviewer_keywords:
- EvalException method [.NET Framework debugging]
- ICorDebugManagedCallback::EvalException method [.NET Framework debugging]
ms.assetid: d6036345-18a3-45c1-a302-b1c6f2dced9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4414bab535b63f55a580e93cc6de9cb0dedc073c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415517"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="6f6de-102">ICorDebugManagedCallback::EvalException メソッド</span><span class="sxs-lookup"><span data-stu-id="6f6de-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="6f6de-103">評価版がハンドルされない例外で終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="6f6de-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f6de-104">構文</span><span class="sxs-lookup"><span data-stu-id="6f6de-104">Syntax</span></span>  
  
```  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f6de-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6f6de-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="6f6de-106">[in]評価が終了したアプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6f6de-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="6f6de-107">[in]評価が終了したスレッドを表す ICorDebugThread オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6f6de-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="6f6de-108">[in]評価を実行するコードを表す ICorDebugEval オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6f6de-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f6de-109">要件</span><span class="sxs-lookup"><span data-stu-id="6f6de-109">Requirements</span></span>  
 <span data-ttu-id="6f6de-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6f6de-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f6de-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f6de-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f6de-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f6de-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f6de-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f6de-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f6de-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f6de-114">See Also</span></span>  
 [<span data-ttu-id="6f6de-115">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6f6de-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
