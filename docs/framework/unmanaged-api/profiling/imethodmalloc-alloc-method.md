---
title: "IMethodMalloc::Alloc メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc.Alloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ae0fa84c08cb8e366db36b6727a3058f24789801
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="dc963-102">IMethodMalloc::Alloc メソッド</span><span class="sxs-lookup"><span data-stu-id="dc963-102">IMethodMalloc::Alloc Method</span></span>
<span data-ttu-id="dc963-103">新しい Microsoft intermediate language (MSIL) 関数本体の指定した量のメモリを割り当てようとします。</span><span class="sxs-lookup"><span data-stu-id="dc963-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc963-104">構文</span><span class="sxs-lookup"><span data-stu-id="dc963-104">Syntax</span></span>  
  
```  
PVOID Alloc (  
    [in] ULONG   cb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc963-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dc963-105">Parameters</span></span>  
 `cb`  
 <span data-ttu-id="dc963-106">[in]メソッドの本体を割り当てることのバイト数。</span><span class="sxs-lookup"><span data-stu-id="dc963-106">[in] The number of bytes to allocate for the method body.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc963-107">コメント</span><span class="sxs-lookup"><span data-stu-id="dc963-107">Remarks</span></span>  
 <span data-ttu-id="dc963-108">割り当てられたメモリは、このアロケーターに関連付けられているモジュールのベース アドレスより大きいアドレスから開始されます。</span><span class="sxs-lookup"><span data-stu-id="dc963-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="dc963-109">つまり、各アロケーターは、特定のモジュールが作成されはそのベース アドレスから正のオフセットにメモリを割り当てようとします。</span><span class="sxs-lookup"><span data-stu-id="dc963-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="dc963-110">場合`Alloc`要求されたモジュールのベース アドレスより大きいアドレスにあるバイト数の割り当てが失敗した実際のメモリ領域の使用可能な量に関係なく、E_OUTOFMEMORY を返します。</span><span class="sxs-lookup"><span data-stu-id="dc963-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>  
  
 <span data-ttu-id="dc963-111">`Alloc`メソッドを組み合わせて使用する必要があります、 [icorprofilerinfo::setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="dc963-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc963-112">要件</span><span class="sxs-lookup"><span data-stu-id="dc963-112">Requirements</span></span>  
 <span data-ttu-id="dc963-113">**プラットフォーム:** WindSee[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dc963-113">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc963-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dc963-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dc963-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc963-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc963-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc963-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc963-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc963-117">See Also</span></span>  
 [<span data-ttu-id="dc963-118">IMethodMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc963-118">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
