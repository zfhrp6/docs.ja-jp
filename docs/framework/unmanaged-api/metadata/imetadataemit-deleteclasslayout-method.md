---
title: "IMetaDataEmit::DeleteClassLayout メソッド"
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
- IMetaDataEmit.DeleteClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteClassLayout
helpviewer_keywords:
- DeleteClassLayout method [.NET Framework metadata]
- IMetaDataEmit::DeleteClassLayout method [.NET Framework metadata]
ms.assetid: 65a4ad49-fa49-4b36-8ed1-76dd6a185ab4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a215ba1f468823a93c1515c4a3875764a6ba5bb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="4881e-102">IMetaDataEmit::DeleteClassLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="4881e-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="4881e-103">指定したトークンによって表される型のクラス レイアウト メタデータ シグネチャを破棄します。</span><span class="sxs-lookup"><span data-stu-id="4881e-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4881e-104">構文</span><span class="sxs-lookup"><span data-stu-id="4881e-104">Syntax</span></span>  
  
```  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4881e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4881e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="4881e-106">[in]`mdTypeDef`クラス レイアウトの削除対象の型を表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="4881e-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4881e-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="4881e-107">Requirements</span></span>  
 <span data-ttu-id="4881e-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4881e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4881e-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4881e-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4881e-110">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="4881e-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4881e-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4881e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4881e-112">参照</span><span class="sxs-lookup"><span data-stu-id="4881e-112">See Also</span></span>  
 [<span data-ttu-id="4881e-113">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4881e-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4881e-114">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4881e-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
