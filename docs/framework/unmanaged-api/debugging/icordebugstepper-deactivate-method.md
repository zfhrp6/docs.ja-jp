---
title: ICorDebugStepper::Deactivate メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Deactivate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bcd7bfb52cadf740d8fe3cb92a09b071f530b7ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417402"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="144ba-102">ICorDebugStepper::Deactivate メソッド</span><span class="sxs-lookup"><span data-stu-id="144ba-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="144ba-103">Icordebugstepper にすると、受信した最後のステップ コマンドをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="144ba-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="144ba-104">構文</span><span class="sxs-lookup"><span data-stu-id="144ba-104">Syntax</span></span>  
  
```  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="144ba-105">コメント</span><span class="sxs-lookup"><span data-stu-id="144ba-105">Remarks</span></span>  
 <span data-ttu-id="144ba-106">最近の受信ステップ コマンドが取り消された後、新しいステップのコマンドを発行できます。</span><span class="sxs-lookup"><span data-stu-id="144ba-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="144ba-107">要件</span><span class="sxs-lookup"><span data-stu-id="144ba-107">Requirements</span></span>  
 <span data-ttu-id="144ba-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="144ba-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="144ba-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="144ba-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="144ba-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="144ba-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="144ba-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="144ba-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
