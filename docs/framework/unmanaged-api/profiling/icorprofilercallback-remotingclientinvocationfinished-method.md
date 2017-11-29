---
title: "ICorProfilerCallback::RemotingClientInvocationFinished メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingClientInvocationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 77f86d12d3a19f1b02ece35c8b717e78802f74f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="a1793-102">ICorProfilerCallback::RemotingClientInvocationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="a1793-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="a1793-103">クライアントで、リモート処理の呼び出しが完了するまで実行をプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a1793-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1793-104">構文</span><span class="sxs-lookup"><span data-stu-id="a1793-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a1793-105">コメント</span><span class="sxs-lookup"><span data-stu-id="a1793-105">Remarks</span></span>  
 <span data-ttu-id="a1793-106">リモート処理の呼び出しが同期すると場合に、も実行が完了、サーバーにします。</span><span class="sxs-lookup"><span data-stu-id="a1793-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="a1793-107">リモート処理の呼び出しが非同期で呼び出しを処理するとき、応答可能性があります予想されます。</span><span class="sxs-lookup"><span data-stu-id="a1793-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="a1793-108">呼び出しとして発生し、応答が予想される場合は[icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)と呼び出しを`RemotingClientInvocationFinished`を必要なセカンダリの処理の非同期呼び出しを示します。</span><span class="sxs-lookup"><span data-stu-id="a1793-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="a1793-109">同じスレッドでコールバックの組み合わせにより、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a1793-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   <span data-ttu-id="a1793-110">`RemotingClientInvocationStarted`および[icorprofilercallback::remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="a1793-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="a1793-111">[Icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)と[icorprofilercallback::remotingclientinvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="a1793-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="a1793-112">[Icorprofilercallback::remotingserverinvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)と[icorprofilercallback::remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="a1793-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="a1793-113">リモート処理のコールバックで次の問題に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1793-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="a1793-114">クライアントから呼び出され、サーバー上で実行される関数の通知が正しく受信されていないために、リモート処理関数の実行がプロファイラー API によって反映されません。</span><span class="sxs-lookup"><span data-stu-id="a1793-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="a1793-115">プロキシ オブジェクトによって行われ、実際の呼び出し、プロファイラーには、特定の関数は、JIT コンパイルしますが、使用されていないことが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a1793-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="a1793-116">プロファイラーは、非同期のリモート処理イベントの正確な通知を受信しません。</span><span class="sxs-lookup"><span data-stu-id="a1793-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1793-117">要件</span><span class="sxs-lookup"><span data-stu-id="a1793-117">Requirements</span></span>  
 <span data-ttu-id="a1793-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a1793-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1793-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1793-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1793-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1793-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1793-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1793-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1793-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1793-122">See Also</span></span>  
 [<span data-ttu-id="a1793-123">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1793-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
