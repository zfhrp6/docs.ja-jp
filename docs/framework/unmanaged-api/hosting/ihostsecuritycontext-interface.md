---
title: "IHostSecurityContext インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8ee464e47ad6e333b507c199e1857309f640a37b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="a4a5e-102">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4a5e-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="a4a5e-103">により、共通言語ランタイム (CLR) にホストによって実装されているセキュリティ コンテキスト情報を維持できます。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a4a5e-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a4a5e-104">Methods</span></span>  
  
|<span data-ttu-id="a4a5e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a4a5e-105">Method</span></span>|<span data-ttu-id="a4a5e-106">説明</span><span class="sxs-lookup"><span data-stu-id="a4a5e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a4a5e-107">Capture メソッド</span><span class="sxs-lookup"><span data-stu-id="a4a5e-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="a4a5e-108">複製を取得、`IHostSecurityContext`への呼び出しから返されるインスタンス[ihostsecuritymanager::getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4a5e-109">コメント</span><span class="sxs-lookup"><span data-stu-id="a4a5e-109">Remarks</span></span>  
 <span data-ttu-id="a4a5e-110">ホストは、CLR とユーザーの両方のコードでスレッド トークンへのすべてのコード アクセスを制御できます。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="a4a5e-111">ように、完全なセキュリティ コンテキスト情報は、非同期操作または制限付きのコード アクセス権を持つコード ポイントを越えて渡されます。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="a4a5e-112">`IHostSecurityContext`このセキュリティ コンテキストについては、ランタイムに対して非透過的であるをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="a4a5e-113">ランタイムを使用してこの情報をキャプチャする`Capture`、し、スレッド プールのワーカーのアイテムのディスパッチ、ファイナライザーの実行、およびモジュールとクラスのコンス トラクターの間で移動します。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4a5e-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="a4a5e-114">Requirements</span></span>  
 <span data-ttu-id="a4a5e-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4a5e-116">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a4a5e-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4a5e-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4a5e-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4a5e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a5e-119">参照</span><span class="sxs-lookup"><span data-stu-id="a4a5e-119">See Also</span></span>  
 [<span data-ttu-id="a4a5e-120">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4a5e-120">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="a4a5e-121">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4a5e-121">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="a4a5e-122">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4a5e-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
