---
title: "IMetaDataEmit::DefineMemberRef メソッド"
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
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 38c2c495bc88dadae2d71b1b3710f30998023516
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="f01b5-102">IMetaDataEmit::DefineMemberRef メソッド</span><span class="sxs-lookup"><span data-stu-id="f01b5-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="f01b5-103">現在のスコープ外にあるモジュールのメンバーへの参照を定義し、その参照定義トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="f01b5-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f01b5-104">構文</span><span class="sxs-lookup"><span data-stu-id="f01b5-104">Syntax</span></span>  
  
```  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f01b5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f01b5-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="f01b5-106">[in]メンバーがグローバルでない場合、対象メンバーのクラスまたはインターフェイスのトークンメンバーが、グローバルの場合、`mdModuleRef`その他のファイルのトークン。</span><span class="sxs-lookup"><span data-stu-id="f01b5-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="f01b5-107">[in]対象メンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="f01b5-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="f01b5-108">[in]対象メンバーのシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="f01b5-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="f01b5-109">[in]内のバイト数`pvSigBlob`です。</span><span class="sxs-lookup"><span data-stu-id="f01b5-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="f01b5-110">[out]`mdMemberRef`トークンが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f01b5-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f01b5-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="f01b5-111">Requirements</span></span>  
 <span data-ttu-id="f01b5-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f01b5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f01b5-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f01b5-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f01b5-114">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="f01b5-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f01b5-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f01b5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f01b5-116">参照</span><span class="sxs-lookup"><span data-stu-id="f01b5-116">See Also</span></span>  
 [<span data-ttu-id="f01b5-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f01b5-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f01b5-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f01b5-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
