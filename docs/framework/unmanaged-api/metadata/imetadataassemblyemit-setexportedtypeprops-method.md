---
title: "IMetaDataAssemblyEmit::SetExportedTypeProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetExportedTypeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c41cc2c6433139f1e1f355585e4af0a8f01c7c94
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="74b81-102">IMetaDataAssemblyEmit::SetExportedTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="74b81-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="74b81-103">指定された `ExportedType` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="74b81-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74b81-104">構文</span><span class="sxs-lookup"><span data-stu-id="74b81-104">Syntax</span></span>  
  
```  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74b81-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="74b81-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="74b81-106">[in]メタデータ トークンを指定する、`ExportedType`メタデータ構造体を変更できます。</span><span class="sxs-lookup"><span data-stu-id="74b81-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="74b81-107">[in]型のトークン、 `File`、 `AssemblyRef`、または`ExportedType`、この型の実装方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="74b81-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="74b81-108">[in]`TypeDef`コード ファイルで参照されているトークンです。</span><span class="sxs-lookup"><span data-stu-id="74b81-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="74b81-109">[in]型の属性を指定する値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="74b81-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74b81-110">コメント</span><span class="sxs-lookup"><span data-stu-id="74b81-110">Remarks</span></span>  
 <span data-ttu-id="74b81-111">作成する、`ExportedType`メタデータ構造体を使用して、 [imetadataassemblyemit::defineexportedtype](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="74b81-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74b81-112">要件</span><span class="sxs-lookup"><span data-stu-id="74b81-112">Requirements</span></span>  
 <span data-ttu-id="74b81-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="74b81-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74b81-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="74b81-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74b81-115">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="74b81-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="74b81-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74b81-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74b81-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="74b81-117">See Also</span></span>  
 [<span data-ttu-id="74b81-118">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74b81-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
