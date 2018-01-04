---
title: "EPolicyAction 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EPolicyAction
api_location: mscoree.dll
api_type: COM
f1_keywords: EPolicyAction
helpviewer_keywords: EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5de55d46eead37962fad7d7c1c5bd1766e772fe8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="9ef2c-102">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="9ef2c-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="9ef2c-103">ホストが記載された操作を設定できますポリシー操作について説明します[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)とによって記述されたエラー [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-103">Describes the policy actions the host can set for operations described by [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) and failures described by [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ef2c-104">構文</span><span class="sxs-lookup"><span data-stu-id="9ef2c-104">Syntax</span></span>  
  
```  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a><span data-ttu-id="9ef2c-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="9ef2c-105">Members</span></span>  
  
|<span data-ttu-id="9ef2c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="9ef2c-106">Member</span></span>|<span data-ttu-id="9ef2c-107">説明</span><span class="sxs-lookup"><span data-stu-id="9ef2c-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="9ef2c-108">共通言語ランタイム (CLR) が、スレッドを適切に中止する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="9ef2c-109">正常な中止では、すべてを実行する試行`finally`ブロックする場合に、いずれかの`catch`ブロックおよび関連するスレッドの中止、ファイナライザーを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="9ef2c-110">CLR が無効な状態を入力する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="9ef2c-111">マネージ コードを実行して、影響を受けるプロセスでそれ以上し、スレッドは CLR に入るをブロックします。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="9ef2c-112">CLR がファイナライザーを実行して、クリーンアップ、およびログ記録操作など、プロセスの通常終了を試みる必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="9ef2c-113">CLR しないで終了すること、プロセス、すぐにファイナライザーを実行するか、クリーンアップ、およびログ記録操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="9ef2c-114">ただし、デバッガーに通知が送信されます。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-114">Nowever, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="9ef2c-115">アクションを実行しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="9ef2c-116">CLR が rude スレッドの中止を実行する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="9ef2c-117">のみ`catch`と`finally`でマークされたブロック<xref:System.EnterpriseServices.MustRunInClientContextAttribute>実行されます。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="9ef2c-118">CLR がファイナライザーを実行するか、操作のログ記録しないでプロセスを終了することを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="9ef2c-119">CLR がの rude アンロードを実行する必要がありますを指定、<xref:System.AppDomain>です。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="9ef2c-120">マークされた唯一のファイナライザー<xref:System.EnterpriseServices.MustRunInClientContextAttribute>実行されます。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="9ef2c-121">これと同様に、すべてのスレッド<xref:System.AppDomain>スタックに表示される、 `ThreadAbortException`、だけが`catch`と`finally`でマークされたブロック<xref:System.EnterpriseServices.MustRunInClientContextAttribute>実行されます。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="9ef2c-122">メモリ不足、バッファーのオーバーフローなどの条件に該当する例外をスローすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="9ef2c-123">指定する、<xref:System.AppDomain>がアンロードされます。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="9ef2c-124">CLR は、ファイナライザーを実行しようとします。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ef2c-125">コメント</span><span class="sxs-lookup"><span data-stu-id="9ef2c-125">Remarks</span></span>  
 <span data-ttu-id="9ef2c-126">ホストでは、ポリシーのアクションを設定のメソッドを呼び出すことによって、 [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="9ef2c-127">中止されて rude かつ安全な方法については、次を参照してください。、 [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-127">For information about rude and graceful aborts, see the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ef2c-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="9ef2c-128">Requirements</span></span>  
 <span data-ttu-id="9ef2c-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ef2c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ef2c-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ef2c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ef2c-131">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ef2c-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ef2c-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ef2c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ef2c-133">参照</span><span class="sxs-lookup"><span data-stu-id="9ef2c-133">See Also</span></span>  
 [<span data-ttu-id="9ef2c-134">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="9ef2c-134">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="9ef2c-135">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ef2c-135">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="9ef2c-136">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ef2c-136">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="9ef2c-137">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="9ef2c-137">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
