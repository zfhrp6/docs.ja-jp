---
title: "IMetaDataAssemblyEmit::DefineExportedType メソッド"
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
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 59aae188e404ebc717a140fb7918e3fbf69f3f70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="1c695-102">IMetaDataAssemblyEmit::DefineExportedType メソッド</span><span class="sxs-lookup"><span data-stu-id="1c695-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="1c695-103">指定してエクスポートした型のメタデータが含まれる `ExportedType` 構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="1c695-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c695-104">構文</span><span class="sxs-lookup"><span data-stu-id="1c695-104">Syntax</span></span>  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c695-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c695-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="1c695-106">[in]エクスポートする型の名前。</span><span class="sxs-lookup"><span data-stu-id="1c695-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="1c695-107">エクスポートされた型の名前、共通言語ランタイムのバージョン 1.1 で指定された名前と一致する必要がありますの`TypeDef`の種類。</span><span class="sxs-lookup"><span data-stu-id="1c695-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="1c695-108">[in]エクスポートされた型が実装されているを指定するトークンです。</span><span class="sxs-lookup"><span data-stu-id="1c695-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="1c695-109">有効な値とその意味です。</span><span class="sxs-lookup"><span data-stu-id="1c695-109">The valid values and their associated meanings are:</span></span>  
  
-   <span data-ttu-id="1c695-110">`mdFile`種類は、このアセンブリ内の別のファイルに実装されます。</span><span class="sxs-lookup"><span data-stu-id="1c695-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
-   <span data-ttu-id="1c695-111">`mdAssemblyRef`種類は、別のアセンブリに実装されます。</span><span class="sxs-lookup"><span data-stu-id="1c695-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
-   <span data-ttu-id="1c695-112">`mdExportedTYpe`型は他のいくつかの型の中で入れ子になった。</span><span class="sxs-lookup"><span data-stu-id="1c695-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
-   <span data-ttu-id="1c695-113">`mdFileNil`型は、マニフェストと同じファイルでは、され、入れ子にされた型ではありません。</span><span class="sxs-lookup"><span data-stu-id="1c695-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="1c695-114">[in]エクスポートする型を指定するメタデータをトークンです。</span><span class="sxs-lookup"><span data-stu-id="1c695-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="1c695-115">この値が入力される、`TypeDef`型を実装し、そのファイルがこのアセンブリ内にある場合にのみ関連するファイル内のテーブルです。</span><span class="sxs-lookup"><span data-stu-id="1c695-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="1c695-116">[in]ビットごとの組み合わせ[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)エクスポートされた型のプロパティの設定を定義する列挙値。</span><span class="sxs-lookup"><span data-stu-id="1c695-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="1c695-117">[out]エクスポートされた型を示す、返されるメタデータ トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1c695-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c695-118">コメント</span><span class="sxs-lookup"><span data-stu-id="1c695-118">Remarks</span></span>  
 <span data-ttu-id="1c695-119">`ExportedType`このアセンブリによって公開されると、モジュール マニフェストを含む 1 つ以外で実装される各型のメタデータ構造体を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c695-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c695-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="1c695-120">Requirements</span></span>  
 <span data-ttu-id="1c695-121">**Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1c695-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c695-122">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1c695-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1c695-123">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="1c695-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1c695-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c695-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c695-125">参照</span><span class="sxs-lookup"><span data-stu-id="1c695-125">See Also</span></span>  
 [<span data-ttu-id="1c695-126">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1c695-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
