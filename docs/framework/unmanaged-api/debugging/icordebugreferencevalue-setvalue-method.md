---
title: ICorDebugReferenceValue::SetValue メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f0c06f9b04c5f15171464b93dc93765625d6f19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418143"
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="b0251-102">ICorDebugReferenceValue::SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="b0251-102">ICorDebugReferenceValue::SetValue Method</span></span>
<span data-ttu-id="b0251-103">指定されたメモリ アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="b0251-103">Sets the specified memory address.</span></span> <span data-ttu-id="b0251-104">つまり、このメソッドは、この ICorDebugReferenceValue オブジェクトを指すようを設定します。</span><span class="sxs-lookup"><span data-stu-id="b0251-104">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0251-105">構文</span><span class="sxs-lookup"><span data-stu-id="b0251-105">Syntax</span></span>  
  
```  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0251-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b0251-106">Parameters</span></span>  
 `value`  
 <span data-ttu-id="b0251-107">[in]A`CORDB_ADDRESS`先であるオブジェクトのアドレスを指定する値`ICorDebugReferenceValue`ポイント。</span><span class="sxs-lookup"><span data-stu-id="b0251-107">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0251-108">要件</span><span class="sxs-lookup"><span data-stu-id="b0251-108">Requirements</span></span>  
 <span data-ttu-id="b0251-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b0251-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0251-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0251-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0251-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0251-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0251-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0251-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
