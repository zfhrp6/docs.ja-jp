---
title: "ICorDebugValue::GetSize メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetSize
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5cf99b35d45c1dda8f187e0206e068c128f347d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="b1c43-102">ICorDebugValue::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="b1c43-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="b1c43-103">この"ICorDebugValue"オブジェクトのバイト単位のサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="b1c43-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1c43-104">構文</span><span class="sxs-lookup"><span data-stu-id="b1c43-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1c43-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b1c43-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="b1c43-106">[out]この値のオブジェクトのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="b1c43-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1c43-107">コメント</span><span class="sxs-lookup"><span data-stu-id="b1c43-107">Remarks</span></span>  
 <span data-ttu-id="b1c43-108">値の型が参照型の場合は、このメソッドは、オブジェクトのサイズではなく、ポインターのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="b1c43-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="b1c43-109">`ICorDebugValue::GetSize`メソッドを返します。`COR_E_OVERFLOW`は 64 ビット プラットフォームで 4 GB より大きいオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b1c43-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="b1c43-110">使用して、 [icordebugvalue 3::getsize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)メソッド代わりにオブジェクトにある 4 GB より大きい。</span><span class="sxs-lookup"><span data-stu-id="b1c43-110">Use the [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1c43-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="b1c43-111">Requirements</span></span>  
 <span data-ttu-id="b1c43-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b1c43-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1c43-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1c43-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1c43-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1c43-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1c43-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1c43-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c43-116">参照</span><span class="sxs-lookup"><span data-stu-id="b1c43-116">See Also</span></span>  
    
 [<span data-ttu-id="b1c43-117">GetSize64 メソッド</span><span class="sxs-lookup"><span data-stu-id="b1c43-117">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
