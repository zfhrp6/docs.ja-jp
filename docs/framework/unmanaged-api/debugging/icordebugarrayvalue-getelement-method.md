---
title: ICorDebugArrayValue::GetElement メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 500e01955666c7a8e2bd1dcf9d34afe3aeb6b421
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403345"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="39d15-102">ICorDebugArrayValue::GetElement メソッド</span><span class="sxs-lookup"><span data-stu-id="39d15-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="39d15-103">指定された配列の要素の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="39d15-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39d15-104">構文</span><span class="sxs-lookup"><span data-stu-id="39d15-104">Syntax</span></span>  
  
```  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39d15-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="39d15-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="39d15-106">[in]これの次元数`ICorDebugArrayValue`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="39d15-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="39d15-107">この値のサイズでも、`indices`配列のサイズがの次元数と等しいので、`ICorDebugArrayValue`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="39d15-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="39d15-108">[in]ディメンション内の位置を指定する各インデックスの値の配列、`ICorDebugArrayValue`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="39d15-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="39d15-109">この値は null にできません。</span><span class="sxs-lookup"><span data-stu-id="39d15-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="39d15-110">[out]指定した要素の値を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39d15-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39d15-111">要件</span><span class="sxs-lookup"><span data-stu-id="39d15-111">Requirements</span></span>  
 <span data-ttu-id="39d15-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="39d15-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39d15-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39d15-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39d15-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39d15-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39d15-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39d15-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
