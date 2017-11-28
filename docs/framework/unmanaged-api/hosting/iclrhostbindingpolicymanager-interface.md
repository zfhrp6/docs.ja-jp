---
title: "ICLRHostBindingPolicyManager インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostBindingPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostBindingPolicyManager
helpviewer_keywords: ICLRHostBindingPolicyManager interface [.NET Framework hosting]
ms.assetid: f9da168b-366b-4b2b-bdb9-330b6bad5a6b
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eed5a72cb9da95f79831784d2bb53a6d60f92988
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="7c8db-102">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c8db-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="7c8db-103">ホストを現在のバインディング ポリシーを評価し、指定したアセンブリのポリシーの変更を通信するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="7c8db-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c8db-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="7c8db-104">Methods</span></span>  
  
|<span data-ttu-id="7c8db-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7c8db-105">Method</span></span>|<span data-ttu-id="7c8db-106">説明</span><span class="sxs-lookup"><span data-stu-id="7c8db-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c8db-107">EvaluatePolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="7c8db-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="7c8db-108">ホストの代わりには、バインディング ポリシーを評価します。</span><span class="sxs-lookup"><span data-stu-id="7c8db-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="7c8db-109">ModifyApplicationPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="7c8db-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="7c8db-110">指定したアセンブリのバインディング ポリシーを変更し、新しいバージョンのポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="7c8db-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c8db-111">要件</span><span class="sxs-lookup"><span data-stu-id="7c8db-111">Requirements</span></span>  
 <span data-ttu-id="7c8db-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7c8db-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c8db-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7c8db-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c8db-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c8db-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c8db-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c8db-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c8db-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c8db-116">See Also</span></span>  
 [<span data-ttu-id="7c8db-117">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c8db-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="7c8db-118">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c8db-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="7c8db-119">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c8db-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
