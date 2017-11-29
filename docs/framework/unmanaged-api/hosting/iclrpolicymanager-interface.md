---
title: "ICLRPolicyManager インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager
helpviewer_keywords: ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f3dd904184b730a5b0f5b2dfcac4197e708544d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="78dc1-102">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78dc1-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="78dc1-103">ホスト ポリシーのエラーやタイムアウトが発生した場合に実行されるアクションを指定できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="78dc1-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78dc1-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="78dc1-104">Methods</span></span>  
  
|<span data-ttu-id="78dc1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="78dc1-105">Method</span></span>|<span data-ttu-id="78dc1-106">説明</span><span class="sxs-lookup"><span data-stu-id="78dc1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="78dc1-107">SetActionOnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="78dc1-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="78dc1-108">指定したエラーが発生したときに、共通言語ランタイム (CLR) が実行するポリシー アクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="78dc1-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="78dc1-109">SetActionOnTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="78dc1-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="78dc1-110">CLR が、指定された操作がタイムアウトしたときに実行ポリシーのアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="78dc1-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="78dc1-111">SetDefaultAction メソッド</span><span class="sxs-lookup"><span data-stu-id="78dc1-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="78dc1-112">指定された操作が発生したときに CLR が実行ポリシーのアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="78dc1-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="78dc1-113">SetTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="78dc1-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="78dc1-114">指定された操作のタイムアウト値を設定します。</span><span class="sxs-lookup"><span data-stu-id="78dc1-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="78dc1-115">SetTimeoutAndAction メソッド</span><span class="sxs-lookup"><span data-stu-id="78dc1-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="78dc1-116">指定された操作のタイムアウト値を設定し、操作が発生したときに、CLR で実行する必要がありますポリシー操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="78dc1-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="78dc1-117">SetUnhandledExceptionPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="78dc1-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="78dc1-118">ハンドルされない例外が発生したときに、CLR の動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="78dc1-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78dc1-119">要件</span><span class="sxs-lookup"><span data-stu-id="78dc1-119">Requirements</span></span>  
 <span data-ttu-id="78dc1-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="78dc1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78dc1-121">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="78dc1-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78dc1-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="78dc1-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78dc1-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78dc1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78dc1-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="78dc1-124">See Also</span></span>  
 [<span data-ttu-id="78dc1-125">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="78dc1-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="78dc1-126">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="78dc1-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="78dc1-127">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="78dc1-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="78dc1-128">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78dc1-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
