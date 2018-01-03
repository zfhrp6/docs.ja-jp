---
title: "ICorDebugProcess::ClearCurrentException メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.ClearCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 905ade7e5c44861b4ad6e7eb57fe7d3e3e9e3002
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="4d273-102">ICorDebugProcess::ClearCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="4d273-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="4d273-103">特定のスレッドで現在のアンマネージ例外をクリアします。</span><span class="sxs-lookup"><span data-stu-id="4d273-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d273-104">構文</span><span class="sxs-lookup"><span data-stu-id="4d273-104">Syntax</span></span>  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d273-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4d273-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="4d273-106">[in]現在のアンマネージ例外をクリアするスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="4d273-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d273-107">コメント</span><span class="sxs-lookup"><span data-stu-id="4d273-107">Remarks</span></span>  
 <span data-ttu-id="4d273-108">このメソッドを呼び出す前に呼び出します[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)ときに、スレッドがデバッガーによって無視されるアンマネージ例外を報告します。</span><span class="sxs-lookup"><span data-stu-id="4d273-108">Call this method before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="4d273-109">未処理帯域内 (IB) と特定のスレッド上の帯域外の (OOB) イベントの両方をクリアします。</span><span class="sxs-lookup"><span data-stu-id="4d273-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="4d273-110">すべての OOB ブレークポイントとシングル ステップ例外は自動的にクリアされます。</span><span class="sxs-lookup"><span data-stu-id="4d273-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="4d273-111">使用して[icordebugthread 2::interceptcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)を傍受したり、現在のスレッドで例外を管理します。</span><span class="sxs-lookup"><span data-stu-id="4d273-111">Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d273-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="4d273-112">Requirements</span></span>  
 <span data-ttu-id="4d273-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4d273-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d273-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d273-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d273-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d273-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d273-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d273-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
