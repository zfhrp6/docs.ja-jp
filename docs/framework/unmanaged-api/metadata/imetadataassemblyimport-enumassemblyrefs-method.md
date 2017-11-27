---
title: "IMetaDataAssemblyImport::EnumAssemblyRefs メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumAssemblyRefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 24a289ed42a99cd26c7829d9a5789ac3027026c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="3cb03-102">IMetaDataAssemblyImport::EnumAssemblyRefs メソッド</span><span class="sxs-lookup"><span data-stu-id="3cb03-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="3cb03-103">列挙、`mdAssemblyRef`アセンブリ マニフェストで定義されているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="3cb03-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cb03-104">構文</span><span class="sxs-lookup"><span data-stu-id="3cb03-104">Syntax</span></span>  
  
```  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3cb03-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3cb03-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3cb03-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3cb03-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3cb03-107">これは null を指定する必要があるときの値、`EnumAssemblyRefs`メソッドは、最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3cb03-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="3cb03-108">[out]列挙体`mdAssemblyRef`メタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="3cb03-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3cb03-109">[in]配置可能なトークンの最大数、`rAssemblyRefs`配列。</span><span class="sxs-lookup"><span data-stu-id="3cb03-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="3cb03-110">[out]トークンの数が実際に配置`rAssemblyRefs`です。</span><span class="sxs-lookup"><span data-stu-id="3cb03-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cb03-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="3cb03-111">Return Value</span></span>  
  
|<span data-ttu-id="3cb03-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3cb03-112">HRESULT</span></span>|<span data-ttu-id="3cb03-113">説明</span><span class="sxs-lookup"><span data-stu-id="3cb03-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3cb03-114">`EnumAssemblyRefs`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="3cb03-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3cb03-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="3cb03-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="3cb03-116">この場合、`pcTokens`は 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="3cb03-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3cb03-117">要件</span><span class="sxs-lookup"><span data-stu-id="3cb03-117">Requirements</span></span>  
 <span data-ttu-id="3cb03-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3cb03-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cb03-119">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3cb03-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3cb03-120">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="3cb03-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3cb03-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cb03-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb03-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="3cb03-122">See Also</span></span>  
 [<span data-ttu-id="3cb03-123">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3cb03-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
