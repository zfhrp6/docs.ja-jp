---
title: "IMethodMalloc インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc
helpviewer_keywords: IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d246f329f80a76d2c93190fd663c7362418385f7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="7a0ca-102">IMethodMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a0ca-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="7a0ca-103">新しい Microsoft intermediate language (MSIL) 関数本体にメモリを割り当てる方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="7a0ca-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a0ca-104">`IMethodMalloc`インターフェイスは、単純なメモリ アロケーター。</span><span class="sxs-lookup"><span data-stu-id="7a0ca-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="7a0ca-105">これにより、メモリを割り当てるには、解放することができます。</span><span class="sxs-lookup"><span data-stu-id="7a0ca-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a0ca-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="7a0ca-106">Methods</span></span>  
  
|<span data-ttu-id="7a0ca-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="7a0ca-107">Method</span></span>|<span data-ttu-id="7a0ca-108">説明</span><span class="sxs-lookup"><span data-stu-id="7a0ca-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a0ca-109">Alloc メソッド</span><span class="sxs-lookup"><span data-stu-id="7a0ca-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="7a0ca-110">新しい MSIL 関数本体の指定した量のメモリを割り当てようとします。</span><span class="sxs-lookup"><span data-stu-id="7a0ca-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a0ca-111">コメント</span><span class="sxs-lookup"><span data-stu-id="7a0ca-111">Remarks</span></span>  
 <span data-ttu-id="7a0ca-112">各アロケーターはモジュール固有であり、関数本体がモジュールのベースから正の値のオフセット位置にあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7a0ca-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="7a0ca-113">モジュールのベースを超えるメモリ アロケーターを使用すると、関数本体にのみメモリを割り当てるため、貴重なことはできます。</span><span class="sxs-lookup"><span data-stu-id="7a0ca-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a0ca-114">要件</span><span class="sxs-lookup"><span data-stu-id="7a0ca-114">Requirements</span></span>  
 <span data-ttu-id="7a0ca-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7a0ca-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a0ca-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7a0ca-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7a0ca-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a0ca-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a0ca-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a0ca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a0ca-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a0ca-119">See Also</span></span>  
 [<span data-ttu-id="7a0ca-120">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a0ca-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
