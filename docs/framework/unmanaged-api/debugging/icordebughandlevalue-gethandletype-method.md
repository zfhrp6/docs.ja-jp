---
title: ICorDebugHandleValue::GetHandleType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.GetHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::GetHandleType
helpviewer_keywords:
- GetHandleType method [.NET Framework debugging]
- ICorDebugHandleValue::GetHandleType method [.NET Framework debugging]
ms.assetid: d5e7b12d-835a-4e86-ae2f-d658d4f1c67c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51fd8e9728955e8f426a38b8bf6cdc78dfa9bbde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412348"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="d5f0b-102">ICorDebugHandleValue::GetHandleType メソッド</span><span class="sxs-lookup"><span data-stu-id="d5f0b-102">ICorDebugHandleValue::GetHandleType Method</span></span>
<span data-ttu-id="d5f0b-103">ICorDebugHandleValue オブジェクトによって参照されているハンドルの種類を示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="d5f0b-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5f0b-104">構文</span><span class="sxs-lookup"><span data-stu-id="d5f0b-104">Syntax</span></span>  
  
```  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5f0b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d5f0b-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="d5f0b-106">[out]このハンドルの種類を示す CorDebugHandleType 列挙型の値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d5f0b-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5f0b-107">要件</span><span class="sxs-lookup"><span data-stu-id="d5f0b-107">Requirements</span></span>  
 <span data-ttu-id="d5f0b-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d5f0b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5f0b-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5f0b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5f0b-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5f0b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5f0b-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5f0b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
