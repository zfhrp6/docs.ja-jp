---
title: ICorDebugFrame::CreateStepper メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3662ed8a3fda5881b0e0929a830d19b0d805299f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411032"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="66203-102">ICorDebugFrame::CreateStepper メソッド</span><span class="sxs-lookup"><span data-stu-id="66203-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="66203-103">により、デバッガーはこの ICorDebugFrame 基準としたステップ実行の操作を実行するステッパを取得します。</span><span class="sxs-lookup"><span data-stu-id="66203-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66203-104">構文</span><span class="sxs-lookup"><span data-stu-id="66203-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66203-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="66203-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="66203-106">[out]デバッガーは、現在のフレームの基準としたステップ実行の操作を実行できるようにする ICorDebugStepper オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="66203-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66203-107">コメント</span><span class="sxs-lookup"><span data-stu-id="66203-107">Remarks</span></span>  
 <span data-ttu-id="66203-108">フレームがアクティブでない場合ステッパ オブジェクト通常の手順を完了する前に、フレームに返される必要があります。</span><span class="sxs-lookup"><span data-stu-id="66203-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66203-109">要件</span><span class="sxs-lookup"><span data-stu-id="66203-109">Requirements</span></span>  
 <span data-ttu-id="66203-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="66203-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66203-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66203-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66203-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66203-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66203-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66203-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
