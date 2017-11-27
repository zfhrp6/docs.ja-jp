---
title: "ICorDebugValue::GetType メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d214da529aed40d33bdf18530560e9cd7b00f60a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="934f1-102">ICorDebugValue::GetType メソッド</span><span class="sxs-lookup"><span data-stu-id="934f1-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="934f1-103">この"ICorDebugValue"オブジェクトのプリミティブ型を取得します。</span><span class="sxs-lookup"><span data-stu-id="934f1-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="934f1-104">構文</span><span class="sxs-lookup"><span data-stu-id="934f1-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="934f1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="934f1-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="934f1-106">[out]値の型を示す"CorElementType"列挙の値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="934f1-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="934f1-107">コメント</span><span class="sxs-lookup"><span data-stu-id="934f1-107">Remarks</span></span>  
 <span data-ttu-id="934f1-108">適切なサブクラスを使用、その型を調べられる場合があります、オブジェクトが実行時の複雑な型である場合、`ICorDebugValue`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="934f1-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="934f1-109">たとえば、"ICorDebugObjectValue"から継承される`ICorDebugValue`、複合型を表します。</span><span class="sxs-lookup"><span data-stu-id="934f1-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="934f1-110">`GetType`と[icordebugobjectvalue::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)の各メソッドは、値の型に関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="934f1-110">The `GetType` and [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="934f1-111">両方の汎用対応によって置き換えられる[icordebugvalue 2::getexacttype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="934f1-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="934f1-112">要件</span><span class="sxs-lookup"><span data-stu-id="934f1-112">Requirements</span></span>  
 <span data-ttu-id="934f1-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="934f1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="934f1-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="934f1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="934f1-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="934f1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="934f1-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="934f1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934f1-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="934f1-117">See Also</span></span>  
 
