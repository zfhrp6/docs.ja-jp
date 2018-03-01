---
title: "IMetaDataEmit::SaveToStream メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 135faea41ab1a8165e315b8d0815abc48ba7fd38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="d1562-102">IMetaDataEmit::SaveToStream メソッド</span><span class="sxs-lookup"><span data-stu-id="d1562-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="d1562-103">現在のスコープを指定したすべてのメタデータを保存`IStream`です。</span><span class="sxs-lookup"><span data-stu-id="d1562-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1562-104">構文</span><span class="sxs-lookup"><span data-stu-id="d1562-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1562-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d1562-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="d1562-106">[in]保存する書き込み可能なストリーム。</span><span class="sxs-lookup"><span data-stu-id="d1562-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="d1562-107">[in]予約されています。</span><span class="sxs-lookup"><span data-stu-id="d1562-107">[in] Reserved.</span></span> <span data-ttu-id="d1562-108">ゼロを指定してください。</span><span class="sxs-lookup"><span data-stu-id="d1562-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1562-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="d1562-109">Requirements</span></span>  
 <span data-ttu-id="d1562-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d1562-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1562-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d1562-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1562-112">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="d1562-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1562-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1562-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1562-114">参照</span><span class="sxs-lookup"><span data-stu-id="d1562-114">See Also</span></span>  
 [<span data-ttu-id="d1562-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d1562-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d1562-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d1562-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
