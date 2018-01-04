---
title: "IMetaDataAssemblyImport::FindExportedTypeByName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindExportedTypeByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 010e6c29541e4b55353db4359c018935c5e1ef2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="7c943-102">IMetaDataAssemblyImport::FindExportedTypeByName メソッド</span><span class="sxs-lookup"><span data-stu-id="7c943-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="7c943-103">名前およびそれを囲む型を指定、エクスポートされた型へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="7c943-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c943-104">構文</span><span class="sxs-lookup"><span data-stu-id="7c943-104">Syntax</span></span>  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c943-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7c943-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="7c943-106">[in]エクスポートされた型の名前。</span><span class="sxs-lookup"><span data-stu-id="7c943-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="7c943-107">[in]エクスポートされた型の外側のクラスのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="7c943-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="7c943-108">この値は`mdExportedTypeNil`型が入れ子にされた型ではない場合は、要求されたエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="7c943-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="7c943-109">[out]ポインター、`mdExportedType`エクスポートされた型を表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="7c943-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c943-110">コメント</span><span class="sxs-lookup"><span data-stu-id="7c943-110">Remarks</span></span>  
 <span data-ttu-id="7c943-111">`FindExportedTypeByName`メソッドは参照を解決するための共通言語ランタイムによって使用されている標準的な規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="7c943-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c943-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="7c943-112">Requirements</span></span>  
 <span data-ttu-id="7c943-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7c943-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c943-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7c943-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c943-115">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="7c943-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7c943-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c943-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c943-117">参照</span><span class="sxs-lookup"><span data-stu-id="7c943-117">See Also</span></span>  
 [<span data-ttu-id="7c943-118">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c943-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="7c943-119">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="7c943-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
