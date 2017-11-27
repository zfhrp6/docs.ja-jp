---
title: "ICorDebugArrayValue::GetElementAtPosition メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.GetElementAtPosition
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::GetElementAtPosition
helpviewer_keywords:
- GetElementAtPosition method [.NET Framework debugging]
- ICorDebugArrayValue::GetElementAtPosition method [.NET Framework debugging]
ms.assetid: 6fd5eaa4-1997-4910-82f5-3887480db764
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 20af0afa395dd69dc8967aa9f39a8bf99eacf530
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="8de88-102">ICorDebugArrayValue::GetElementAtPosition メソッド</span><span class="sxs-lookup"><span data-stu-id="8de88-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="8de88-103">0 から始まる 1 次元の配列として、配列を扱う方法の指定された位置に要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="8de88-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8de88-104">構文</span><span class="sxs-lookup"><span data-stu-id="8de88-104">Syntax</span></span>  
  
```  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8de88-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8de88-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="8de88-106">[in]取得する要素の位置。</span><span class="sxs-lookup"><span data-stu-id="8de88-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="8de88-107">[out]要素の値を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8de88-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8de88-108">コメント</span><span class="sxs-lookup"><span data-stu-id="8de88-108">Remarks</span></span>  
 <span data-ttu-id="8de88-109">多次元配列のレイアウトには、配列のレイアウトの C++ のスタイルが次に示します。</span><span class="sxs-lookup"><span data-stu-id="8de88-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8de88-110">要件</span><span class="sxs-lookup"><span data-stu-id="8de88-110">Requirements</span></span>  
 <span data-ttu-id="8de88-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8de88-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8de88-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8de88-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8de88-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8de88-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8de88-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8de88-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
