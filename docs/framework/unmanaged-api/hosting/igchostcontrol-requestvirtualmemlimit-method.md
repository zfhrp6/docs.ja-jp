---
title: IGCHostControl::RequestVirtualMemLimit メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2df33e3edebbf558bf78986e737c4f7bb9b2f0f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437158"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="f60bf-102">IGCHostControl::RequestVirtualMemLimit メソッド</span><span class="sxs-lookup"><span data-stu-id="f60bf-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="f60bf-103">仮想メモリの制限を変更するホストを要求します。</span><span class="sxs-lookup"><span data-stu-id="f60bf-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f60bf-104">構文</span><span class="sxs-lookup"><span data-stu-id="f60bf-104">Syntax</span></span>  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f60bf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f60bf-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="f60bf-106">[in]割り当てられるメモリの要求されたサイズ。</span><span class="sxs-lookup"><span data-stu-id="f60bf-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="f60bf-107">[入力、出力].割り当てられたメモリの実際のサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f60bf-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f60bf-108">要件</span><span class="sxs-lookup"><span data-stu-id="f60bf-108">Requirements</span></span>  
 <span data-ttu-id="f60bf-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f60bf-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f60bf-110">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f60bf-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f60bf-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="f60bf-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f60bf-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f60bf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f60bf-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f60bf-113">See Also</span></span>  
 [<span data-ttu-id="f60bf-114">IGCHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f60bf-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
