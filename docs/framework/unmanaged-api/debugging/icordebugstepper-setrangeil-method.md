---
title: ICorDebugStepper::SetRangeIL メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3c24b3a96a03359dc6983bcaac4a800613ff5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420532"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="cff5b-102">ICorDebugStepper::SetRangeIL メソッド</span><span class="sxs-lookup"><span data-stu-id="cff5b-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="cff5b-103">指定する値を設定するかどうかを呼び出す[icordebugstepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)または Microsoft の基準としたネイティブ コードへの相対値の中間 language (MSIL) コードがステップ インされているメソッドの引数を渡すを通じてします。</span><span class="sxs-lookup"><span data-stu-id="cff5b-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cff5b-104">構文</span><span class="sxs-lookup"><span data-stu-id="cff5b-104">Syntax</span></span>  
  
```  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cff5b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cff5b-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="cff5b-106">[in]設定`true`な MSIL コード相対の範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="cff5b-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="cff5b-107">設定`false`範囲がネイティブ コードの基準としたことを指定します。</span><span class="sxs-lookup"><span data-stu-id="cff5b-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="cff5b-108">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="cff5b-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cff5b-109">要件</span><span class="sxs-lookup"><span data-stu-id="cff5b-109">Requirements</span></span>  
 <span data-ttu-id="cff5b-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cff5b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cff5b-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cff5b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cff5b-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cff5b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cff5b-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cff5b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
