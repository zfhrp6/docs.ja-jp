---
title: ICorDebugObjectValue::GetClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dff7a42cac7002e170e8da3c3505fe37bd5eb85f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418764"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="e71d3-102">ICorDebugObjectValue::GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="e71d3-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="e71d3-103">このオブジェクトの値のクラスを取得します。</span><span class="sxs-lookup"><span data-stu-id="e71d3-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e71d3-104">構文</span><span class="sxs-lookup"><span data-stu-id="e71d3-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e71d3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e71d3-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="e71d3-106">[out]この"ICorDebugObjectValue"オブジェクトによって表されるオブジェクトの値のクラスを表す"ICorDebugClass"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e71d3-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e71d3-107">コメント</span><span class="sxs-lookup"><span data-stu-id="e71d3-107">Remarks</span></span>  
 <span data-ttu-id="e71d3-108">`GetClass`と[icordebugvalue::gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)の各メソッドは、値の型に関する情報を返します。 両方の汎用対応によって置き換えられる[icordebugvalue 2::getexacttype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="e71d3-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e71d3-109">要件</span><span class="sxs-lookup"><span data-stu-id="e71d3-109">Requirements</span></span>  
 <span data-ttu-id="e71d3-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e71d3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e71d3-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e71d3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e71d3-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e71d3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e71d3-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e71d3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e71d3-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="e71d3-114">See Also</span></span>  
    
 
