---
title: "ICorDebugManagedCallback::EditAndContinueRemap メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.EditAndContinueRemap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e45cf5376f0c8b4fbe76f56e3adcce22b1ef5c88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="724f2-102">ICorDebugManagedCallback::EditAndContinueRemap メソッド</span><span class="sxs-lookup"><span data-stu-id="724f2-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="724f2-103">このメソッドの使用は推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="724f2-103">This method has been deprecated.</span></span> <span data-ttu-id="724f2-104">統合開発環境 (IDE) に再割り当てイベントが送信されたことに、デバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="724f2-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="724f2-105">構文</span><span class="sxs-lookup"><span data-stu-id="724f2-105">Syntax</span></span>  
  
```  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="724f2-106">コメント</span><span class="sxs-lookup"><span data-stu-id="724f2-106">Remarks</span></span>  
 <span data-ttu-id="724f2-107">`EditAndContinueRemap`メソッドは、更新された関数の古いバージョンのコードの実行が試行されたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="724f2-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="724f2-108">共通言語ランタイムの呼び出し、 `EditAndContinueRemap` IDE に再割り当てイベントを送信する方法です。</span><span class="sxs-lookup"><span data-stu-id="724f2-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="724f2-109">要件</span><span class="sxs-lookup"><span data-stu-id="724f2-109">Requirements</span></span>  
 <span data-ttu-id="724f2-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="724f2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="724f2-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="724f2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="724f2-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="724f2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="724f2-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="724f2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="724f2-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="724f2-114">See Also</span></span>  
 [<span data-ttu-id="724f2-115">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="724f2-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
