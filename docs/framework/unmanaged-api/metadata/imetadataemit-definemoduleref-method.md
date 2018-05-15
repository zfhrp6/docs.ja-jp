---
title: IMetaDataEmit::DefineModuleRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineModuleRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4503c3c745fde148c77ff30c9ece008dd9d54829
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="4260f-102">IMetaDataEmit::DefineModuleRef メソッド</span><span class="sxs-lookup"><span data-stu-id="4260f-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="4260f-103">指定した名前のモジュールのメタデータ署名を作成します。</span><span class="sxs-lookup"><span data-stu-id="4260f-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4260f-104">構文</span><span class="sxs-lookup"><span data-stu-id="4260f-104">Syntax</span></span>  
  
```  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4260f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4260f-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="4260f-106">[in]その他のメタデータ ファイル、DLL では通常の名前。</span><span class="sxs-lookup"><span data-stu-id="4260f-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="4260f-107">これは、ファイル名のみです。</span><span class="sxs-lookup"><span data-stu-id="4260f-107">This is the file name only.</span></span> <span data-ttu-id="4260f-108">完全なパス名を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="4260f-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="4260f-109">[out]割り当てられている`mdModuleRef`トークンです。</span><span class="sxs-lookup"><span data-stu-id="4260f-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4260f-110">要件</span><span class="sxs-lookup"><span data-stu-id="4260f-110">Requirements</span></span>  
 <span data-ttu-id="4260f-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4260f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4260f-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4260f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4260f-113">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="4260f-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4260f-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4260f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4260f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="4260f-115">See Also</span></span>  
 [<span data-ttu-id="4260f-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4260f-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4260f-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4260f-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
