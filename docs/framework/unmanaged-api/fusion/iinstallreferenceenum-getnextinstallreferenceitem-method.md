---
title: "IInstallReferenceEnum::GetNextInstallReferenceItem メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IInstallReferenceEnum.GetNextInstallReferenceItem
api_location: fusion.dll
api_type: COM
f1_keywords: IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db7e8bfaf396293f89f4b2e2bb20b5f6f532db19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="56fc1-102">IInstallReferenceEnum::GetNextInstallReferenceItem メソッド</span><span class="sxs-lookup"><span data-stu-id="56fc1-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="56fc1-103">ポインターを取得[IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)これに含まれるオブジェクト[IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="56fc1-103">Gets a pointer to the next [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56fc1-104">構文</span><span class="sxs-lookup"><span data-stu-id="56fc1-104">Syntax</span></span>  
  
```  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56fc1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="56fc1-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="56fc1-106">[out]返された`IInstallReferenceItem`ポインター。</span><span class="sxs-lookup"><span data-stu-id="56fc1-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="56fc1-107">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="56fc1-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="56fc1-108">`dwFlags`0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="56fc1-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="56fc1-109">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="56fc1-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="56fc1-110">`pvReserved`null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="56fc1-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56fc1-111">要件</span><span class="sxs-lookup"><span data-stu-id="56fc1-111">Requirements</span></span>  
 <span data-ttu-id="56fc1-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="56fc1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56fc1-113">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="56fc1-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="56fc1-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56fc1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56fc1-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="56fc1-115">See Also</span></span>  
 [<span data-ttu-id="56fc1-116">IInstallReferenceItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56fc1-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [<span data-ttu-id="56fc1-117">IInstallReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56fc1-117">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
