---
title: IHostFilter::MarkToken メソッド
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52375486eb9d7780a51808dedc5f876587efb115
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="bf422-102">IHostFilter::MarkToken メソッド</span><span class="sxs-lookup"><span data-stu-id="bf422-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="bf422-103">指定したメタデータ トークンが処理されることを示します。</span><span class="sxs-lookup"><span data-stu-id="bf422-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf422-104">構文</span><span class="sxs-lookup"><span data-stu-id="bf422-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf422-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bf422-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="bf422-106">[in]処理するメタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="bf422-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf422-107">コメント</span><span class="sxs-lookup"><span data-stu-id="bf422-107">Remarks</span></span>  
 <span data-ttu-id="bf422-108">通常、トークンのメタデータ スコープ内にあるときに処理します。</span><span class="sxs-lookup"><span data-stu-id="bf422-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="bf422-109">`MarkToken`メソッドが経由でメタデータ エンジンに渡される、 [imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bf422-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf422-110">要件</span><span class="sxs-lookup"><span data-stu-id="bf422-110">Requirements</span></span>  
 <span data-ttu-id="bf422-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bf422-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf422-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bf422-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf422-113">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="bf422-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bf422-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf422-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf422-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf422-115">See Also</span></span>  
 [<span data-ttu-id="bf422-116">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bf422-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="bf422-117">IHostFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bf422-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
