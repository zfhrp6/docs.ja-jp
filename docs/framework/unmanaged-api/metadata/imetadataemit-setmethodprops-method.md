---
title: IMetaDataEmit::SetMethodProps メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ef6771ec3f458c20701cc330a5730367b3c5b89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445927"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="a9a31-102">IMetaDataEmit::SetMethodProps メソッド</span><span class="sxs-lookup"><span data-stu-id="a9a31-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="a9a31-103">設定または、指定の相対仮想アドレス、前回の呼び出しによって定義されたメソッドに格納されている、この機能を更新[imetadataemit::definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="a9a31-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9a31-104">構文</span><span class="sxs-lookup"><span data-stu-id="a9a31-104">Syntax</span></span>  
  
```  
HRESULT SetMethodProps (   
    [in]  mdMethodDef md,   
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,   
    [in]  DWORD       dwImplFlags   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9a31-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a9a31-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="a9a31-106">[in]変更するメソッドのトークン。</span><span class="sxs-lookup"><span data-stu-id="a9a31-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="a9a31-107">[in]メンバーの属性です。</span><span class="sxs-lookup"><span data-stu-id="a9a31-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="a9a31-108">[in]コードのアドレス。</span><span class="sxs-lookup"><span data-stu-id="a9a31-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="a9a31-109">[in]このメソッドの実装フラグ。</span><span class="sxs-lookup"><span data-stu-id="a9a31-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9a31-110">要件</span><span class="sxs-lookup"><span data-stu-id="a9a31-110">Requirements</span></span>  
 <span data-ttu-id="a9a31-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a9a31-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9a31-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a9a31-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9a31-113">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="a9a31-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9a31-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9a31-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9a31-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9a31-115">See Also</span></span>  
 [<span data-ttu-id="a9a31-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9a31-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a9a31-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9a31-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
