---
title: "IMetaDataFilter::IsTokenMarked メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataFilter.IsTokenMarked
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d140e81d98e99982789d8d8999329cda3524acd5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="c04f6-102">IMetaDataFilter::IsTokenMarked メソッド</span><span class="sxs-lookup"><span data-stu-id="c04f6-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="c04f6-103">指定したメタデータ トークンが処理済みとマークされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="c04f6-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c04f6-104">構文</span><span class="sxs-lookup"><span data-stu-id="c04f6-104">Syntax</span></span>  
  
```  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,   
    [out] BOOL     *pIsMarked  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c04f6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c04f6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="c04f6-106">[in]処理のマークがないか調査するトークン。</span><span class="sxs-lookup"><span data-stu-id="c04f6-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="c04f6-107">[out]値が`true`場合`tk`それ以外の処理がされて`false`です。</span><span class="sxs-lookup"><span data-stu-id="c04f6-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c04f6-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="c04f6-108">Requirements</span></span>  
 <span data-ttu-id="c04f6-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c04f6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c04f6-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c04f6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c04f6-111">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="c04f6-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c04f6-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c04f6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c04f6-113">参照</span><span class="sxs-lookup"><span data-stu-id="c04f6-113">See Also</span></span>  
 [<span data-ttu-id="c04f6-114">IMetaDataFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c04f6-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
