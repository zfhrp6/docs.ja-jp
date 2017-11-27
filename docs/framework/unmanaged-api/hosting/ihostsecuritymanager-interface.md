---
title: "IHostSecurityManager インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager
helpviewer_keywords: IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2b3d67328dbf68491d319e55e63a9c3540cd1ee4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="b8798-102">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8798-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="b8798-103">アクセスと実行中のスレッドのセキュリティ コンテキストを制御できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b8798-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8798-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="b8798-104">Methods</span></span>  
  
|<span data-ttu-id="b8798-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b8798-105">Method</span></span>|<span data-ttu-id="b8798-106">説明</span><span class="sxs-lookup"><span data-stu-id="b8798-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8798-107">GetSecurityContext メソッド</span><span class="sxs-lookup"><span data-stu-id="b8798-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="b8798-108">要求された取得[IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)ホストからです。</span><span class="sxs-lookup"><span data-stu-id="b8798-108">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="b8798-109">ImpersonateLoggedOnUser メソッド</span><span class="sxs-lookup"><span data-stu-id="b8798-109">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="b8798-110">要求の現在のユーザー id の資格情報を使用してコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="b8798-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="b8798-111">OpenThreadToken メソッド</span><span class="sxs-lookup"><span data-stu-id="b8798-111">OpenThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="b8798-112">現在のスレッドに関連付けられている随意アクセス トークンを開きます。</span><span class="sxs-lookup"><span data-stu-id="b8798-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="b8798-113">RevertToSelf メソッド</span><span class="sxs-lookup"><span data-stu-id="b8798-113">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="b8798-114">現在のユーザー id の権限の借用を終了し、元のスレッド トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="b8798-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="b8798-115">SetSecurityContext メソッド</span><span class="sxs-lookup"><span data-stu-id="b8798-115">SetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="b8798-116">現在実行中のスレッドのセキュリティ コンテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="b8798-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="b8798-117">SetThreadToken メソッド</span><span class="sxs-lookup"><span data-stu-id="b8798-117">SetThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="b8798-118">現在実行中のスレッドのハンドルを設定します。</span><span class="sxs-lookup"><span data-stu-id="b8798-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8798-119">コメント</span><span class="sxs-lookup"><span data-stu-id="b8798-119">Remarks</span></span>  
 <span data-ttu-id="b8798-120">ホストは、共通言語ランタイム (CLR) とユーザー コードの両方でスレッド トークンへのすべてのコード アクセスを制御できます。</span><span class="sxs-lookup"><span data-stu-id="b8798-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="b8798-121">ように、完全なセキュリティ コンテキスト情報は、非同期操作または制限付きのコード アクセス権を持つコード ポイントを越えて渡されます。</span><span class="sxs-lookup"><span data-stu-id="b8798-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="b8798-122">`IHostSecurityContext`このが CLR に対して非透過的セキュリティ コンテキスト情報をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="b8798-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="b8798-123">CLR では、マネージ スレッドのコンテキストを内部的に処理します。</span><span class="sxs-lookup"><span data-stu-id="b8798-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="b8798-124">プロセスに固有のクエリを実行`IHostSecurityManager`次の状況で。</span><span class="sxs-lookup"><span data-stu-id="b8798-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
-   <span data-ttu-id="b8798-125">ファイナライザー スレッドでファイナライザーの実行中です。</span><span class="sxs-lookup"><span data-stu-id="b8798-125">On the finalizer thread, during finalizer execution.</span></span>  
  
-   <span data-ttu-id="b8798-126">実行中にクラスとモジュール コンス トラクター。</span><span class="sxs-lookup"><span data-stu-id="b8798-126">During class and module constructor execution.</span></span>  
  
-   <span data-ttu-id="b8798-127">呼び出しで、ワーカー スレッドで非同期の時点で、 [ihostthreadpoolmanager::queueuserworkitem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b8798-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
-   <span data-ttu-id="b8798-128">I/O 完了ポートの使用中です。</span><span class="sxs-lookup"><span data-stu-id="b8798-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8798-129">要件</span><span class="sxs-lookup"><span data-stu-id="b8798-129">Requirements</span></span>  
 <span data-ttu-id="b8798-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8798-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8798-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b8798-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b8798-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b8798-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8798-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8798-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8798-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8798-134">See Also</span></span>  
 [<span data-ttu-id="b8798-135">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8798-135">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="b8798-136">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8798-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
