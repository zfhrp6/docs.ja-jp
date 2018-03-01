---
title: "ICorDebugHeapValue::IsValid メソッド"
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
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f4f356c953feaf0e6597983f431222a469e90c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="93ec8-102">ICorDebugHeapValue::IsValid メソッド</span><span class="sxs-lookup"><span data-stu-id="93ec8-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="93ec8-103">この ICorDebugHeapValue によって表されるオブジェクトが有効かどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="93ec8-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="93ec8-104">.NET Framework version 2.0 では、このメソッドは廃止されました。</span><span class="sxs-lookup"><span data-stu-id="93ec8-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93ec8-105">構文</span><span class="sxs-lookup"><span data-stu-id="93ec8-105">Syntax</span></span>  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93ec8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="93ec8-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="93ec8-107">[out]ヒープでは、この値が有効かどうかを示すブール値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="93ec8-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93ec8-108">コメント</span><span class="sxs-lookup"><span data-stu-id="93ec8-108">Remarks</span></span>  
 <span data-ttu-id="93ec8-109">値は、ガベージ コレクターが解放された場合に有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="93ec8-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="93ec8-110">このメソッドの使用は推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="93ec8-110">This method has been deprecated.</span></span> <span data-ttu-id="93ec8-111">.NET Framework 2.0 ではすべての値は有効期限[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)に時間値は、検証が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="93ec8-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93ec8-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="93ec8-112">Requirements</span></span>  
 <span data-ttu-id="93ec8-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="93ec8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93ec8-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93ec8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93ec8-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93ec8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93ec8-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93ec8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
