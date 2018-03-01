---
title: "ICorDebugThread::CreateEval メソッド"
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
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 766677d9eef60c811c8537bc60bb8db29dd988c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="e9fe2-102">ICorDebugThread::CreateEval メソッド</span><span class="sxs-lookup"><span data-stu-id="e9fe2-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="e9fe2-103">収集し、この ICorDebugThread の機能を公開する ICorDebugEval オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e9fe2-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9fe2-104">構文</span><span class="sxs-lookup"><span data-stu-id="e9fe2-104">Syntax</span></span>  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9fe2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e9fe2-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="e9fe2-106">[out]アドレスへのポインター、`ICorDebugEval`を収集し、このスレッドの機能を公開するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e9fe2-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9fe2-107">コメント</span><span class="sxs-lookup"><span data-stu-id="e9fe2-107">Remarks</span></span>  
 <span data-ttu-id="e9fe2-108">評価オブジェクトは、計算を実行する前に、スレッドで新しいチェーンにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="e9fe2-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="e9fe2-109">これにより、現在実行中のスレッドで評価が完了するまで計算が中断します。</span><span class="sxs-lookup"><span data-stu-id="e9fe2-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9fe2-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="e9fe2-110">Requirements</span></span>  
 <span data-ttu-id="e9fe2-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e9fe2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9fe2-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9fe2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9fe2-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9fe2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9fe2-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9fe2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
