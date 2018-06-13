---
title: IGCHost::Collect メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bce005a677dcb74c176a6dddfb2726f6b1fd0e8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436908"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="71318-102">IGCHost::Collect メソッド</span><span class="sxs-lookup"><span data-stu-id="71318-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="71318-103">現在のガベージ コレクションの状態に関係なく、特定のジェネレーションで発生するコレクションを強制的にします。</span><span class="sxs-lookup"><span data-stu-id="71318-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71318-104">構文</span><span class="sxs-lookup"><span data-stu-id="71318-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71318-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="71318-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="71318-106">[in]ガベージ コレクションを実行する生成します。</span><span class="sxs-lookup"><span data-stu-id="71318-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="71318-107">-1 の値は、すべてのジェネレーションのガベージ コレクションが施されますことを示します。</span><span class="sxs-lookup"><span data-stu-id="71318-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71318-108">要件</span><span class="sxs-lookup"><span data-stu-id="71318-108">Requirements</span></span>  
 <span data-ttu-id="71318-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="71318-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71318-110">**ヘッダー:** GCHost.idl、GCHost.h</span><span class="sxs-lookup"><span data-stu-id="71318-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="71318-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="71318-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71318-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71318-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71318-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="71318-113">See Also</span></span>  
 [<span data-ttu-id="71318-114">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71318-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
