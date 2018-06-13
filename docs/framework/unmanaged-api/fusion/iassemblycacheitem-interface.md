---
title: IAssemblyCacheItem インターフェイス
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c6da86ce2d86a6842d2d7d8de860e9a8621bdaf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429596"
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="13cc3-102">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13cc3-102">IAssemblyCacheItem Interface</span></span>
<span data-ttu-id="13cc3-103">グローバル アセンブリ キャッシュ内の 1 つのアセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="13cc3-103">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="13cc3-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="13cc3-104">Methods</span></span>  
  
|<span data-ttu-id="13cc3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="13cc3-105">Method</span></span>|<span data-ttu-id="13cc3-106">説明</span><span class="sxs-lookup"><span data-stu-id="13cc3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="13cc3-107">AbortItem メソッド</span><span class="sxs-lookup"><span data-stu-id="13cc3-107">AbortItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="13cc3-108">リリースされる前に、クリーンアップ操作を実行する、グローバル アセンブリ キャッシュにアセンブリを使用します。</span><span class="sxs-lookup"><span data-stu-id="13cc3-108">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="13cc3-109">Commit メソッド</span><span class="sxs-lookup"><span data-stu-id="13cc3-109">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-commit-method.md)|<span data-ttu-id="13cc3-110">メモリにキャッシュされたアセンブリ参照をコミットします。</span><span class="sxs-lookup"><span data-stu-id="13cc3-110">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="13cc3-111">CreateStream メソッド</span><span class="sxs-lookup"><span data-stu-id="13cc3-111">CreateStream Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-createstream-method.md)|<span data-ttu-id="13cc3-112">指定した名前と形式を使用するストリームを作成します。</span><span class="sxs-lookup"><span data-stu-id="13cc3-112">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13cc3-113">要件</span><span class="sxs-lookup"><span data-stu-id="13cc3-113">Requirements</span></span>  
 <span data-ttu-id="13cc3-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="13cc3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13cc3-115">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="13cc3-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="13cc3-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13cc3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13cc3-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="13cc3-117">See Also</span></span>  
 [<span data-ttu-id="13cc3-118">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13cc3-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="13cc3-119">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="13cc3-119">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="13cc3-120">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13cc3-120">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
