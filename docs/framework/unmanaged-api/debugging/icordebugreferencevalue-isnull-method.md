---
title: ICorDebugReferenceValue::IsNull メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c82c72350931bf3aed8ec6699cd0af834798e92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417216"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="5d41e-102">ICorDebugReferenceValue::IsNull メソッド</span><span class="sxs-lookup"><span data-stu-id="5d41e-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="5d41e-103">この ICorDebugReferenceValue いる場合、null 値は、かどうかを示す値を取得、`ICorDebugReferenceValue`がオブジェクトを指していません。</span><span class="sxs-lookup"><span data-stu-id="5d41e-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d41e-104">構文</span><span class="sxs-lookup"><span data-stu-id="5d41e-104">Syntax</span></span>  
  
```  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d41e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5d41e-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="5d41e-106">[out]ブール値へのポインター`true`場合は、この`ICorDebugReferenceValue`オブジェクトは null。 それ以外の場合、`pbNull`は`false`します。</span><span class="sxs-lookup"><span data-stu-id="5d41e-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d41e-107">要件</span><span class="sxs-lookup"><span data-stu-id="5d41e-107">Requirements</span></span>  
 <span data-ttu-id="5d41e-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d41e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d41e-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d41e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d41e-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d41e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d41e-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d41e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
