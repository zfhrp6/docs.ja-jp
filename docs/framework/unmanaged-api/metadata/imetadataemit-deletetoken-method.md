---
title: "IMetaDataEmit::DeleteToken メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.DeleteToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteToken
helpviewer_keywords:
- DeleteToken method [.NET Framework metadata]
- IMetaDataEmit::DeleteToken method [.NET Framework metadata]
ms.assetid: a4926d0a-261b-46b1-9994-82633661a64b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5fe79e13a44ef9d916a0009c46200605950e8895
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="c2ef4-102">IMetaDataEmit::DeleteToken メソッド</span><span class="sxs-lookup"><span data-stu-id="c2ef4-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="c2ef4-103">現在のメタデータ スコープから、指定されたトークンを削除します。</span><span class="sxs-lookup"><span data-stu-id="c2ef4-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2ef4-104">構文</span><span class="sxs-lookup"><span data-stu-id="c2ef4-104">Syntax</span></span>  
  
```  
HRESULT DeleteToken (   
    [in]  mdToken     tkObj   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2ef4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c2ef4-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="c2ef4-106">[in]削除するトークンです。</span><span class="sxs-lookup"><span data-stu-id="c2ef4-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2ef4-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="c2ef4-107">Requirements</span></span>  
 <span data-ttu-id="c2ef4-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c2ef4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2ef4-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c2ef4-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c2ef4-110">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="c2ef4-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2ef4-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2ef4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2ef4-112">参照</span><span class="sxs-lookup"><span data-stu-id="c2ef4-112">See Also</span></span>  
 [<span data-ttu-id="c2ef4-113">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c2ef4-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="c2ef4-114">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c2ef4-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
