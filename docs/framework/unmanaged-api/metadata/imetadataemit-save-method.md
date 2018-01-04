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
ms.workload: dotnet
ms.openlocfilehash: a11241894116f57889a15a184290cd95f2f4f54f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="661dc-102">IMetaDataEmit::Save メソッド</span><span class="sxs-lookup"><span data-stu-id="661dc-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="661dc-103">指定したアドレスにファイルを現在のスコープ内のすべてのメタデータを保存します。</span><span class="sxs-lookup"><span data-stu-id="661dc-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="661dc-104">構文</span><span class="sxs-lookup"><span data-stu-id="661dc-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="661dc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="661dc-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="661dc-106">[in]保存先のファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="661dc-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="661dc-107">この値が null の場合は、メモリ内のコピーは最後に使用された場所に保存されます。</span><span class="sxs-lookup"><span data-stu-id="661dc-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="661dc-108">[in]予約されています。</span><span class="sxs-lookup"><span data-stu-id="661dc-108">[in] Reserved.</span></span> <span data-ttu-id="661dc-109">ゼロを指定してください。</span><span class="sxs-lookup"><span data-stu-id="661dc-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="661dc-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="661dc-110">Requirements</span></span>  
 <span data-ttu-id="661dc-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="661dc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="661dc-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="661dc-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="661dc-113">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="661dc-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="661dc-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="661dc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="661dc-115">参照</span><span class="sxs-lookup"><span data-stu-id="661dc-115">See Also</span></span>  
 [<span data-ttu-id="661dc-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="661dc-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="661dc-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="661dc-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
