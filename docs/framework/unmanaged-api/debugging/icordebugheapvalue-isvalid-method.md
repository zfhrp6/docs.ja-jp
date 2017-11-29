---
title: "ICorDebugHeapValue::IsValid メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue.IsValid
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df7105c94a6f88c9c196f1d9d6be6f4a62f7c258
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="42ed1-102">ICorDebugHeapValue::IsValid メソッド</span><span class="sxs-lookup"><span data-stu-id="42ed1-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="42ed1-103">この ICorDebugHeapValue によって表されるオブジェクトが有効かどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="42ed1-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="42ed1-104">.NET Framework version 2.0 では、このメソッドは廃止されました。</span><span class="sxs-lookup"><span data-stu-id="42ed1-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42ed1-105">構文</span><span class="sxs-lookup"><span data-stu-id="42ed1-105">Syntax</span></span>  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42ed1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="42ed1-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="42ed1-107">[out]ヒープでは、この値が有効かどうかを示すブール値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="42ed1-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42ed1-108">コメント</span><span class="sxs-lookup"><span data-stu-id="42ed1-108">Remarks</span></span>  
 <span data-ttu-id="42ed1-109">値は、ガベージ コレクターが解放された場合に有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="42ed1-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="42ed1-110">このメソッドの使用は推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="42ed1-110">This method has been deprecated.</span></span> <span data-ttu-id="42ed1-111">.NET Framework 2.0 ではすべての値は有効期限[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)に時間値は、検証が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="42ed1-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42ed1-112">要件</span><span class="sxs-lookup"><span data-stu-id="42ed1-112">Requirements</span></span>  
 <span data-ttu-id="42ed1-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="42ed1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42ed1-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42ed1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42ed1-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42ed1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42ed1-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42ed1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
