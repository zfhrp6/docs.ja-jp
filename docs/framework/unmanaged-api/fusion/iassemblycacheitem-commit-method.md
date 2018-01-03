---
title: "IAssemblyCacheItem::Commit メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCacheItem.Commit
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCacheItem::Commit
helpviewer_keywords:
- IAssemblyCacheItem::Commit method [.NET Framework fusion]
- Commit method, IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: c2321f17-f46f-4815-ae41-b28678753613
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3e1907fa3be4992573f84b4810f7504f3af78397
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="d9d20-102">IAssemblyCacheItem::Commit メソッド</span><span class="sxs-lookup"><span data-stu-id="d9d20-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="d9d20-103">メモリにキャッシュされたアセンブリ参照をコミットします。</span><span class="sxs-lookup"><span data-stu-id="d9d20-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9d20-104">構文</span><span class="sxs-lookup"><span data-stu-id="d9d20-104">Syntax</span></span>  
  
```  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9d20-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d9d20-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="d9d20-106">[in]ものがありますで定義されているフラグです。</span><span class="sxs-lookup"><span data-stu-id="d9d20-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="d9d20-107">[out, 省略可能]操作の結果を示す値です。</span><span class="sxs-lookup"><span data-stu-id="d9d20-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9d20-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="d9d20-108">Requirements</span></span>  
 <span data-ttu-id="d9d20-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d9d20-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9d20-110">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d9d20-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d9d20-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9d20-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9d20-112">参照</span><span class="sxs-lookup"><span data-stu-id="d9d20-112">See Also</span></span>  
 [<span data-ttu-id="d9d20-113">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d9d20-113">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
