---
title: ICorDebugProcess::ClearCurrentException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2515e21ec00bd656eafd21a092a27304f7b1769
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419017"
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="b3540-102">ICorDebugProcess::ClearCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="b3540-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="b3540-103">特定のスレッドで現在のアンマネージ例外をクリアします。</span><span class="sxs-lookup"><span data-stu-id="b3540-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3540-104">構文</span><span class="sxs-lookup"><span data-stu-id="b3540-104">Syntax</span></span>  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3540-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b3540-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="b3540-106">[in]現在のアンマネージ例外をクリアするスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="b3540-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3540-107">コメント</span><span class="sxs-lookup"><span data-stu-id="b3540-107">Remarks</span></span>  
 <span data-ttu-id="b3540-108">このメソッドを呼び出す前に呼び出します[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)ときに、スレッドがデバッガーによって無視されるアンマネージ例外を報告します。</span><span class="sxs-lookup"><span data-stu-id="b3540-108">Call this method before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="b3540-109">未処理帯域内 (IB) と特定のスレッド上の帯域外の (OOB) イベントの両方をクリアします。</span><span class="sxs-lookup"><span data-stu-id="b3540-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="b3540-110">すべての OOB ブレークポイントとシングル ステップ例外は自動的にクリアされます。</span><span class="sxs-lookup"><span data-stu-id="b3540-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="b3540-111">使用して[icordebugthread 2::interceptcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)を傍受したり、現在のスレッドで例外を管理します。</span><span class="sxs-lookup"><span data-stu-id="b3540-111">Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3540-112">要件</span><span class="sxs-lookup"><span data-stu-id="b3540-112">Requirements</span></span>  
 <span data-ttu-id="b3540-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b3540-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3540-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3540-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3540-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3540-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3540-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3540-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
