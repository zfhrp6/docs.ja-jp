---
title: "ICorDebugArrayValue::GetCount メソッド"
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
- ICorDebugArrayValue.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetCount
helpviewer_keywords:
- ICorDebugArrayValue::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 44cd98cf-2127-4d46-8c6a-da4e857bb6b0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8a4dfdf6ad1fc50cbca039d50b32bc81b6b977ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="9b89c-102">ICorDebugArrayValue::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="9b89c-102">ICorDebugArrayValue::GetCount Method</span></span>
<span data-ttu-id="9b89c-103">配列の要素の合計数を取得します。</span><span class="sxs-lookup"><span data-stu-id="9b89c-103">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b89c-104">構文</span><span class="sxs-lookup"><span data-stu-id="9b89c-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b89c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b89c-105">Parameters</span></span>  
 `pnCount`  
 <span data-ttu-id="9b89c-106">[out]配列内の要素の総数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9b89c-106">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b89c-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="9b89c-107">Requirements</span></span>  
 <span data-ttu-id="9b89c-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9b89c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b89c-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b89c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b89c-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b89c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b89c-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b89c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
