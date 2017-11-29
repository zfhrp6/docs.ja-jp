---
title: "ICorDebugValue2::GetExactType メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue2.GetExactType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e061e0cd1d467a556c7dd1bd6298784d015aa94
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="ab262-102">ICorDebugValue2::GetExactType メソッド</span><span class="sxs-lookup"><span data-stu-id="ab262-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="ab262-103">表す"ICorDebugType"オブジェクトへのインターフェイス ポインターを取得、<xref:System.Type>この値のです。</span><span class="sxs-lookup"><span data-stu-id="ab262-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab262-104">構文</span><span class="sxs-lookup"><span data-stu-id="ab262-104">Syntax</span></span>  
  
```  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab262-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ab262-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="ab262-106">[out]アドレスへのポインター、`ICorDebugType`を表すオブジェクト、 <xref:System.Type> "ICorDebugValue2"オブジェクトによって表される値。</span><span class="sxs-lookup"><span data-stu-id="ab262-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab262-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ab262-107">Remarks</span></span>  
 <span data-ttu-id="ab262-108">汎用対応`GetExactType`メソッドはどちらも、 [icordebugobjectvalue::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)と[icordebugvalue::gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)メソッド、戻り値の型に関する情報の各.</span><span class="sxs-lookup"><span data-stu-id="ab262-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab262-109">要件</span><span class="sxs-lookup"><span data-stu-id="ab262-109">Requirements</span></span>  
 <span data-ttu-id="ab262-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ab262-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab262-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab262-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab262-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab262-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab262-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab262-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab262-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab262-114">See Also</span></span>  
 
