---
title: "IMetaDataEmit::Save メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.Save
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8a2e77ad9ce66a04ef0530dc41f9795c501eed9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="0b801-102">IMetaDataEmit::Save メソッド</span><span class="sxs-lookup"><span data-stu-id="0b801-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="0b801-103">指定したアドレスにファイルを現在のスコープ内のすべてのメタデータを保存します。</span><span class="sxs-lookup"><span data-stu-id="0b801-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b801-104">構文</span><span class="sxs-lookup"><span data-stu-id="0b801-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b801-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0b801-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="0b801-106">[in]保存先のファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="0b801-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="0b801-107">この値が null の場合は、メモリ内のコピーは最後に使用された場所に保存されます。</span><span class="sxs-lookup"><span data-stu-id="0b801-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="0b801-108">[in]予約されています。</span><span class="sxs-lookup"><span data-stu-id="0b801-108">[in] Reserved.</span></span> <span data-ttu-id="0b801-109">ゼロを指定してください。</span><span class="sxs-lookup"><span data-stu-id="0b801-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b801-110">要件</span><span class="sxs-lookup"><span data-stu-id="0b801-110">Requirements</span></span>  
 <span data-ttu-id="0b801-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0b801-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b801-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0b801-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b801-113">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="0b801-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b801-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b801-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b801-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b801-115">See Also</span></span>  
 [<span data-ttu-id="0b801-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b801-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="0b801-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b801-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
