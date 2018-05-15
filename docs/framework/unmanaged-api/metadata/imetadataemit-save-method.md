---
title: IMetaDataEmit::Save メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a6d97d3e4a93985f9b2de3ed9785eff5f7f46c36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="ff5f2-102">IMetaDataEmit::Save メソッド</span><span class="sxs-lookup"><span data-stu-id="ff5f2-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="ff5f2-103">指定したアドレスにファイルを現在のスコープ内のすべてのメタデータを保存します。</span><span class="sxs-lookup"><span data-stu-id="ff5f2-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff5f2-104">構文</span><span class="sxs-lookup"><span data-stu-id="ff5f2-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff5f2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff5f2-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="ff5f2-106">[in]保存先のファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="ff5f2-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="ff5f2-107">この値が null の場合は、メモリ内のコピーは最後に使用された場所に保存されます。</span><span class="sxs-lookup"><span data-stu-id="ff5f2-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="ff5f2-108">[in]予約されています。</span><span class="sxs-lookup"><span data-stu-id="ff5f2-108">[in] Reserved.</span></span> <span data-ttu-id="ff5f2-109">ゼロを指定してください。</span><span class="sxs-lookup"><span data-stu-id="ff5f2-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff5f2-110">要件</span><span class="sxs-lookup"><span data-stu-id="ff5f2-110">Requirements</span></span>  
 <span data-ttu-id="ff5f2-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ff5f2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff5f2-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ff5f2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff5f2-113">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="ff5f2-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff5f2-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff5f2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff5f2-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff5f2-115">See Also</span></span>  
 [<span data-ttu-id="ff5f2-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ff5f2-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ff5f2-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ff5f2-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
