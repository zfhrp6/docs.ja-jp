---
title: ICorProfilerCallback::RemotingServerReceivingMessage メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1874b5bea465eb31bcaad2d912b90d35cfc711b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454107"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="1c8fb-102">ICorProfilerCallback::RemotingServerReceivingMessage メソッド</span><span class="sxs-lookup"><span data-stu-id="1c8fb-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="1c8fb-103">プロセスが、リモート メソッド呼び出しまたはアクティブ化要求を受信したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="1c8fb-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c8fb-104">構文</span><span class="sxs-lookup"><span data-stu-id="1c8fb-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c8fb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c8fb-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="1c8fb-106">[in]指定された値に対応する値[icorprofilercallback::remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)これらの条件下で。</span><span class="sxs-lookup"><span data-stu-id="1c8fb-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="1c8fb-107">リモート処理 GUID cookie はアクティブです。</span><span class="sxs-lookup"><span data-stu-id="1c8fb-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="1c8fb-108">チャネルは、メッセージの送信に成功します。</span><span class="sxs-lookup"><span data-stu-id="1c8fb-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="1c8fb-109">GUID の cookie は、クライアント側のプロセスでアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="1c8fb-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="1c8fb-110">これにより、論理呼び出し履歴の作成とリモート処理の呼び出しのペアを容易にします。</span><span class="sxs-lookup"><span data-stu-id="1c8fb-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="1c8fb-111">[in]値が`true`呼び出しの場合は、それ以外の非同期`false`です。</span><span class="sxs-lookup"><span data-stu-id="1c8fb-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c8fb-112">コメント</span><span class="sxs-lookup"><span data-stu-id="1c8fb-112">Remarks</span></span>  
 <span data-ttu-id="1c8fb-113">非同期メッセージ要求の場合は、任意のスレッドによって、要求を処理することができます。</span><span class="sxs-lookup"><span data-stu-id="1c8fb-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c8fb-114">要件</span><span class="sxs-lookup"><span data-stu-id="1c8fb-114">Requirements</span></span>  
 <span data-ttu-id="1c8fb-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1c8fb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c8fb-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c8fb-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c8fb-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c8fb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c8fb-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c8fb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c8fb-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c8fb-119">See Also</span></span>  
 [<span data-ttu-id="1c8fb-120">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1c8fb-120">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
