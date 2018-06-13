---
title: IDebuggerThreadControl::StartBlockingForDebugger メソッド
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.StartBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48aa7452373f83465b3e5ec8a09a9a00c902a22c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437935"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="d694c-102">IDebuggerThreadControl::StartBlockingForDebugger メソッド</span><span class="sxs-lookup"><span data-stu-id="d694c-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="d694c-103">デバッグ サービスがすべてのスレッドのブロックを開始しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="d694c-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d694c-104">構文</span><span class="sxs-lookup"><span data-stu-id="d694c-104">Syntax</span></span>  
  
```  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d694c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d694c-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="d694c-106">[in]将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="d694c-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d694c-107">コメント</span><span class="sxs-lookup"><span data-stu-id="d694c-107">Remarks</span></span>  
 <span data-ttu-id="d694c-108">`StartBlockingForDebugger`ランタイム スレッドでメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d694c-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d694c-109">要件</span><span class="sxs-lookup"><span data-stu-id="d694c-109">Requirements</span></span>  
 <span data-ttu-id="d694c-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d694c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d694c-111">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d694c-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d694c-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d694c-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d694c-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d694c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d694c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d694c-114">See Also</span></span>  
 [<span data-ttu-id="d694c-115">IDebuggerThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d694c-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
