---
title: ICorDebugArrayValue::GetCount メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetCount
helpviewer_keywords:
- ICorDebugArrayValue::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 44cd98cf-2127-4d46-8c6a-da4e857bb6b0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa72f82d2fc78110fc2bee8edd265916996aa884
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403147"
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="f16bb-102">ICorDebugArrayValue::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="f16bb-102">ICorDebugArrayValue::GetCount Method</span></span>
<span data-ttu-id="f16bb-103">配列の要素の合計数を取得します。</span><span class="sxs-lookup"><span data-stu-id="f16bb-103">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f16bb-104">構文</span><span class="sxs-lookup"><span data-stu-id="f16bb-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f16bb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f16bb-105">Parameters</span></span>  
 `pnCount`  
 <span data-ttu-id="f16bb-106">[out]配列内の要素の総数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f16bb-106">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f16bb-107">要件</span><span class="sxs-lookup"><span data-stu-id="f16bb-107">Requirements</span></span>  
 <span data-ttu-id="f16bb-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f16bb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f16bb-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f16bb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f16bb-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f16bb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f16bb-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f16bb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
