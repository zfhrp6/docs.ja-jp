---
title: "ICorPublishProcess::EnumAppDomains メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.EnumAppDomains
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 938c022788d5ed9f0e28f794432017748dc096e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="3233d-102">ICorPublishProcess::EnumAppDomains メソッド</span><span class="sxs-lookup"><span data-stu-id="3233d-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="3233d-103">これによって参照されているプロセスのアプリケーション ドメインの列挙子を取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="3233d-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3233d-104">構文</span><span class="sxs-lookup"><span data-stu-id="3233d-104">Syntax</span></span>  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3233d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3233d-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="3233d-106">[out]アドレスへのポインター、 [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)により、このプロセスでのアプリケーション ドメインのコレクションを反復処理するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="3233d-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3233d-107">コメント</span><span class="sxs-lookup"><span data-stu-id="3233d-107">Remarks</span></span>  
 <span data-ttu-id="3233d-108">アプリケーション ドメインの一覧が存在するアプリケーション ドメインのスナップショットに基づいたときに、`EnumAppDomains`メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3233d-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="3233d-109">このメソッドは、最新の一覧を作成する複数回呼び出すことがあります。</span><span class="sxs-lookup"><span data-stu-id="3233d-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="3233d-110">このメソッドの後続の呼び出しは既存のリストを受けません。</span><span class="sxs-lookup"><span data-stu-id="3233d-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="3233d-111">プロセスが終了した場合`EnumAppDomains`CORDBG_E_PROCESS_TERMINATED HRESULT 値を持つは失敗します。</span><span class="sxs-lookup"><span data-stu-id="3233d-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3233d-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="3233d-112">Requirements</span></span>  
 <span data-ttu-id="3233d-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3233d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3233d-114">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="3233d-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3233d-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3233d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3233d-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3233d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3233d-117">参照</span><span class="sxs-lookup"><span data-stu-id="3233d-117">See Also</span></span>  
 [<span data-ttu-id="3233d-118">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3233d-118">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
