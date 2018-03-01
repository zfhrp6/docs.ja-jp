---
title: "IMetaDataEmit::SetMethodProps メソッド"
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
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 28ec0ba45a83ccf51cc84ee9deb2c658b9b106bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="f94c2-102">IMetaDataEmit::SetMethodProps メソッド</span><span class="sxs-lookup"><span data-stu-id="f94c2-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="f94c2-103">設定または、指定の相対仮想アドレス、前回の呼び出しによって定義されたメソッドに格納されている、この機能を更新[imetadataemit::definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="f94c2-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f94c2-104">構文</span><span class="sxs-lookup"><span data-stu-id="f94c2-104">Syntax</span></span>  
  
```  
HRESULT SetMethodProps (   
    [in]  mdMethodDef md,   
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,   
    [in]  DWORD       dwImplFlags   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f94c2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f94c2-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="f94c2-106">[in]変更するメソッドのトークン。</span><span class="sxs-lookup"><span data-stu-id="f94c2-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="f94c2-107">[in]メンバーの属性です。</span><span class="sxs-lookup"><span data-stu-id="f94c2-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="f94c2-108">[in]コードのアドレス。</span><span class="sxs-lookup"><span data-stu-id="f94c2-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="f94c2-109">[in]このメソッドの実装フラグ。</span><span class="sxs-lookup"><span data-stu-id="f94c2-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f94c2-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="f94c2-110">Requirements</span></span>  
 <span data-ttu-id="f94c2-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f94c2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f94c2-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f94c2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f94c2-113">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="f94c2-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f94c2-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f94c2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f94c2-115">参照</span><span class="sxs-lookup"><span data-stu-id="f94c2-115">See Also</span></span>  
 [<span data-ttu-id="f94c2-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f94c2-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f94c2-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f94c2-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
