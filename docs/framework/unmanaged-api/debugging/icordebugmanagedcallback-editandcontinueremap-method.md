---
title: "ICorDebugManagedCallback::EditAndContinueRemap メソッド"
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
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 90c22b697677ec493b8093117af0a9d1a86268ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="2a123-102">ICorDebugManagedCallback::EditAndContinueRemap メソッド</span><span class="sxs-lookup"><span data-stu-id="2a123-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="2a123-103">このメソッドの使用は推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="2a123-103">This method has been deprecated.</span></span> <span data-ttu-id="2a123-104">統合開発環境 (IDE) に再割り当てイベントが送信されたことに、デバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2a123-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a123-105">構文</span><span class="sxs-lookup"><span data-stu-id="2a123-105">Syntax</span></span>  
  
```  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="2a123-106">コメント</span><span class="sxs-lookup"><span data-stu-id="2a123-106">Remarks</span></span>  
 <span data-ttu-id="2a123-107">`EditAndContinueRemap`メソッドは、更新された関数の古いバージョンのコードの実行が試行されたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2a123-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="2a123-108">共通言語ランタイムの呼び出し、 `EditAndContinueRemap` IDE に再割り当てイベントを送信する方法です。</span><span class="sxs-lookup"><span data-stu-id="2a123-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a123-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="2a123-109">Requirements</span></span>  
 <span data-ttu-id="2a123-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2a123-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a123-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a123-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a123-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a123-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a123-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a123-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a123-114">参照</span><span class="sxs-lookup"><span data-stu-id="2a123-114">See Also</span></span>  
 [<span data-ttu-id="2a123-115">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a123-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
