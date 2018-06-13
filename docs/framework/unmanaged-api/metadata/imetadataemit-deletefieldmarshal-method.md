---
title: IMetaDataEmit::DeleteFieldMarshal メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc88baea130adbec3dd8e4065ac0eb14ece7b8ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444852"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="d728f-102">IMetaDataEmit::DeleteFieldMarshal メソッド</span><span class="sxs-lookup"><span data-stu-id="d728f-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="d728f-103">指定したトークンによって参照されるオブジェクトのメタデータ シグネチャのマーシャ リング PInvoke を破棄します。</span><span class="sxs-lookup"><span data-stu-id="d728f-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d728f-104">構文</span><span class="sxs-lookup"><span data-stu-id="d728f-104">Syntax</span></span>  
  
```  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d728f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d728f-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d728f-106">[in]`mdFieldDef`または`mdParamDef`フィールドまたはマーシャ リングのメタデータ署名を削除する対象のパラメーターを表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="d728f-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d728f-107">要件</span><span class="sxs-lookup"><span data-stu-id="d728f-107">Requirements</span></span>  
 <span data-ttu-id="d728f-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d728f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d728f-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d728f-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d728f-110">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="d728f-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d728f-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d728f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d728f-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d728f-112">See Also</span></span>  
 [<span data-ttu-id="d728f-113">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d728f-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d728f-114">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d728f-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
