---
title: "ICorRuntimeHost::Stop メソッド"
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
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f9e27bd5d05b10f8db24a1119e4ed3717ce044e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="9a044-102">ICorRuntimeHost::Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="9a044-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="9a044-103">現在のプロセスのランタイムでコードの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="9a044-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a044-104">構文</span><span class="sxs-lookup"><span data-stu-id="9a044-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9a044-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="9a044-105">Return Value</span></span>  
  
|<span data-ttu-id="9a044-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a044-106">HRESULT</span></span>|<span data-ttu-id="9a044-107">説明</span><span class="sxs-lookup"><span data-stu-id="9a044-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a044-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a044-108">S_OK</span></span>|<span data-ttu-id="9a044-109">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="9a044-109">The operation was successful.</span></span>|  
|<span data-ttu-id="9a044-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9a044-110">S_FALSE</span></span>|<span data-ttu-id="9a044-111">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="9a044-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="9a044-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9a044-112">E_FAIL</span></span>|<span data-ttu-id="9a044-113">未知の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9a044-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9a044-114">メソッドには、E_FAIL が返されます、共通言語ランタイム (CLR) は、プロセスで使用可能なできなくします。</span><span class="sxs-lookup"><span data-stu-id="9a044-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="9a044-115">Api をホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="9a044-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9a044-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9a044-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9a044-117">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="9a044-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a044-118">コメント</span><span class="sxs-lookup"><span data-stu-id="9a044-118">Remarks</span></span>  
 <span data-ttu-id="9a044-119">通常を呼び出す必要はありません、`Stop`メソッド、コードは、プロセスが終了したときに実行が停止されるためです。</span><span class="sxs-lookup"><span data-stu-id="9a044-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a044-120">呼び出しの後に`Stop`CLR は、同じプロセスに再初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="9a044-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a044-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="9a044-121">Requirements</span></span>  
 <span data-ttu-id="9a044-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9a044-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a044-123">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a044-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a044-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9a044-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a044-125">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="9a044-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a044-126">参照</span><span class="sxs-lookup"><span data-stu-id="9a044-126">See Also</span></span>  
 [<span data-ttu-id="9a044-127">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a044-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
