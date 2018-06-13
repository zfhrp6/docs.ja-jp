---
title: IMetaDataImport::ResetEnum メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResetEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 56fc0273fb2c1b77c74d7a1d853886f47170497e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447929"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="476d6-102">IMetaDataImport::ResetEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="476d6-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="476d6-103">指定した列挙子を指定した位置にリセットします。</span><span class="sxs-lookup"><span data-stu-id="476d6-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="476d6-104">構文</span><span class="sxs-lookup"><span data-stu-id="476d6-104">Syntax</span></span>  
  
```  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="476d6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="476d6-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="476d6-106">[in]リセットする列挙子。</span><span class="sxs-lookup"><span data-stu-id="476d6-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="476d6-107">[in]新しい位置を列挙子を配置します。</span><span class="sxs-lookup"><span data-stu-id="476d6-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="476d6-108">要件</span><span class="sxs-lookup"><span data-stu-id="476d6-108">Requirements</span></span>  
 <span data-ttu-id="476d6-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="476d6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="476d6-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="476d6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="476d6-111">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="476d6-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="476d6-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="476d6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="476d6-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="476d6-113">See Also</span></span>  
 [<span data-ttu-id="476d6-114">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="476d6-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="476d6-115">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="476d6-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
