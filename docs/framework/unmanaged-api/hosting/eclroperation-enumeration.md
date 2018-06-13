---
title: EClrOperation 列挙型
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b18c89cee0c3f5088a9978e448a0d61de1b9848
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434246"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="94175-102">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="94175-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="94175-103">一連のホストがポリシーのアクションを適用できる操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="94175-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94175-104">構文</span><span class="sxs-lookup"><span data-stu-id="94175-104">Syntax</span></span>  
  
```  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a><span data-ttu-id="94175-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="94175-105">Members</span></span>  
  
|<span data-ttu-id="94175-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="94175-106">Member</span></span>|<span data-ttu-id="94175-107">説明</span><span class="sxs-lookup"><span data-stu-id="94175-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="94175-108">ホストは、ときに実行されるポリシーのアクションを指定できます、<xref:System.AppDomain>正常でない (rude) 方式でモジュールはアンロードされます。</span><span class="sxs-lookup"><span data-stu-id="94175-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="94175-109">ホストは、ときに実行されるポリシーのアクションを指定できます、<xref:System.AppDomain>が読み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="94175-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="94175-110">ホストは、ファイナライザーを実行するときのポリシーのアクションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="94175-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="94175-111">ホストは、ポリシー、プロセスが終了したときに実行されるアクションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="94175-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="94175-112">ホストは、スレッドが中止されたときに実行されるポリシーのアクションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="94175-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="94175-113">ホストは、コードの重要な領域で rude スレッドの中断が発生したときに実行されるポリシーのアクションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="94175-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="94175-114">ホストは、重大でないコード領域で rude スレッドの中断が発生したときに実行されるポリシーのアクションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="94175-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94175-115">コメント</span><span class="sxs-lookup"><span data-stu-id="94175-115">Remarks</span></span>  
 <span data-ttu-id="94175-116">共通言語ランタイム (CLR) の信頼性インフラストラクチャは、中止とリソース内のコードとコードの重要ではない領域で発生した重要な領域の割り当てエラーを区別します。</span><span class="sxs-lookup"><span data-stu-id="94175-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="94175-117">この区別は、ホストのコードに障害が発生した場所に応じて異なるポリシーを設定できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="94175-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="94175-118">A*コードの重要な領域*は、CLR がそのタスクの中止またはリソースが現在のタスクだけに影響するために、要求を完了に失敗を保証できない領域。</span><span class="sxs-lookup"><span data-stu-id="94175-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="94175-119">たとえば、タスクは、ロックが保持していると、メモリ割り当て要求の発行時に失敗を示す HRESULT を受け取る場合、にないの安定性を確保するには、そのタスクを中止するだけでは不十分、<xref:System.AppDomain>であるため、<xref:System.AppDomain>他を含めることがありますタスクが同じロックを待機します。</span><span class="sxs-lookup"><span data-stu-id="94175-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="94175-120">現在を破棄する可能性がありますタスクがタスクのその他の応答を停止 (ハング) に無期限にします。</span><span class="sxs-lookup"><span data-stu-id="94175-120">To abandon the current task might cause those other tasks to stop responding (or hang) indefinitely.</span></span> <span data-ttu-id="94175-121">このような場合は、全体にアンロードする機能、ホストする必要があります。<xref:System.AppDomain>リスクの潜在的なが不安定になるのではなくです。</span><span class="sxs-lookup"><span data-stu-id="94175-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="94175-122">A*重大でないコード領域*、その一方で、CLR が、中断や障害の影響は、エラーが発生しているタスクのみれることを保証できる領域がします。</span><span class="sxs-lookup"><span data-stu-id="94175-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="94175-123">CLR も区別正常かつ非正常 (rude) 中止します。</span><span class="sxs-lookup"><span data-stu-id="94175-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="94175-124">一般に、正常または適切な中止は、あらゆる努力 rude 中止がこのような保証を行いません中にタスクを中止する前に、例外処理ルーチンで、ファイナライザーを実行します。</span><span class="sxs-lookup"><span data-stu-id="94175-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94175-125">要件</span><span class="sxs-lookup"><span data-stu-id="94175-125">Requirements</span></span>  
 <span data-ttu-id="94175-126">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="94175-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94175-127">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="94175-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94175-128">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="94175-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94175-129">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94175-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94175-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="94175-130">See Also</span></span>  
 [<span data-ttu-id="94175-131">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="94175-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="94175-132">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="94175-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="94175-133">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94175-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="94175-134">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94175-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="94175-135">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="94175-135">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
