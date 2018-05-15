---
title: IMetaDataEmit::DeleteToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteToken
helpviewer_keywords:
- DeleteToken method [.NET Framework metadata]
- IMetaDataEmit::DeleteToken method [.NET Framework metadata]
ms.assetid: a4926d0a-261b-46b1-9994-82633661a64b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 269dac0f3d8a719224c177ef2c261e4c1e2e7e92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="f68ff-102">IMetaDataEmit::DeleteToken メソッド</span><span class="sxs-lookup"><span data-stu-id="f68ff-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="f68ff-103">現在のメタデータ スコープから、指定されたトークンを削除します。</span><span class="sxs-lookup"><span data-stu-id="f68ff-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f68ff-104">構文</span><span class="sxs-lookup"><span data-stu-id="f68ff-104">Syntax</span></span>  
  
```  
HRESULT DeleteToken (   
    [in]  mdToken     tkObj   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f68ff-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f68ff-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="f68ff-106">[in]削除するトークンです。</span><span class="sxs-lookup"><span data-stu-id="f68ff-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f68ff-107">要件</span><span class="sxs-lookup"><span data-stu-id="f68ff-107">Requirements</span></span>  
 <span data-ttu-id="f68ff-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f68ff-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f68ff-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f68ff-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f68ff-110">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="f68ff-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f68ff-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f68ff-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f68ff-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="f68ff-112">See Also</span></span>  
 [<span data-ttu-id="f68ff-113">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f68ff-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f68ff-114">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f68ff-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
