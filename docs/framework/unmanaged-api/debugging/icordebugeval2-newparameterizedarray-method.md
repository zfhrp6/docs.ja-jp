---
title: "ICorDebugEval2::NewParameterizedArray メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedArray
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf7f8fb0d3418f863f2cd1531dc32b7e64c2b8a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="41b9f-102">ICorDebugEval2::NewParameterizedArray メソッド</span><span class="sxs-lookup"><span data-stu-id="41b9f-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="41b9f-103">指定した要素の型および次元の新しい配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="41b9f-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41b9f-104">構文</span><span class="sxs-lookup"><span data-stu-id="41b9f-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41b9f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="41b9f-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="41b9f-106">[in]配列に格納されている要素の型を表す ICorDebugType オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="41b9f-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="41b9f-107">[in]配列の次元の数。</span><span class="sxs-lookup"><span data-stu-id="41b9f-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="41b9f-108">.NET Framework version 2.0 では、この値は 1 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="41b9f-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="41b9f-109">[in]配列の各次元のバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="41b9f-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="41b9f-110">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="41b9f-110">[in] Optional.</span></span> <span data-ttu-id="41b9f-111">配列の各次元の下限値です。</span><span class="sxs-lookup"><span data-stu-id="41b9f-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="41b9f-112">この値を省略すると、各次元の下限を 0 が使われます。</span><span class="sxs-lookup"><span data-stu-id="41b9f-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41b9f-113">コメント</span><span class="sxs-lookup"><span data-stu-id="41b9f-113">Remarks</span></span>  
 <span data-ttu-id="41b9f-114">配列の要素のジェネリック型のインスタンスがあります。</span><span class="sxs-lookup"><span data-stu-id="41b9f-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="41b9f-115">配列は常に、現在のスレッドが実行されているアプリケーション ドメインに作成します。</span><span class="sxs-lookup"><span data-stu-id="41b9f-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="41b9f-116">.NET Framework 2.0 の値で`rank`1 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="41b9f-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41b9f-117">要件</span><span class="sxs-lookup"><span data-stu-id="41b9f-117">Requirements</span></span>  
 <span data-ttu-id="41b9f-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="41b9f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41b9f-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41b9f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41b9f-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41b9f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41b9f-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41b9f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
