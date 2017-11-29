---
title: "IMetaDataAssemblyImport::GetFileProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetFileProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c4ca64d4781f0cc228c0af7f2ae772098d2f164a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="b3128-102">IMetaDataAssemblyImport::GetFileProps メソッド</span><span class="sxs-lookup"><span data-stu-id="b3128-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="b3128-103">指定したメタデータ シグネチャを持つファイルのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="b3128-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3128-104">構文</span><span class="sxs-lookup"><span data-stu-id="b3128-104">Syntax</span></span>  
  
```  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,   
    [out] LPWSTR      szName,   
    [in]  ULONG       cchName,   
    [out] ULONG       *pchName,   
    [out] const void  **ppbHashValue,   
    [out] ULONG       *pcbHashValue,   
    [out] DWORD       *pdwFileFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3128-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b3128-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="b3128-106">[in]`mdFile`プロパティを取得する対象のファイルを表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="b3128-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="b3128-107">[out]ファイルの簡易名。</span><span class="sxs-lookup"><span data-stu-id="b3128-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b3128-108">[in]ワイド文字単位のサイズの`szName`します。</span><span class="sxs-lookup"><span data-stu-id="b3128-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b3128-109">[out]実際に返されるワイド文字数`szName`です。</span><span class="sxs-lookup"><span data-stu-id="b3128-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="b3128-110">[out]ハッシュ値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b3128-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="b3128-111">これは、ファイルの sha-1 アルゴリズムを使用して、ハッシュです。</span><span class="sxs-lookup"><span data-stu-id="b3128-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="b3128-112">[out]返されるハッシュ値のワイド文字の数。</span><span class="sxs-lookup"><span data-stu-id="b3128-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="b3128-113">[out]ファイルに適用されるメタデータを記述するフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b3128-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="b3128-114">フラグの値は 1 つまたは複数の組み合わせ[CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)値。</span><span class="sxs-lookup"><span data-stu-id="b3128-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3128-115">要件</span><span class="sxs-lookup"><span data-stu-id="b3128-115">Requirements</span></span>  
 <span data-ttu-id="b3128-116">**Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b3128-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3128-117">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b3128-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3128-118">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="b3128-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3128-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3128-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3128-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3128-120">See Also</span></span>  
 [<span data-ttu-id="b3128-121">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b3128-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
