---
title: "IMetaDataAssemblyEmit::DefineManifestResource メソッド"
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
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a435c946e13950faad7545e3da78ce373ee7fa0d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="9725a-102">IMetaDataAssemblyEmit::DefineManifestResource メソッド</span><span class="sxs-lookup"><span data-stu-id="9725a-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="9725a-103">指定したマニフェスト リソースのメタデータを含む `ManifestResource` 構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="9725a-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9725a-104">構文</span><span class="sxs-lookup"><span data-stu-id="9725a-104">Syntax</span></span>  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9725a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9725a-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="9725a-106">[in]リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="9725a-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="9725a-107">[in]型のメタデータ トークン`mdtFile`または`mdtAssemblyRef`リソース プロバイダーにマップします。</span><span class="sxs-lookup"><span data-stu-id="9725a-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="9725a-108">NULL 値のメタデータが埋め込まれているファイルが、リソース プロバイダーであることを示します。</span><span class="sxs-lookup"><span data-stu-id="9725a-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="9725a-109">[in]ファイル内のリソースの先頭までのオフセット。</span><span class="sxs-lookup"><span data-stu-id="9725a-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="9725a-110">スタンドアロン ファイル内のリソースのこの常に 0 になります。</span><span class="sxs-lookup"><span data-stu-id="9725a-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="9725a-111">PE (ポータブル実行可能) ファイルには、リソースが埋め込まれている場合はリソース cor.h ヘッダー ファイルで指定された位置から開始する BLOB のオフセットです。</span><span class="sxs-lookup"><span data-stu-id="9725a-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="9725a-112">[in]リソース定義のプロパティ設定を指定するフラグ値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="9725a-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="9725a-113">[out]返されるメタデータ トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9725a-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9725a-114">コメント</span><span class="sxs-lookup"><span data-stu-id="9725a-114">Remarks</span></span>  
 <span data-ttu-id="9725a-115">1 つ`ManifestResource`の各アセンブリのファイルで実装されている各リソースのメタデータ構造体を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9725a-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9725a-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="9725a-116">Requirements</span></span>  
 <span data-ttu-id="9725a-117">**Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9725a-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9725a-118">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9725a-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9725a-119">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="9725a-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9725a-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9725a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9725a-121">参照</span><span class="sxs-lookup"><span data-stu-id="9725a-121">See Also</span></span>  
 [<span data-ttu-id="9725a-122">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9725a-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
