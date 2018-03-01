---
title: "IGCThreadControl::ThreadIsBlockingForSuspension メソッド"
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
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0cb7cfbab18334f1892c24225311160179920f81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="c9df2-102">IGCThreadControl::ThreadIsBlockingForSuspension メソッド</span><span class="sxs-lookup"><span data-stu-id="c9df2-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="c9df2-103">呼び出しを行っているスレッドがガベージ コレクションまたはその他の中断のためにブロックすることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="c9df2-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9df2-104">構文</span><span class="sxs-lookup"><span data-stu-id="c9df2-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="c9df2-105">コメント</span><span class="sxs-lookup"><span data-stu-id="c9df2-105">Remarks</span></span>  
 <span data-ttu-id="c9df2-106">内でホストを選択ことがあります、`ThreadIsBlockingForSuspension`コールバック スレッドのスケジュールを変更するかどうか。</span><span class="sxs-lookup"><span data-stu-id="c9df2-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9df2-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="c9df2-107">Requirements</span></span>  
 <span data-ttu-id="c9df2-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c9df2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9df2-109">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c9df2-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9df2-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="c9df2-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9df2-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9df2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9df2-112">参照</span><span class="sxs-lookup"><span data-stu-id="c9df2-112">See Also</span></span>  
 [<span data-ttu-id="c9df2-113">IGCThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c9df2-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
