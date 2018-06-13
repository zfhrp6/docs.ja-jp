---
title: IMetaDataImport::IsValidToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d752d6dbe8a6b7a23faae498f9118c8d89e92929
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447698"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="52eba-102">IMetaDataImport::IsValidToken メソッド</span><span class="sxs-lookup"><span data-stu-id="52eba-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="52eba-103">指定したトークンが、コード オブジェクトへの有効な参照を保持しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="52eba-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52eba-104">構文</span><span class="sxs-lookup"><span data-stu-id="52eba-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52eba-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52eba-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="52eba-106">[in]参照の有効性を確認するトークン。</span><span class="sxs-lookup"><span data-stu-id="52eba-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52eba-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="52eba-107">Return Value</span></span>  
 <span data-ttu-id="52eba-108">`true` 場合`tk`現在のスコープ内で有効なメタデータ トークンします。</span><span class="sxs-lookup"><span data-stu-id="52eba-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="52eba-109">それ以外の場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="52eba-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52eba-110">要件</span><span class="sxs-lookup"><span data-stu-id="52eba-110">Requirements</span></span>  
 <span data-ttu-id="52eba-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="52eba-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52eba-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="52eba-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52eba-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="52eba-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52eba-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52eba-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52eba-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="52eba-115">See Also</span></span>  
 [<span data-ttu-id="52eba-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52eba-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="52eba-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52eba-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
