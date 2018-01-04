---
title: "IMetaDataAssemblyImport::GetAssemblyProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetAssemblyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e99474fea329f53286d698d0e1a302909d5cc65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="c0e6f-102">IMetaDataAssemblyImport::GetAssemblyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="c0e6f-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="c0e6f-103">指定したメタデータ シグネチャを持つアセンブリのプロパティのセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="c0e6f-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0e6f-104">構文</span><span class="sxs-lookup"><span data-stu-id="c0e6f-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0e6f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c0e6f-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="c0e6f-106">[in] です。</span><span class="sxs-lookup"><span data-stu-id="c0e6f-106">[in].</span></span> <span data-ttu-id="c0e6f-107">`mdAssembly`プロパティを取得する対象のアセンブリを表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="c0e6f-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="c0e6f-108">[out]公開キーまたはメタデータ トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c0e6f-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="c0e6f-109">[out]返されたパブリック キー内のバイト数。</span><span class="sxs-lookup"><span data-stu-id="c0e6f-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="c0e6f-110">[out]アセンブリ内のファイルのハッシュに使用されるアルゴリズムへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c0e6f-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="c0e6f-111">[out]アセンブリの簡易名。</span><span class="sxs-lookup"><span data-stu-id="c0e6f-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c0e6f-112">[in]ワイド文字単位のサイズの`szName`します。</span><span class="sxs-lookup"><span data-stu-id="c0e6f-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="c0e6f-113">[out]実際に返されるワイド文字数`szName`です。</span><span class="sxs-lookup"><span data-stu-id="c0e6f-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="c0e6f-114">[out]アセンブリのメタデータを含む ASSEMBLYMETADATA 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c0e6f-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="c0e6f-115">[out]アセンブリに適用されるメタデータを記述するフラグ。</span><span class="sxs-lookup"><span data-stu-id="c0e6f-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="c0e6f-116">この値は 1 つまたは複数の組み合わせ[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)値。</span><span class="sxs-lookup"><span data-stu-id="c0e6f-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0e6f-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="c0e6f-117">Requirements</span></span>  
 <span data-ttu-id="c0e6f-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c0e6f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0e6f-119">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c0e6f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0e6f-120">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="c0e6f-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c0e6f-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0e6f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e6f-122">参照</span><span class="sxs-lookup"><span data-stu-id="c0e6f-122">See Also</span></span>  
 [<span data-ttu-id="c0e6f-123">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c0e6f-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
