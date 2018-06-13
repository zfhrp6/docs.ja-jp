---
title: IMetaDataImport::GetModuleFromScope メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f1f8acc546c0d96aca079223200b43aec933f729
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447910"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="acb2b-102">IMetaDataImport::GetModuleFromScope メソッド</span><span class="sxs-lookup"><span data-stu-id="acb2b-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="acb2b-103">現在のメタデータ スコープ内で参照されるモジュールのメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="acb2b-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acb2b-104">構文</span><span class="sxs-lookup"><span data-stu-id="acb2b-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="acb2b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="acb2b-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="acb2b-106">[out]現在のメタデータ スコープで参照されているモジュールを表すトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="acb2b-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acb2b-107">要件</span><span class="sxs-lookup"><span data-stu-id="acb2b-107">Requirements</span></span>  
 <span data-ttu-id="acb2b-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="acb2b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acb2b-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="acb2b-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="acb2b-110">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="acb2b-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="acb2b-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acb2b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb2b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="acb2b-112">See Also</span></span>  
 [<span data-ttu-id="acb2b-113">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="acb2b-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="acb2b-114">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="acb2b-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
