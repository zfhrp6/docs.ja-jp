---
title: "ICorDebugType::GetFirstTypeParameter メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetFirstTypeParameter
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e963553bfeac2d659de8fc460a938d2d523b53e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="dc42e-102">ICorDebugType::GetFirstTypeParameter メソッド</span><span class="sxs-lookup"><span data-stu-id="dc42e-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="dc42e-103">1 つを表す ICorDebugType へのインターフェイス ポインターを取得<xref:System.Type>これによって表される型のパラメーター`ICorDebugType`です。</span><span class="sxs-lookup"><span data-stu-id="dc42e-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc42e-104">構文</span><span class="sxs-lookup"><span data-stu-id="dc42e-104">Syntax</span></span>  
  
```  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc42e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dc42e-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="dc42e-106">[out]アドレスへのポインター、`ICorDebugType`を最初のパラメーターを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dc42e-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc42e-107">コメント</span><span class="sxs-lookup"><span data-stu-id="dc42e-107">Remarks</span></span>  
 <span data-ttu-id="dc42e-108">`GetFirstTypeParameter`呼び出せるケースの場所の種類に関する追加情報では、多くても 1 つの型パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="dc42e-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="dc42e-109">具体的には、使用できます、型が ELEMENT_TYPE_ARRAY、インポートする場合、ELEMENT_TYPE_BYREF、または ELEMENT_TYPE_PTR 場合、によって示される、 [icordebugtype::gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="dc42e-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc42e-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="dc42e-110">Requirements</span></span>  
 <span data-ttu-id="dc42e-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dc42e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc42e-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc42e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc42e-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc42e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc42e-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc42e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
