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
ms.workload: dotnet
ms.openlocfilehash: 831ce047f38f7f4a5c7a8b84efea423c482a418d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="46e0c-102">ICorProfilerCallback::RemotingClientReceivingReply メソッド</span><span class="sxs-lookup"><span data-stu-id="46e0c-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="46e0c-103">サーバー側のリモート処理の呼び出しが完了し、クライアントが受け取るようになりましたことをプロファイラーに通知応答を処理しようとします。</span><span class="sxs-lookup"><span data-stu-id="46e0c-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46e0c-104">構文</span><span class="sxs-lookup"><span data-stu-id="46e0c-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="46e0c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="46e0c-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="46e0c-106">[in]指定された値に対応する値[icorprofilercallback::remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)これらの条件下で。</span><span class="sxs-lookup"><span data-stu-id="46e0c-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="46e0c-107">リモート処理 GUID cookie はアクティブです。</span><span class="sxs-lookup"><span data-stu-id="46e0c-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="46e0c-108">チャネルは、メッセージの送信に成功します。</span><span class="sxs-lookup"><span data-stu-id="46e0c-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="46e0c-109">GUID の cookie は、サーバー側のプロセスでアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="46e0c-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="46e0c-110">これにより、リモート呼び出しのペアを容易にします。</span><span class="sxs-lookup"><span data-stu-id="46e0c-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="46e0c-111">[in]値が`true`呼び出しの場合は、それ以外の非同期`false`です。</span><span class="sxs-lookup"><span data-stu-id="46e0c-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46e0c-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="46e0c-112">Requirements</span></span>  
 <span data-ttu-id="46e0c-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="46e0c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46e0c-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="46e0c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46e0c-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46e0c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46e0c-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46e0c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46e0c-117">参照</span><span class="sxs-lookup"><span data-stu-id="46e0c-117">See Also</span></span>  
 [<span data-ttu-id="46e0c-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="46e0c-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
