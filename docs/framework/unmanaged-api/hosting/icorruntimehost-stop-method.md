---
title: "ICorRuntimeHost::Stop メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.Stop
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f6bf66065293107efae7f401a584b7342f29125
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="042ba-102">ICorRuntimeHost::Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="042ba-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="042ba-103">現在のプロセスのランタイムでコードの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="042ba-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="042ba-104">構文</span><span class="sxs-lookup"><span data-stu-id="042ba-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="042ba-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="042ba-105">Return Value</span></span>  
  
|<span data-ttu-id="042ba-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="042ba-106">HRESULT</span></span>|<span data-ttu-id="042ba-107">説明</span><span class="sxs-lookup"><span data-stu-id="042ba-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="042ba-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="042ba-108">S_OK</span></span>|<span data-ttu-id="042ba-109">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="042ba-109">The operation was successful.</span></span>|  
|<span data-ttu-id="042ba-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="042ba-110">S_FALSE</span></span>|<span data-ttu-id="042ba-111">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="042ba-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="042ba-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="042ba-112">E_FAIL</span></span>|<span data-ttu-id="042ba-113">未知の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="042ba-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="042ba-114">メソッドには、E_FAIL が返されます、共通言語ランタイム (CLR) は、プロセスで使用可能なできなくします。</span><span class="sxs-lookup"><span data-stu-id="042ba-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="042ba-115">Api をホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="042ba-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="042ba-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="042ba-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="042ba-117">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="042ba-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="042ba-118">コメント</span><span class="sxs-lookup"><span data-stu-id="042ba-118">Remarks</span></span>  
 <span data-ttu-id="042ba-119">通常を呼び出す必要はありません、`Stop`メソッド、コードは、プロセスが終了したときに実行が停止されるためです。</span><span class="sxs-lookup"><span data-stu-id="042ba-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="042ba-120">呼び出しの後に`Stop`CLR は、同じプロセスに再初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="042ba-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="042ba-121">要件</span><span class="sxs-lookup"><span data-stu-id="042ba-121">Requirements</span></span>  
 <span data-ttu-id="042ba-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="042ba-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="042ba-123">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="042ba-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="042ba-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="042ba-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="042ba-125">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="042ba-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="042ba-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="042ba-126">See Also</span></span>  
 [<span data-ttu-id="042ba-127">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="042ba-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
