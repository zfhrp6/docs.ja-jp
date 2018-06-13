---
title: IMetaDataFilter::MarkToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97f184bae4628f2aa357644188594396468671ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444153"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="7cee0-102">IMetaDataFilter::MarkToken メソッド</span><span class="sxs-lookup"><span data-stu-id="7cee0-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="7cee0-103">指定したメタデータ トークンが処理されたことを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="7cee0-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cee0-104">構文</span><span class="sxs-lookup"><span data-stu-id="7cee0-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7cee0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7cee0-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="7cee0-106">[in]処理済みとマークするトークンです。</span><span class="sxs-lookup"><span data-stu-id="7cee0-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cee0-107">要件</span><span class="sxs-lookup"><span data-stu-id="7cee0-107">Requirements</span></span>  
 <span data-ttu-id="7cee0-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7cee0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cee0-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7cee0-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7cee0-110">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="7cee0-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7cee0-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cee0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cee0-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7cee0-112">See Also</span></span>  
 [<span data-ttu-id="7cee0-113">IMetaDataFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7cee0-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
