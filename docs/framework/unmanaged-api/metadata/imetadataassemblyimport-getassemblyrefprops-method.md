---
title: "IMetaDataAssemblyImport::GetAssemblyRefProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetAssemblyRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76ae1d81db314530ab33a42cb99824da1745dff0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="5b30e-102">IMetaDataAssemblyImport::GetAssemblyRefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="5b30e-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="5b30e-103">指定したメタデータ シグネチャを持つアセンブリ参照のプロパティのセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="5b30e-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b30e-104">構文</span><span class="sxs-lookup"><span data-stu-id="5b30e-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,   
    [out] const void          **ppbPublicKeyOrToken,   
    [out] ULONG                *pcbPublicKeyOrToken,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] ASSEMBLYMETADATA     *pMetaData,   
    [out] const void           **ppbHashValue,   
    [out] ULONG                *pcbHashValue,   
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b30e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5b30e-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="5b30e-106">[in]`mdAssemblyRef`プロパティを取得する対象のアセンブリ参照を表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="5b30e-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="5b30e-107">[out]公開キーまたはメタデータ トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5b30e-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="5b30e-108">[out]返される公開キー、またはトークンのバイト数。</span><span class="sxs-lookup"><span data-stu-id="5b30e-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="5b30e-109">[out]アセンブリの簡易名。</span><span class="sxs-lookup"><span data-stu-id="5b30e-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5b30e-110">[in]ワイド文字単位のサイズの`szName`します。</span><span class="sxs-lookup"><span data-stu-id="5b30e-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="5b30e-111">[out]実際に返されるワイド文字数へのポインター`szName`です。</span><span class="sxs-lookup"><span data-stu-id="5b30e-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="5b30e-112">[out]アセンブリのメタデータを含む ASSEMBLYMETADATA 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5b30e-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="5b30e-113">[out]ハッシュ値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5b30e-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="5b30e-114">これは、sha-1 アルゴリズムを使用して、ハッシュ、 `PublicKey` 、arfFullOriginator のフラグを設定しない限り、参照されるアセンブリのプロパティ、 [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)列挙型を設定します。</span><span class="sxs-lookup"><span data-stu-id="5b30e-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="5b30e-115">[out]返されるハッシュ値のワイド文字の数。</span><span class="sxs-lookup"><span data-stu-id="5b30e-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="5b30e-116">[out]アセンブリに適用されるメタデータを記述するフラグをへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5b30e-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="5b30e-117">フラグの値は 1 つまたは複数の組み合わせ[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)値。</span><span class="sxs-lookup"><span data-stu-id="5b30e-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b30e-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="5b30e-118">Return Value</span></span>  
 <span data-ttu-id="5b30e-119">このメソッドは、それが成功した場合は S_OK を返します。それ以外の場合、Winerror.h ヘッダー ファイルで定義されているエラー コードのいずれかを返します。</span><span class="sxs-lookup"><span data-stu-id="5b30e-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b30e-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="5b30e-120">Requirements</span></span>  
 <span data-ttu-id="5b30e-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5b30e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b30e-122">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5b30e-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b30e-123">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="5b30e-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5b30e-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b30e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b30e-125">参照</span><span class="sxs-lookup"><span data-stu-id="5b30e-125">See Also</span></span>  
 [<span data-ttu-id="5b30e-126">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5b30e-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
