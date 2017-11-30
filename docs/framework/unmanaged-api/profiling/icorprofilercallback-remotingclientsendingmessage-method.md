---
title: "ICorProfilerCallback::RemotingClientSendingMessage メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingClientSendingMessage
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a77acb736cec02da6839335e981016469eeb42b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="1718b-102">ICorProfilerCallback::RemotingClientSendingMessage メソッド</span><span class="sxs-lookup"><span data-stu-id="1718b-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="1718b-103">クライアントがサーバーに要求を送信することをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="1718b-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1718b-104">構文</span><span class="sxs-lookup"><span data-stu-id="1718b-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1718b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1718b-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="1718b-106">[in]指定された値に対応する値[icorprofilercallback::remotingserverreceivingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)これらの条件下で。</span><span class="sxs-lookup"><span data-stu-id="1718b-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="1718b-107">リモート処理 GUID cookie はアクティブです。</span><span class="sxs-lookup"><span data-stu-id="1718b-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="1718b-108">チャネルは、メッセージの送信に成功します。</span><span class="sxs-lookup"><span data-stu-id="1718b-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="1718b-109">GUID の cookie は、サーバー側のプロセスでアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="1718b-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="1718b-110">これにより、論理呼び出し履歴の作成とリモート処理の呼び出しのペアを容易にします。</span><span class="sxs-lookup"><span data-stu-id="1718b-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="1718b-111">[in]値が`true`呼び出しの場合は、それ以外の非同期`false`です。</span><span class="sxs-lookup"><span data-stu-id="1718b-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1718b-112">要件</span><span class="sxs-lookup"><span data-stu-id="1718b-112">Requirements</span></span>  
 <span data-ttu-id="1718b-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1718b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1718b-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1718b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1718b-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1718b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1718b-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1718b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1718b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="1718b-117">See Also</span></span>  
 [<span data-ttu-id="1718b-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1718b-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
