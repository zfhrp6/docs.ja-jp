---
title: ICorDebugArrayValue::GetBaseIndicies メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3fe9edf7a635e54aac881a242aca3bc32e21fe1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408126"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="f7e15-102">ICorDebugArrayValue::GetBaseIndicies メソッド</span><span class="sxs-lookup"><span data-stu-id="f7e15-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="f7e15-103">配列内の各次元の基本のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="f7e15-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7e15-104">構文</span><span class="sxs-lookup"><span data-stu-id="f7e15-104">Syntax</span></span>  
  
```  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32           indicies[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7e15-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f7e15-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="f7e15-106">[in]これの次元数`ICorDebugArrayValue`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f7e15-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="f7e15-107">この値のサイズでも、`indicies`配列のサイズがの次元数と等しいので、`ICorDebugArrayValue`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f7e15-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="f7e15-108">[out]このディメンションの基本のインデックス (つまり、開始インデックス) は、それぞれが、整数の配列`ICorDebugArrayValue`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f7e15-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7e15-109">要件</span><span class="sxs-lookup"><span data-stu-id="f7e15-109">Requirements</span></span>  
 <span data-ttu-id="f7e15-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7e15-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7e15-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7e15-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7e15-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7e15-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7e15-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7e15-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
