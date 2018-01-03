---
title: "ICorDebugGenericValue::SetValue メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGenericValue.SetValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11cb4ab6d32f3dbada25fe42f062fdc2c1fabd17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="16615-102">ICorDebugGenericValue::SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="16615-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="16615-103">指定されたバッファーから新しい値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="16615-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16615-104">構文</span><span class="sxs-lookup"><span data-stu-id="16615-104">Syntax</span></span>  
  
```  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16615-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="16615-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="16615-106">[in]元の値をコピーするバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="16615-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16615-107">コメント</span><span class="sxs-lookup"><span data-stu-id="16615-107">Remarks</span></span>  
 <span data-ttu-id="16615-108">参照型の場合、値はコンテンツではなく、参照します。</span><span class="sxs-lookup"><span data-stu-id="16615-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16615-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="16615-109">Requirements</span></span>  
 <span data-ttu-id="16615-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="16615-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16615-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16615-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16615-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16615-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16615-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16615-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
