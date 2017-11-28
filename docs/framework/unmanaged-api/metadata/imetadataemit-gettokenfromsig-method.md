---
title: "IMetaDataEmit::GetTokenFromSig メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.GetTokenFromSig
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aefd95f62fce70f87c0724cbb4013462a449c7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="99d12-102">IMetaDataEmit::GetTokenFromSig メソッド</span><span class="sxs-lookup"><span data-stu-id="99d12-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="99d12-103">指定されたメタデータ署名のトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="99d12-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99d12-104">構文</span><span class="sxs-lookup"><span data-stu-id="99d12-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99d12-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="99d12-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="99d12-106">[in]永続化され、格納されている署名します。</span><span class="sxs-lookup"><span data-stu-id="99d12-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="99d12-107">[in]内のバイト数`pvSig`です。</span><span class="sxs-lookup"><span data-stu-id="99d12-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="99d12-108">[out]`mdSignature`トークンが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="99d12-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99d12-109">要件</span><span class="sxs-lookup"><span data-stu-id="99d12-109">Requirements</span></span>  
 <span data-ttu-id="99d12-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="99d12-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99d12-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="99d12-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99d12-112">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="99d12-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99d12-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99d12-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99d12-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="99d12-114">See Also</span></span>  
 [<span data-ttu-id="99d12-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99d12-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="99d12-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99d12-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
