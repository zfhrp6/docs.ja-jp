---
title: "IInstallReferenceItem::GetReference メソッド"
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
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: de21e9b0d224ec417eeb50f8de5c33411d0dadb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="caa12-102">IInstallReferenceItem::GetReference メソッド</span><span class="sxs-lookup"><span data-stu-id="caa12-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="caa12-103">ポインターを取得、 [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)これによって表される構造体[IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="caa12-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caa12-104">構文</span><span class="sxs-lookup"><span data-stu-id="caa12-104">Syntax</span></span>  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="caa12-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="caa12-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="caa12-106">[out]返された`FUSION_INSTALL_REFERENCE`ポインター。</span><span class="sxs-lookup"><span data-stu-id="caa12-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="caa12-107">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="caa12-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="caa12-108">`dwFlags`0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="caa12-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="caa12-109">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="caa12-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="caa12-110">`pvReserved`null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="caa12-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caa12-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="caa12-111">Requirements</span></span>  
 <span data-ttu-id="caa12-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="caa12-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caa12-113">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="caa12-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="caa12-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caa12-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa12-115">参照</span><span class="sxs-lookup"><span data-stu-id="caa12-115">See Also</span></span>  
 [<span data-ttu-id="caa12-116">IInstallReferenceItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="caa12-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [<span data-ttu-id="caa12-117">FUSION_INSTALL_REFERENCE 構造体</span><span class="sxs-lookup"><span data-stu-id="caa12-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
