---
title: IMethodMalloc インターフェイス
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b11cf0fadc9142ee291115cf9f0d84e6429834fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455118"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="058f5-102">IMethodMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="058f5-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="058f5-103">新しい Microsoft intermediate language (MSIL) 関数本体にメモリを割り当てる方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="058f5-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="058f5-104">`IMethodMalloc`インターフェイスは、単純なメモリ アロケーター。</span><span class="sxs-lookup"><span data-stu-id="058f5-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="058f5-105">これにより、メモリを割り当てるには、解放することができます。</span><span class="sxs-lookup"><span data-stu-id="058f5-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="058f5-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="058f5-106">Methods</span></span>  
  
|<span data-ttu-id="058f5-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="058f5-107">Method</span></span>|<span data-ttu-id="058f5-108">説明</span><span class="sxs-lookup"><span data-stu-id="058f5-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="058f5-109">Alloc メソッド</span><span class="sxs-lookup"><span data-stu-id="058f5-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="058f5-110">新しい MSIL 関数本体の指定した量のメモリを割り当てようとします。</span><span class="sxs-lookup"><span data-stu-id="058f5-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="058f5-111">コメント</span><span class="sxs-lookup"><span data-stu-id="058f5-111">Remarks</span></span>  
 <span data-ttu-id="058f5-112">各アロケーターはモジュール固有であり、関数本体がモジュールのベースから正の値のオフセット位置にあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="058f5-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="058f5-113">モジュールのベースを超えるメモリ アロケーターを使用すると、関数本体にのみメモリを割り当てるため、貴重なことはできます。</span><span class="sxs-lookup"><span data-stu-id="058f5-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="058f5-114">要件</span><span class="sxs-lookup"><span data-stu-id="058f5-114">Requirements</span></span>  
 <span data-ttu-id="058f5-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="058f5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="058f5-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="058f5-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="058f5-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="058f5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="058f5-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="058f5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="058f5-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="058f5-119">See Also</span></span>  
 [<span data-ttu-id="058f5-120">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="058f5-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
