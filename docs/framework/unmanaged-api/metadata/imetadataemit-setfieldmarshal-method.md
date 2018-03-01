---
title: "IMetaDataEmit::SetFieldMarshal メソッド"
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
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 20186870510e67e518414d2bd5e9a00fd5164dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="198e9-102">IMetaDataEmit::SetFieldMarshal メソッド</span><span class="sxs-lookup"><span data-stu-id="198e9-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="198e9-103">指定したトークンによって参照されるフィールド、メソッドの戻り値、またはメソッドのパラメーターのマーシャ リング情報 PInvoke に設定します。</span><span class="sxs-lookup"><span data-stu-id="198e9-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="198e9-104">構文</span><span class="sxs-lookup"><span data-stu-id="198e9-104">Syntax</span></span>  
  
```  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="198e9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="198e9-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="198e9-106">[in]ターゲット データ項目のトークンです。</span><span class="sxs-lookup"><span data-stu-id="198e9-106">[in] The token for target data item.</span></span> <span data-ttu-id="198e9-107">これは、いずれか、`mdFieldDef`または`mdParamDef`トークンです。</span><span class="sxs-lookup"><span data-stu-id="198e9-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="198e9-108">[in]アンマネージ型のシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="198e9-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="198e9-109">[in]内のバイト数`pvNativeType`です。</span><span class="sxs-lookup"><span data-stu-id="198e9-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="198e9-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="198e9-110">Requirements</span></span>  
 <span data-ttu-id="198e9-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="198e9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="198e9-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="198e9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="198e9-113">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="198e9-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="198e9-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="198e9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="198e9-115">参照</span><span class="sxs-lookup"><span data-stu-id="198e9-115">See Also</span></span>  
 [<span data-ttu-id="198e9-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="198e9-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="198e9-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="198e9-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
