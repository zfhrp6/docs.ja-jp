---
title: "IGCHostControl::RequestVirtualMemLimit メソッド"
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
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a14cb0d2d34db4ea0e5f9abf6fba6efc5e5a950c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="69a5d-102">IGCHostControl::RequestVirtualMemLimit メソッド</span><span class="sxs-lookup"><span data-stu-id="69a5d-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="69a5d-103">仮想メモリの制限を変更するホストを要求します。</span><span class="sxs-lookup"><span data-stu-id="69a5d-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69a5d-104">構文</span><span class="sxs-lookup"><span data-stu-id="69a5d-104">Syntax</span></span>  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69a5d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="69a5d-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="69a5d-106">[in]割り当てられるメモリの要求されたサイズ。</span><span class="sxs-lookup"><span data-stu-id="69a5d-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="69a5d-107">[入力、出力].割り当てられたメモリの実際のサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="69a5d-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69a5d-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="69a5d-108">Requirements</span></span>  
 <span data-ttu-id="69a5d-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="69a5d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69a5d-110">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="69a5d-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="69a5d-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="69a5d-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69a5d-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69a5d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69a5d-113">参照</span><span class="sxs-lookup"><span data-stu-id="69a5d-113">See Also</span></span>  
 [<span data-ttu-id="69a5d-114">IGCHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69a5d-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
