---
title: ICorDebugStepperEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bd62e4c5476aacf736f2ddfea008790861d931c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419618"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="53c71-102">ICorDebugStepperEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="53c71-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="53c71-103">列挙体の現在位置から指定数の ICorDebugStepper インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="53c71-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53c71-104">構文</span><span class="sxs-lookup"><span data-stu-id="53c71-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53c71-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="53c71-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="53c71-106">[in]数`ICorDebugStepper`を取得するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="53c71-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="53c71-107">[out]それぞれが指すポインターの配列、`ICorDebugStepper`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="53c71-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="53c71-108">[out]数へのポインター`ICorDebugStepper`実際に返されるインスタンス。</span><span class="sxs-lookup"><span data-stu-id="53c71-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="53c71-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="53c71-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53c71-110">要件</span><span class="sxs-lookup"><span data-stu-id="53c71-110">Requirements</span></span>  
 <span data-ttu-id="53c71-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="53c71-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53c71-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53c71-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53c71-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53c71-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53c71-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53c71-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
