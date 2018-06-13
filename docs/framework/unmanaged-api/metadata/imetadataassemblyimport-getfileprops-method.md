---
title: IMetaDataAssemblyImport::GetFileProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f147fef90d7a9033bdfd07b75e5c33efd2c6881f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444517"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="8a0a2-102">IMetaDataAssemblyImport::GetFileProps メソッド</span><span class="sxs-lookup"><span data-stu-id="8a0a2-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="8a0a2-103">指定したメタデータ シグネチャを持つファイルのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="8a0a2-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a0a2-104">構文</span><span class="sxs-lookup"><span data-stu-id="8a0a2-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="8a0a2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a0a2-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="8a0a2-106">[in]`mdFile`プロパティを取得する対象のファイルを表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="8a0a2-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="8a0a2-107">[out]ファイルの簡易名。</span><span class="sxs-lookup"><span data-stu-id="8a0a2-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8a0a2-108">[in]ワイド文字単位のサイズの`szName`します。</span><span class="sxs-lookup"><span data-stu-id="8a0a2-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="8a0a2-109">[out]実際に返されるワイド文字数`szName`です。</span><span class="sxs-lookup"><span data-stu-id="8a0a2-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="8a0a2-110">[out]ハッシュ値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8a0a2-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="8a0a2-111">これは、ファイルの sha-1 アルゴリズムを使用して、ハッシュです。</span><span class="sxs-lookup"><span data-stu-id="8a0a2-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="8a0a2-112">[out]返されるハッシュ値のワイド文字の数。</span><span class="sxs-lookup"><span data-stu-id="8a0a2-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="8a0a2-113">[out]ファイルに適用されるメタデータを記述するフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8a0a2-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="8a0a2-114">フラグの値は 1 つまたは複数の組み合わせ[CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)値。</span><span class="sxs-lookup"><span data-stu-id="8a0a2-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a0a2-115">要件</span><span class="sxs-lookup"><span data-stu-id="8a0a2-115">Requirements</span></span>  
 <span data-ttu-id="8a0a2-116">**Platform:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8a0a2-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a0a2-117">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8a0a2-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a0a2-118">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="8a0a2-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a0a2-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a0a2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a0a2-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a0a2-120">See Also</span></span>  
 [<span data-ttu-id="8a0a2-121">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a0a2-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
