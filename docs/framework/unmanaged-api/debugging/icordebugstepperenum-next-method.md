---
title: "ICorDebugStepperEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepperEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a0ad2e3361387875178e8261fad4159a3064da1b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="d8423-102">ICorDebugStepperEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="d8423-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="d8423-103">列挙体の現在位置から指定数の ICorDebugStepper インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="d8423-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8423-104">構文</span><span class="sxs-lookup"><span data-stu-id="d8423-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8423-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d8423-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d8423-106">[in]数`ICorDebugStepper`を取得するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="d8423-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="d8423-107">[out]それぞれが指すポインターの配列、`ICorDebugStepper`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d8423-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d8423-108">[out]数へのポインター`ICorDebugStepper`実際に返されるインスタンス。</span><span class="sxs-lookup"><span data-stu-id="d8423-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="d8423-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="d8423-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8423-110">要件</span><span class="sxs-lookup"><span data-stu-id="d8423-110">Requirements</span></span>  
 <span data-ttu-id="d8423-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d8423-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8423-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8423-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8423-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8423-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8423-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8423-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
