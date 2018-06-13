---
title: ICLRPolicyManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e8a1b1bcf4470f5e754775b1137b8221ae1d0b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435148"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="ec30f-102">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec30f-102">ICLRPolicyManager Interface</span></span>
<span data-ttu-id="ec30f-103">ホスト ポリシーのエラーやタイムアウトが発生した場合に実行されるアクションを指定できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ec30f-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec30f-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="ec30f-104">Methods</span></span>  
  
|<span data-ttu-id="ec30f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ec30f-105">Method</span></span>|<span data-ttu-id="ec30f-106">説明</span><span class="sxs-lookup"><span data-stu-id="ec30f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec30f-107">SetActionOnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="ec30f-107">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="ec30f-108">指定したエラーが発生したときに、共通言語ランタイム (CLR) が実行するポリシー アクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="ec30f-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="ec30f-109">SetActionOnTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="ec30f-109">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="ec30f-110">CLR が、指定された操作がタイムアウトしたときに実行ポリシーのアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="ec30f-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="ec30f-111">SetDefaultAction メソッド</span><span class="sxs-lookup"><span data-stu-id="ec30f-111">SetDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="ec30f-112">指定された操作が発生したときに CLR が実行ポリシーのアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="ec30f-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="ec30f-113">SetTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="ec30f-113">SetTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="ec30f-114">指定された操作のタイムアウト値を設定します。</span><span class="sxs-lookup"><span data-stu-id="ec30f-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="ec30f-115">SetTimeoutAndAction メソッド</span><span class="sxs-lookup"><span data-stu-id="ec30f-115">SetTimeoutAndAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="ec30f-116">指定された操作のタイムアウト値を設定し、操作が発生したときに、CLR で実行する必要がありますポリシー操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="ec30f-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="ec30f-117">SetUnhandledExceptionPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="ec30f-117">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="ec30f-118">ハンドルされない例外が発生したときに、CLR の動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="ec30f-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec30f-119">要件</span><span class="sxs-lookup"><span data-stu-id="ec30f-119">Requirements</span></span>  
 <span data-ttu-id="ec30f-120">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ec30f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec30f-121">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ec30f-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec30f-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec30f-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec30f-123">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec30f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec30f-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec30f-124">See Also</span></span>  
 [<span data-ttu-id="ec30f-125">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="ec30f-125">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="ec30f-126">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="ec30f-126">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="ec30f-127">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="ec30f-127">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="ec30f-128">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec30f-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
