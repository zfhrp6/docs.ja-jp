---
title: ICLRHostBindingPolicyManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager
helpviewer_keywords:
- ICLRHostBindingPolicyManager interface [.NET Framework hosting]
ms.assetid: f9da168b-366b-4b2b-bdb9-330b6bad5a6b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 637803c509935fdff080802f66f9f73ab8cf25e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="9c6bc-102">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9c6bc-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="9c6bc-103">ホストを現在のバインディング ポリシーを評価し、指定したアセンブリのポリシーの変更を通信するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9c6bc-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9c6bc-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="9c6bc-104">Methods</span></span>  
  
|<span data-ttu-id="9c6bc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9c6bc-105">Method</span></span>|<span data-ttu-id="9c6bc-106">説明</span><span class="sxs-lookup"><span data-stu-id="9c6bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9c6bc-107">EvaluatePolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="9c6bc-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="9c6bc-108">ホストの代わりには、バインディング ポリシーを評価します。</span><span class="sxs-lookup"><span data-stu-id="9c6bc-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="9c6bc-109">ModifyApplicationPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="9c6bc-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="9c6bc-110">指定したアセンブリのバインディング ポリシーを変更し、新しいバージョンのポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="9c6bc-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9c6bc-111">要件</span><span class="sxs-lookup"><span data-stu-id="9c6bc-111">Requirements</span></span>  
 <span data-ttu-id="9c6bc-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9c6bc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c6bc-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9c6bc-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c6bc-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9c6bc-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c6bc-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c6bc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c6bc-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c6bc-116">See Also</span></span>  
 [<span data-ttu-id="9c6bc-117">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9c6bc-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="9c6bc-118">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9c6bc-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="9c6bc-119">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9c6bc-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
