---
title: "ICorDebugReferenceValue::GetValue メソッド"
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
- ICorDebugReferenceValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::GetValue method [.NET Framework debugging]
ms.assetid: 5da07f99-6c70-46ec-b997-5ab6fb7106cd
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d7be70ec41b2044b4af10e102218ce487e4a5e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugreferencevaluegetvalue-method"></a><span data-ttu-id="2ffe8-102">ICorDebugReferenceValue::GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="2ffe8-102">ICorDebugReferenceValue::GetValue Method</span></span>
<span data-ttu-id="2ffe8-103">参照先オブジェクトの現在のメモリ アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="2ffe8-103">Gets the current memory address of the referenced object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ffe8-104">構文</span><span class="sxs-lookup"><span data-stu-id="2ffe8-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ffe8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2ffe8-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="2ffe8-106">[out]ポインター、`CORDB_ADDRESS`この ICorDebugReferenceValue オブジェクトが指し示すオブジェクトのアドレスを指定する値。</span><span class="sxs-lookup"><span data-stu-id="2ffe8-106">[out] A pointer to a `CORDB_ADDRESS` value that specifies the address of the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ffe8-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="2ffe8-107">Requirements</span></span>  
 <span data-ttu-id="2ffe8-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2ffe8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ffe8-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ffe8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ffe8-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ffe8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ffe8-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ffe8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
