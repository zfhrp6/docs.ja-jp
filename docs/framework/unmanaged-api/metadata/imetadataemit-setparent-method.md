---
title: IMetaDataEmit::SetParent メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdaa6aab28eb82450db7b9f946e033bfad55faf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446070"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="83f7d-102">IMetaDataEmit::SetParent メソッド</span><span class="sxs-lookup"><span data-stu-id="83f7d-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="83f7d-103">確立する前回の呼び出しで定義されている、指定されたメンバー [imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)、前回の呼び出しで定義されている、指定した型のメンバーである[imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="83f7d-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f7d-104">構文</span><span class="sxs-lookup"><span data-stu-id="83f7d-104">Syntax</span></span>  
  
```  
HRESULT SetParent (   
    [in]  mdMemberRef mr,   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83f7d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83f7d-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="83f7d-106">[in]`mdMemberRef`新しい親を受信するためのトークン。</span><span class="sxs-lookup"><span data-stu-id="83f7d-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="83f7d-107">[in]`mdToken`新しい親。</span><span class="sxs-lookup"><span data-stu-id="83f7d-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83f7d-108">要件</span><span class="sxs-lookup"><span data-stu-id="83f7d-108">Requirements</span></span>  
 <span data-ttu-id="83f7d-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="83f7d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83f7d-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="83f7d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83f7d-111">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="83f7d-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83f7d-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83f7d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f7d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="83f7d-113">See Also</span></span>  
 [<span data-ttu-id="83f7d-114">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83f7d-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="83f7d-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83f7d-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
