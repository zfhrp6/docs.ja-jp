---
title: "ICLRRuntimeHost::Stop メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.Stop
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cb9eaecdec661ae56727e5fd38c7e9a3b9621d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="5c6ce-102">ICLRRuntimeHost::Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="5c6ce-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="5c6ce-103">共通言語ランタイム (CLR) でコードの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="5c6ce-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5c6ce-104">このメソッドによって、ホストにリソースを解放されたり、アプリケーション ドメインのアンロードまたは、スレッドの破棄されたりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5c6ce-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="5c6ce-105">これらのリソースを解放するプロセスを終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c6ce-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c6ce-106">構文</span><span class="sxs-lookup"><span data-stu-id="5c6ce-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5c6ce-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="5c6ce-107">Return Value</span></span>  
  
|<span data-ttu-id="5c6ce-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c6ce-108">HRESULT</span></span>|<span data-ttu-id="5c6ce-109">説明</span><span class="sxs-lookup"><span data-stu-id="5c6ce-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c6ce-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c6ce-110">S_OK</span></span>|<span data-ttu-id="5c6ce-111">`Stop`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="5c6ce-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="5c6ce-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c6ce-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c6ce-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="5c6ce-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c6ce-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c6ce-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c6ce-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="5c6ce-115">The call timed out.</span></span>|  
|<span data-ttu-id="5c6ce-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c6ce-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c6ce-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="5c6ce-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c6ce-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c6ce-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c6ce-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="5c6ce-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c6ce-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c6ce-120">E_FAIL</span></span>|<span data-ttu-id="5c6ce-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5c6ce-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c6ce-122">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="5c6ce-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c6ce-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="5c6ce-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5c6ce-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="5c6ce-124">Requirements</span></span>  
 <span data-ttu-id="5c6ce-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c6ce-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c6ce-126">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c6ce-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c6ce-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5c6ce-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c6ce-128">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c6ce-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c6ce-129">参照</span><span class="sxs-lookup"><span data-stu-id="5c6ce-129">See Also</span></span>  
 [<span data-ttu-id="5c6ce-130">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c6ce-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
