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
ms.openlocfilehash: b7ef0e09cb5a44e612e545fc4ee7278c2d128174
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="16acf-102">IMetaDataAssemblyImport::FindExportedTypeByName メソッド</span><span class="sxs-lookup"><span data-stu-id="16acf-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="16acf-103">名前およびそれを囲む型を指定、エクスポートされた型へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="16acf-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16acf-104">構文</span><span class="sxs-lookup"><span data-stu-id="16acf-104">Syntax</span></span>  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16acf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="16acf-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="16acf-106">[in]エクスポートされた型の名前。</span><span class="sxs-lookup"><span data-stu-id="16acf-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="16acf-107">[in]エクスポートされた型の外側のクラスのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="16acf-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="16acf-108">この値は`mdExportedTypeNil`型が入れ子にされた型ではない場合は、要求されたエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="16acf-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="16acf-109">[out]ポインター、`mdExportedType`エクスポートされた型を表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="16acf-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16acf-110">コメント</span><span class="sxs-lookup"><span data-stu-id="16acf-110">Remarks</span></span>  
 <span data-ttu-id="16acf-111">`FindExportedTypeByName`メソッドは参照を解決するための共通言語ランタイムによって使用されている標準的な規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="16acf-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16acf-112">要件</span><span class="sxs-lookup"><span data-stu-id="16acf-112">Requirements</span></span>  
 <span data-ttu-id="16acf-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="16acf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16acf-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="16acf-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16acf-115">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="16acf-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16acf-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16acf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16acf-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="16acf-117">See Also</span></span>  
 [<span data-ttu-id="16acf-118">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="16acf-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="16acf-119">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="16acf-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
