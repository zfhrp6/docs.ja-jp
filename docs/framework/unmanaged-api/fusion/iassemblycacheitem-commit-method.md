---
title: IAssemblyCacheItem::Commit メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.Commit
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::Commit
helpviewer_keywords:
- IAssemblyCacheItem::Commit method [.NET Framework fusion]
- Commit method, IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: c2321f17-f46f-4815-ae41-b28678753613
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f5cbb7c0b4e3ce6d66d30e812008fc3419d7d7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429093"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="8a8a3-102">IAssemblyCacheItem::Commit メソッド</span><span class="sxs-lookup"><span data-stu-id="8a8a3-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="8a8a3-103">メモリにキャッシュされたアセンブリ参照をコミットします。</span><span class="sxs-lookup"><span data-stu-id="8a8a3-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a8a3-104">構文</span><span class="sxs-lookup"><span data-stu-id="8a8a3-104">Syntax</span></span>  
  
```  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a8a3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a8a3-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="8a8a3-106">[in]ものがありますで定義されているフラグです。</span><span class="sxs-lookup"><span data-stu-id="8a8a3-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="8a8a3-107">[out, 省略可能]操作の結果を示す値です。</span><span class="sxs-lookup"><span data-stu-id="8a8a3-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a8a3-108">要件</span><span class="sxs-lookup"><span data-stu-id="8a8a3-108">Requirements</span></span>  
 <span data-ttu-id="8a8a3-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8a8a3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a8a3-110">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="8a8a3-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8a8a3-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a8a3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a8a3-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a8a3-112">See Also</span></span>  
 [<span data-ttu-id="8a8a3-113">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a8a3-113">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
