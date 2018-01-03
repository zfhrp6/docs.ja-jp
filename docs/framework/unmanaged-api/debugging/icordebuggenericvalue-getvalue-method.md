---
title: "ICorDebugGenericValue::GetValue メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGenericValue.GetValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ebb681d32c3ba805fd2e413ceeb007cb2cee57f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="a5c79-102">ICorDebugGenericValue::GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="a5c79-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="a5c79-103">指定されたバッファーには、このジェネリックの値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="a5c79-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c79-104">構文</span><span class="sxs-lookup"><span data-stu-id="a5c79-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5c79-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a5c79-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="a5c79-106">[out]ICorDebugGenericValue オブジェクトによって表される値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a5c79-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="a5c79-107">値には、単純型または参照型 (つまり、ポインター) があります。</span><span class="sxs-lookup"><span data-stu-id="a5c79-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5c79-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="a5c79-108">Requirements</span></span>  
 <span data-ttu-id="a5c79-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a5c79-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5c79-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5c79-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5c79-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5c79-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5c79-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5c79-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
