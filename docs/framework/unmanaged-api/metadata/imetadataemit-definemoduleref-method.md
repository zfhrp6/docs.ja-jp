---
title: "IMetaDataEmit::DefineModuleRef メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineModuleRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b745e216ca49ed5d226d6d531281880b43e4939
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="dd710-102">IMetaDataEmit::DefineModuleRef メソッド</span><span class="sxs-lookup"><span data-stu-id="dd710-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="dd710-103">指定した名前のモジュールのメタデータ署名を作成します。</span><span class="sxs-lookup"><span data-stu-id="dd710-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd710-104">構文</span><span class="sxs-lookup"><span data-stu-id="dd710-104">Syntax</span></span>  
  
```  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd710-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dd710-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="dd710-106">[in]その他のメタデータ ファイル、DLL では通常の名前。</span><span class="sxs-lookup"><span data-stu-id="dd710-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="dd710-107">これは、ファイル名のみです。</span><span class="sxs-lookup"><span data-stu-id="dd710-107">This is the file name only.</span></span> <span data-ttu-id="dd710-108">完全なパス名を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="dd710-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="dd710-109">[out]割り当てられている`mdModuleRef`トークンです。</span><span class="sxs-lookup"><span data-stu-id="dd710-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd710-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="dd710-110">Requirements</span></span>  
 <span data-ttu-id="dd710-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd710-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd710-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd710-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd710-113">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="dd710-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd710-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd710-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd710-115">参照</span><span class="sxs-lookup"><span data-stu-id="dd710-115">See Also</span></span>  
 [<span data-ttu-id="dd710-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd710-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="dd710-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd710-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
