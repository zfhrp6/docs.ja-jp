---
title: "IMetaDataEmit::SaveToStream メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SaveToStream
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 97f65fb6cfb7067ed4e6929772f0f114cedcf787
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="060b5-102">IMetaDataEmit::SaveToStream メソッド</span><span class="sxs-lookup"><span data-stu-id="060b5-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="060b5-103">現在のスコープを指定したすべてのメタデータを保存`IStream`です。</span><span class="sxs-lookup"><span data-stu-id="060b5-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="060b5-104">構文</span><span class="sxs-lookup"><span data-stu-id="060b5-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="060b5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="060b5-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="060b5-106">[in]保存する書き込み可能なストリーム。</span><span class="sxs-lookup"><span data-stu-id="060b5-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="060b5-107">[in]予約されています。</span><span class="sxs-lookup"><span data-stu-id="060b5-107">[in] Reserved.</span></span> <span data-ttu-id="060b5-108">ゼロを指定してください。</span><span class="sxs-lookup"><span data-stu-id="060b5-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="060b5-109">要件</span><span class="sxs-lookup"><span data-stu-id="060b5-109">Requirements</span></span>  
 <span data-ttu-id="060b5-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="060b5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="060b5-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="060b5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="060b5-112">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="060b5-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="060b5-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="060b5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="060b5-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="060b5-114">See Also</span></span>  
 [<span data-ttu-id="060b5-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="060b5-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="060b5-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="060b5-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
