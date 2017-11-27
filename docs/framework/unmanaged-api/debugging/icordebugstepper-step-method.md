---
title: "ICorDebugStepper::Step メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.Step
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 914773adefd2ed4c1aa98310fd27a0cbc829bf49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="712a0-102">ICorDebugStepper::Step メソッド</span><span class="sxs-lookup"><span data-stu-id="712a0-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="712a0-103">Icordebugstepper にその格納スレッドおよび必要に応じて、1 ステップに、スレッド内で呼び出される関数をシングル ステップ実行を続行します。</span><span class="sxs-lookup"><span data-stu-id="712a0-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="712a0-104">構文</span><span class="sxs-lookup"><span data-stu-id="712a0-104">Syntax</span></span>  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="712a0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="712a0-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="712a0-106">[in]設定`true`スレッド内で呼び出される関数にステップ インします。</span><span class="sxs-lookup"><span data-stu-id="712a0-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="712a0-107">設定`false`をステップ オーバー関数。</span><span class="sxs-lookup"><span data-stu-id="712a0-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="712a0-108">コメント</span><span class="sxs-lookup"><span data-stu-id="712a0-108">Remarks</span></span>  
 <span data-ttu-id="712a0-109">共通言語ランタイムがこのステッパのフレームで次のマネージ命令を実行するときに、手順を完了します。</span><span class="sxs-lookup"><span data-stu-id="712a0-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="712a0-110">場合`Step`は、ステッパで呼び出されると、マネージ コードのではない、スレッドがマネージ コードの次の命令を実行するとステップが完了します。</span><span class="sxs-lookup"><span data-stu-id="712a0-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="712a0-111">要件</span><span class="sxs-lookup"><span data-stu-id="712a0-111">Requirements</span></span>  
 <span data-ttu-id="712a0-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="712a0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="712a0-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="712a0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="712a0-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="712a0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="712a0-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="712a0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
