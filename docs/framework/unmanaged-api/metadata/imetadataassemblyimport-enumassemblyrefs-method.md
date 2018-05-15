---
title: IMetaDataAssemblyImport::EnumAssemblyRefs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a56d874e5e7ef491c24b0aef2ace700087de677
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="6b658-102">IMetaDataAssemblyImport::EnumAssemblyRefs メソッド</span><span class="sxs-lookup"><span data-stu-id="6b658-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="6b658-103">列挙、`mdAssemblyRef`アセンブリ マニフェストで定義されているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="6b658-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b658-104">構文</span><span class="sxs-lookup"><span data-stu-id="6b658-104">Syntax</span></span>  
  
```  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b658-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6b658-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6b658-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6b658-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="6b658-107">これは null を指定する必要があるときの値、`EnumAssemblyRefs`メソッドは、最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6b658-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="6b658-108">[out]列挙体`mdAssemblyRef`メタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="6b658-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6b658-109">[in]配置可能なトークンの最大数、`rAssemblyRefs`配列。</span><span class="sxs-lookup"><span data-stu-id="6b658-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="6b658-110">[out]トークンの数が実際に配置`rAssemblyRefs`です。</span><span class="sxs-lookup"><span data-stu-id="6b658-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b658-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="6b658-111">Return Value</span></span>  
  
|<span data-ttu-id="6b658-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b658-112">HRESULT</span></span>|<span data-ttu-id="6b658-113">説明</span><span class="sxs-lookup"><span data-stu-id="6b658-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6b658-114">`EnumAssemblyRefs` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="6b658-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6b658-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="6b658-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="6b658-116">この場合、`pcTokens`は 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="6b658-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b658-117">要件</span><span class="sxs-lookup"><span data-stu-id="6b658-117">Requirements</span></span>  
 <span data-ttu-id="6b658-118">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b658-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b658-119">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6b658-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b658-120">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="6b658-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b658-121">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b658-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b658-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b658-122">See Also</span></span>  
 [<span data-ttu-id="6b658-123">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b658-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
