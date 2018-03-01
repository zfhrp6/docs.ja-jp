---
title: "ICorDebugReferenceValue::SetValue メソッド"
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
- ICorDebugReferenceValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::SetValue
helpviewer_keywords:
- SetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::SetValue method [.NET Framework debugging]
ms.assetid: 3d3f6eec-d772-401f-a028-1a2ecdc31e95
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 71250155d0c71b9b8f9cddad57d0c74b4ffc7991
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="629d5-102">ICorDebugReferenceValue::SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="629d5-102">ICorDebugReferenceValue::SetValue Method</span></span>
<span data-ttu-id="629d5-103">指定されたメモリ アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="629d5-103">Sets the specified memory address.</span></span> <span data-ttu-id="629d5-104">つまり、このメソッドは、この ICorDebugReferenceValue オブジェクトを指すようを設定します。</span><span class="sxs-lookup"><span data-stu-id="629d5-104">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="629d5-105">構文</span><span class="sxs-lookup"><span data-stu-id="629d5-105">Syntax</span></span>  
  
```  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="629d5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="629d5-106">Parameters</span></span>  
 `value`  
 <span data-ttu-id="629d5-107">[in]A`CORDB_ADDRESS`先であるオブジェクトのアドレスを指定する値`ICorDebugReferenceValue`ポイント。</span><span class="sxs-lookup"><span data-stu-id="629d5-107">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="629d5-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="629d5-108">Requirements</span></span>  
 <span data-ttu-id="629d5-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="629d5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="629d5-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="629d5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="629d5-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="629d5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="629d5-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="629d5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
