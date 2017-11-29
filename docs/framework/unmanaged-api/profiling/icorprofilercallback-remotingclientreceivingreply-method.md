---
title: "ICorProfilerCallback::RemotingClientReceivingReply メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingClientReceivingReply
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f1dd027dc113abfceeb88abbc82c69ed395584e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="b418f-102">ICorProfilerCallback::RemotingClientReceivingReply メソッド</span><span class="sxs-lookup"><span data-stu-id="b418f-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="b418f-103">サーバー側のリモート処理の呼び出しが完了し、クライアントが受け取るようになりましたことをプロファイラーに通知応答を処理しようとします。</span><span class="sxs-lookup"><span data-stu-id="b418f-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b418f-104">構文</span><span class="sxs-lookup"><span data-stu-id="b418f-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="b418f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b418f-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="b418f-106">[in]指定された値に対応する値[icorprofilercallback::remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)これらの条件下で。</span><span class="sxs-lookup"><span data-stu-id="b418f-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="b418f-107">リモート処理 GUID cookie はアクティブです。</span><span class="sxs-lookup"><span data-stu-id="b418f-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="b418f-108">チャネルは、メッセージの送信に成功します。</span><span class="sxs-lookup"><span data-stu-id="b418f-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="b418f-109">GUID の cookie は、サーバー側のプロセスでアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="b418f-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="b418f-110">これにより、リモート呼び出しのペアを容易にします。</span><span class="sxs-lookup"><span data-stu-id="b418f-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="b418f-111">[in]値が`true`呼び出しの場合は、それ以外の非同期`false`です。</span><span class="sxs-lookup"><span data-stu-id="b418f-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b418f-112">要件</span><span class="sxs-lookup"><span data-stu-id="b418f-112">Requirements</span></span>  
 <span data-ttu-id="b418f-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b418f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b418f-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b418f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b418f-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b418f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b418f-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b418f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b418f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b418f-117">See Also</span></span>  
 [<span data-ttu-id="b418f-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b418f-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
