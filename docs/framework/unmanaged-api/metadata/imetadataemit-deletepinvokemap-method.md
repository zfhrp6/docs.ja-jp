---
title: "IMetaDataEmit::DeletePinvokeMap メソッド"
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
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1479c3fb19feec0e42ee4aec8544a35ce51350a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="b5ab6-102">IMetaDataEmit::DeletePinvokeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="b5ab6-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="b5ab6-103">指定したトークンによって参照されるオブジェクトの PInvoke マッピング メタデータを破棄します。</span><span class="sxs-lookup"><span data-stu-id="b5ab6-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5ab6-104">構文</span><span class="sxs-lookup"><span data-stu-id="b5ab6-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5ab6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b5ab6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b5ab6-106">[in]`mdFieldDef`または`mdMethodDef`PInvoke マッピング メタデータを削除する対象のオブジェクトを表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="b5ab6-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5ab6-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="b5ab6-107">Requirements</span></span>  
 <span data-ttu-id="b5ab6-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b5ab6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5ab6-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b5ab6-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b5ab6-110">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="b5ab6-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5ab6-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5ab6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ab6-112">参照</span><span class="sxs-lookup"><span data-stu-id="b5ab6-112">See Also</span></span>  
 [<span data-ttu-id="b5ab6-113">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b5ab6-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="b5ab6-114">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b5ab6-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
