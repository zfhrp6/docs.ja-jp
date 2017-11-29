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
ms.openlocfilehash: 3798c4fc451b78257373c0ac47a5e7e7c27dd048
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="311af-102">ICLRRuntimeHost::Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="311af-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="311af-103">共通言語ランタイム (CLR) でコードの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="311af-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="311af-104">このメソッドによって、ホストにリソースを解放されたり、アプリケーション ドメインのアンロードまたは、スレッドの破棄されたりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="311af-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="311af-105">これらのリソースを解放するプロセスを終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="311af-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="311af-106">構文</span><span class="sxs-lookup"><span data-stu-id="311af-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="311af-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="311af-107">Return Value</span></span>  
  
|<span data-ttu-id="311af-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="311af-108">HRESULT</span></span>|<span data-ttu-id="311af-109">説明</span><span class="sxs-lookup"><span data-stu-id="311af-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="311af-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="311af-110">S_OK</span></span>|<span data-ttu-id="311af-111">`Stop`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="311af-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="311af-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="311af-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="311af-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="311af-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="311af-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="311af-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="311af-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="311af-115">The call timed out.</span></span>|  
|<span data-ttu-id="311af-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="311af-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="311af-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="311af-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="311af-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="311af-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="311af-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="311af-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="311af-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="311af-120">E_FAIL</span></span>|<span data-ttu-id="311af-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="311af-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="311af-122">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="311af-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="311af-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="311af-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="311af-124">要件</span><span class="sxs-lookup"><span data-stu-id="311af-124">Requirements</span></span>  
 <span data-ttu-id="311af-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="311af-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="311af-126">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="311af-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="311af-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="311af-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="311af-128">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="311af-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="311af-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="311af-129">See Also</span></span>  
 [<span data-ttu-id="311af-130">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="311af-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
