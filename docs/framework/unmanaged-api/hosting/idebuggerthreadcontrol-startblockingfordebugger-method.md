---
title: "IDebuggerThreadControl::StartBlockingForDebugger メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl.StartBlockingForDebugger
api_location: mscoree.dll
api_type: COM
f1_keywords: StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0f7d49766c68c24441bf59d2d83958276def0143
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="a3058-102">IDebuggerThreadControl::StartBlockingForDebugger メソッド</span><span class="sxs-lookup"><span data-stu-id="a3058-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="a3058-103">デバッグ サービスがすべてのスレッドのブロックを開始しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="a3058-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3058-104">構文</span><span class="sxs-lookup"><span data-stu-id="a3058-104">Syntax</span></span>  
  
```  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3058-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a3058-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="a3058-106">[in]将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="a3058-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3058-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a3058-107">Remarks</span></span>  
 <span data-ttu-id="a3058-108">`StartBlockingForDebugger`ランタイム スレッドでメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a3058-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3058-109">要件</span><span class="sxs-lookup"><span data-stu-id="a3058-109">Requirements</span></span>  
 <span data-ttu-id="a3058-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a3058-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3058-111">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a3058-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3058-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a3058-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3058-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3058-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3058-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3058-114">See Also</span></span>  
 [<span data-ttu-id="a3058-115">IDebuggerThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a3058-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
