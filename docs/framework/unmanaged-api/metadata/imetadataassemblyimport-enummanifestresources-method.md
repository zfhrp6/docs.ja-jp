---
title: "IMetaDataAssemblyImport::EnumManifestResources メソッド"
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
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fa31441d060744bb17fc26a61daa7e655aa378fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="961ef-102">IMetaDataAssemblyImport::EnumManifestResources メソッド</span><span class="sxs-lookup"><span data-stu-id="961ef-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="961ef-103">現在のアセンブリ マニフェストで参照されているリソースの列挙子へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="961ef-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="961ef-104">構文</span><span class="sxs-lookup"><span data-stu-id="961ef-104">Syntax</span></span>  
  
```  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="961ef-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="961ef-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="961ef-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="961ef-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="961ef-107">これは null を指定する必要があるときの値、`EnumManifestResources`メソッドは、最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="961ef-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="961ef-108">[out]配列の格納に使用される、`mdManifestResource`メタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="961ef-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="961ef-109">[in]最大数`mdManifestResource`に配置できるトークン`rManifestResources`です。</span><span class="sxs-lookup"><span data-stu-id="961ef-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="961ef-110">[out]数`mdManifestResource`にトークンが実際に配置されます`rManifestResources`です。</span><span class="sxs-lookup"><span data-stu-id="961ef-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="961ef-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="961ef-111">Return Value</span></span>  
  
|<span data-ttu-id="961ef-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="961ef-112">HRESULT</span></span>|<span data-ttu-id="961ef-113">説明</span><span class="sxs-lookup"><span data-stu-id="961ef-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="961ef-114">`EnumManifestResources`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="961ef-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="961ef-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="961ef-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="961ef-116">この場合、`pcTokens`は 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="961ef-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="961ef-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="961ef-117">Requirements</span></span>  
 <span data-ttu-id="961ef-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="961ef-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="961ef-119">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="961ef-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="961ef-120">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="961ef-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="961ef-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="961ef-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="961ef-122">参照</span><span class="sxs-lookup"><span data-stu-id="961ef-122">See Also</span></span>  
 [<span data-ttu-id="961ef-123">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="961ef-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
