---
title: "IMetaDataEmit2::SaveDeltaToMemory メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.SaveDeltaToMemory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f4243840ac64a14b4f4e6c86787fdf238507635
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="d6ea4-102">IMetaDataEmit2::SaveDeltaToMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="d6ea4-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="d6ea4-103">エディット コンティニュの現在のセッションからの変更をメモリに保存します。</span><span class="sxs-lookup"><span data-stu-id="d6ea4-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ea4-104">構文</span><span class="sxs-lookup"><span data-stu-id="d6ea4-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6ea4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d6ea4-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="d6ea4-106">[out]メタデータのデルタの書き込みを開始する位置を示すアドレス。</span><span class="sxs-lookup"><span data-stu-id="d6ea4-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="d6ea4-107">[in]変更のサイズ。</span><span class="sxs-lookup"><span data-stu-id="d6ea4-107">[in] The size of the changes.</span></span> <span data-ttu-id="d6ea4-108">使用して[imetadataemit 2::getdeltasavesize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)サイズを決定します。</span><span class="sxs-lookup"><span data-stu-id="d6ea4-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6ea4-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="d6ea4-109">Requirements</span></span>  
 <span data-ttu-id="d6ea4-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d6ea4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6ea4-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d6ea4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6ea4-112">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="d6ea4-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6ea4-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6ea4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ea4-114">参照</span><span class="sxs-lookup"><span data-stu-id="d6ea4-114">See Also</span></span>  
 [<span data-ttu-id="d6ea4-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6ea4-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="d6ea4-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6ea4-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
