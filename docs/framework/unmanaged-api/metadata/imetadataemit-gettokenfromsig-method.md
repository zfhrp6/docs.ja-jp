---
title: IMetaDataEmit::GetTokenFromSig メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be42fea034be4fe5d48874b00db86977a3039a34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448221"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="52145-102">IMetaDataEmit::GetTokenFromSig メソッド</span><span class="sxs-lookup"><span data-stu-id="52145-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="52145-103">指定されたメタデータ署名のトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="52145-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52145-104">構文</span><span class="sxs-lookup"><span data-stu-id="52145-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52145-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52145-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="52145-106">[in]永続化され、格納されている署名します。</span><span class="sxs-lookup"><span data-stu-id="52145-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="52145-107">[in]内のバイト数`pvSig`です。</span><span class="sxs-lookup"><span data-stu-id="52145-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="52145-108">[out]`mdSignature`トークンが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="52145-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52145-109">要件</span><span class="sxs-lookup"><span data-stu-id="52145-109">Requirements</span></span>  
 <span data-ttu-id="52145-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="52145-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52145-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="52145-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52145-112">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="52145-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52145-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52145-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52145-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="52145-114">See Also</span></span>  
 [<span data-ttu-id="52145-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52145-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="52145-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52145-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
