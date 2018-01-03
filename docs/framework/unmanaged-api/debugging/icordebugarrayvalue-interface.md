---
title: ICorDebugArrayValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue interface
helpviewer_keywords: ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35169f0dd2ca71400d3aebddf9d5e2ae6b72be07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvalue-interface1"></a><span data-ttu-id="d62f6-102">ICorDebugArrayValue Interface1</span><span class="sxs-lookup"><span data-stu-id="d62f6-102">ICorDebugArrayValue Interface1</span></span>
<span data-ttu-id="d62f6-103">1 次元または多次元配列を表す ICorDebugHeapValue のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="d62f6-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d62f6-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="d62f6-104">Methods</span></span>  
  
|<span data-ttu-id="d62f6-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d62f6-105">Method</span></span>|<span data-ttu-id="d62f6-106">説明</span><span class="sxs-lookup"><span data-stu-id="d62f6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d62f6-107">GetBaseIndicies メソッド</span><span class="sxs-lookup"><span data-stu-id="d62f6-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="d62f6-108">配列内の各次元の基本のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="d62f6-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="d62f6-109">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="d62f6-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="d62f6-110">配列の要素の合計数を取得します。</span><span class="sxs-lookup"><span data-stu-id="d62f6-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="d62f6-111">GetDimensions メソッド</span><span class="sxs-lookup"><span data-stu-id="d62f6-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="d62f6-112">配列の次元を取得します。</span><span class="sxs-lookup"><span data-stu-id="d62f6-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="d62f6-113">GetElement メソッド</span><span class="sxs-lookup"><span data-stu-id="d62f6-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="d62f6-114">配列内の特定の要素を表す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="d62f6-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="d62f6-115">GetElementAtPosition メソッド</span><span class="sxs-lookup"><span data-stu-id="d62f6-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="d62f6-116">0 から始まる 1 次元の配列として、配列を扱う方法の指定された位置に要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="d62f6-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="d62f6-117">GetElementType メソッド</span><span class="sxs-lookup"><span data-stu-id="d62f6-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="d62f6-118">配列内の要素の単純型を取得します。</span><span class="sxs-lookup"><span data-stu-id="d62f6-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="d62f6-119">GetRank メソッド</span><span class="sxs-lookup"><span data-stu-id="d62f6-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="d62f6-120">配列のディメンションの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="d62f6-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="d62f6-121">HasBaseIndicies メソッド</span><span class="sxs-lookup"><span data-stu-id="d62f6-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="d62f6-122">配列の基本のインデックスがあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="d62f6-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d62f6-123">コメント</span><span class="sxs-lookup"><span data-stu-id="d62f6-123">Remarks</span></span>  
 <span data-ttu-id="d62f6-124">`ICorDebugArrayValue`1 次元と多次元の両方の配列をサポートします。</span><span class="sxs-lookup"><span data-stu-id="d62f6-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d62f6-125">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d62f6-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d62f6-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="d62f6-126">Requirements</span></span>  
 <span data-ttu-id="d62f6-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d62f6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d62f6-128">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d62f6-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d62f6-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d62f6-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d62f6-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d62f6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d62f6-131">参照</span><span class="sxs-lookup"><span data-stu-id="d62f6-131">See Also</span></span>  
 [<span data-ttu-id="d62f6-132">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d62f6-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
