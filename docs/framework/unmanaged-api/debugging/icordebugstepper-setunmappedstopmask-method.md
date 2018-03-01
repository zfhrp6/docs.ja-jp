---
title: "ICorDebugStepper::SetUnmappedStopMask メソッド"
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
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2fffd523caef6bba1b495f9b8a257f57bd8955af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="eb006-102">ICorDebugStepper::SetUnmappedStopMask メソッド</span><span class="sxs-lookup"><span data-stu-id="eb006-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="eb006-103">マップ解除したコードの実行が停止しメッセージの種類を指定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="eb006-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb006-104">構文</span><span class="sxs-lookup"><span data-stu-id="eb006-104">Syntax</span></span>  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb006-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eb006-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="eb006-106">[in]デバッガーが実行を停止はマップ解除したコードの種類を指定する CorDebugUnmappedStop 列挙型の値です。</span><span class="sxs-lookup"><span data-stu-id="eb006-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="eb006-107">既定値は、STOP_OTHER_UNMAPPED です。</span><span class="sxs-lookup"><span data-stu-id="eb006-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="eb006-108">STOP_UNMANAGED 値で、相互運用機能デバッグでのみです。</span><span class="sxs-lookup"><span data-stu-id="eb006-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb006-109">コメント</span><span class="sxs-lookup"><span data-stu-id="eb006-109">Remarks</span></span>  
 <span data-ttu-id="eb006-110">マップされていないコードの種類を指定するフラグが設定されている場合は、実行を停止、デバッガーには、Microsoft intermediate language (MSIL) に対応するマッピングされていないことジャスト イン タイム (JIT) コンパイルが検出されると、それ以外の場合、透過的にステップ実行は続行されます。</span><span class="sxs-lookup"><span data-stu-id="eb006-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="eb006-111">デバッガーを使用していない、ステッパ メソッドを入力する場合は、マップされていないコードをステップされませんとは限りません。</span><span class="sxs-lookup"><span data-stu-id="eb006-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb006-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="eb006-112">Requirements</span></span>  
 <span data-ttu-id="eb006-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="eb006-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb006-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb006-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb006-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb006-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb006-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb006-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
