---
title: "IDebuggerThreadControl::ThreadIsBlockingForDebugger メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location: mscoree.dll
api_type: COM
f1_keywords: ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5b14818f06fec78cfc2cff9ea66548c9ee87bb4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="b6378-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger メソッド</span><span class="sxs-lookup"><span data-stu-id="b6378-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="b6378-103">このコールバックを送信しているスレッドは、ホストに通知デバッグ サービス内でブロックします。</span><span class="sxs-lookup"><span data-stu-id="b6378-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6378-104">構文</span><span class="sxs-lookup"><span data-stu-id="b6378-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="b6378-105">コメント</span><span class="sxs-lookup"><span data-stu-id="b6378-105">Remarks</span></span>  
 <span data-ttu-id="b6378-106">`ThreadIsBlockingForDebugger`メソッドは常に、ランタイム スレッドで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b6378-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="b6378-107">`ThreadIsBlockingForDebugger`メソッドに、ホスト、スレッドはブロックの中に別の操作を実行する機会が与えられます。</span><span class="sxs-lookup"><span data-stu-id="b6378-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6378-108">要件</span><span class="sxs-lookup"><span data-stu-id="b6378-108">Requirements</span></span>  
 <span data-ttu-id="b6378-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6378-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6378-110">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b6378-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6378-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b6378-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6378-112">**NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6378-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6378-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6378-113">See Also</span></span>  
 [<span data-ttu-id="b6378-114">IDebuggerThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b6378-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
