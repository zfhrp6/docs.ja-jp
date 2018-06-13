---
title: ICorDebugGenericValue::SetValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83aebad108a743d25b8ea93c99060d10bf5c3980
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413209"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="e85df-102">ICorDebugGenericValue::SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="e85df-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="e85df-103">指定されたバッファーから新しい値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="e85df-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e85df-104">構文</span><span class="sxs-lookup"><span data-stu-id="e85df-104">Syntax</span></span>  
  
```  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e85df-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e85df-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="e85df-106">[in]元の値をコピーするバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e85df-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e85df-107">コメント</span><span class="sxs-lookup"><span data-stu-id="e85df-107">Remarks</span></span>  
 <span data-ttu-id="e85df-108">参照型の場合、値はコンテンツではなく、参照します。</span><span class="sxs-lookup"><span data-stu-id="e85df-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e85df-109">要件</span><span class="sxs-lookup"><span data-stu-id="e85df-109">Requirements</span></span>  
 <span data-ttu-id="e85df-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e85df-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e85df-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e85df-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e85df-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e85df-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e85df-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e85df-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
