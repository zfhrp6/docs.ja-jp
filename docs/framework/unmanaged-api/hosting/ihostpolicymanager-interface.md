---
title: IHostPolicyManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7247dddc2d3313948fe6f49fbaa1440b141c4cf3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440766"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="acb56-102">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="acb56-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="acb56-103">ホストの場合、共通言語ランタイム (CLR) を実行する操作の中止、タイムアウト、またはエラーを通知するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="acb56-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="acb56-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="acb56-104">Methods</span></span>  
  
|<span data-ttu-id="acb56-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="acb56-105">Method</span></span>|<span data-ttu-id="acb56-106">説明</span><span class="sxs-lookup"><span data-stu-id="acb56-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="acb56-107">OnDefaultAction メソッド</span><span class="sxs-lookup"><span data-stu-id="acb56-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="acb56-108">CLR がへの呼び出しで指定された既定のアクションを実行しようとしていますが、ホストに通知[iclrpolicymanager::setdefaultaction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)スレッドへの応答で中止または<xref:System.AppDomain>をアンロードします。</span><span class="sxs-lookup"><span data-stu-id="acb56-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="acb56-109">OnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="acb56-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="acb56-110">CLR がへの呼び出しで指定されたアクションを実行しようとしていますが、ホストに通知[iclrpolicymanager::setactiononfailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)リソース割り当てまたは解放の失敗に応答します。</span><span class="sxs-lookup"><span data-stu-id="acb56-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="acb56-111">OnTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="acb56-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="acb56-112">CLR がへの呼び出しで指定されたアクションを実行しようとしていますが、ホストに通知[iclrpolicymanager::setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)タイムアウトに応答します。</span><span class="sxs-lookup"><span data-stu-id="acb56-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="acb56-113">要件</span><span class="sxs-lookup"><span data-stu-id="acb56-113">Requirements</span></span>  
 <span data-ttu-id="acb56-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="acb56-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acb56-115">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="acb56-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="acb56-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="acb56-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="acb56-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acb56-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb56-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="acb56-118">See Also</span></span>  
 [<span data-ttu-id="acb56-119">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="acb56-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="acb56-120">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="acb56-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="acb56-121">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="acb56-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="acb56-122">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="acb56-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="acb56-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="acb56-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
