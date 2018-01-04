---
title: "IActionOnCLREvent::OnEvent メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IActionOnCLREvent.OnEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfba70cb1e0daf230abd16af6e24b4671334f20d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="70c56-102">IActionOnCLREvent::OnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="70c56-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="70c56-103">呼び出しを使用して、登録されているイベントのコールバックを実行、 [iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="70c56-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70c56-104">構文</span><span class="sxs-lookup"><span data-stu-id="70c56-104">Syntax</span></span>  
  
```  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70c56-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="70c56-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="70c56-106">[in]1 つ、 [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)値で、イベントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="70c56-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="70c56-107">[in]に関する詳細情報を格納しているオブジェクトへのポインター`event`です。</span><span class="sxs-lookup"><span data-stu-id="70c56-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70c56-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="70c56-108">Return Value</span></span>  
  
|<span data-ttu-id="70c56-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="70c56-109">HRESULT</span></span>|<span data-ttu-id="70c56-110">説明</span><span class="sxs-lookup"><span data-stu-id="70c56-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="70c56-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="70c56-111">S_OK</span></span>|<span data-ttu-id="70c56-112">`OnEvent`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="70c56-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="70c56-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="70c56-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="70c56-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="70c56-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="70c56-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="70c56-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="70c56-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="70c56-116">The call timed out.</span></span>|  
|<span data-ttu-id="70c56-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="70c56-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="70c56-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="70c56-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="70c56-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="70c56-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="70c56-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="70c56-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="70c56-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="70c56-121">E_FAIL</span></span>|<span data-ttu-id="70c56-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="70c56-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="70c56-123">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="70c56-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="70c56-124">任意のホスト メソッドに後続の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="70c56-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70c56-125">コメント</span><span class="sxs-lookup"><span data-stu-id="70c56-125">Remarks</span></span>  
 <span data-ttu-id="70c56-126">`data`パラメーターが指定されていない型のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="70c56-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="70c56-127">場合、`event`パラメーターは`Event_DomainUnload`、`data`の数値識別子を指定、<xref:System.AppDomain>アンロードされました。</span><span class="sxs-lookup"><span data-stu-id="70c56-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="70c56-128">ホストには、キーとしてこの識別子を使用して適切な操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="70c56-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="70c56-129">場合`event`は`Event_MDAFired`、`data`へのポインター、 [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)メッセージ出力から、マネージ デバッグ アシスタント (MDA) が格納されているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="70c56-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="70c56-130">Mda は、開発者によるをトラップするが困難な場合はイベントに関する XML メッセージを生成することによって、デバッグを支援する CLR の機能です。</span><span class="sxs-lookup"><span data-stu-id="70c56-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="70c56-131">このようなメッセージは、マネージとアンマネージ コード間の遷移のデバッグに特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="70c56-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="70c56-132">詳細については、次を参照してください。[マネージ デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)です。</span><span class="sxs-lookup"><span data-stu-id="70c56-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70c56-133">必要条件</span><span class="sxs-lookup"><span data-stu-id="70c56-133">Requirements</span></span>  
 <span data-ttu-id="70c56-134">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="70c56-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70c56-135">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="70c56-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70c56-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="70c56-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70c56-137">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70c56-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70c56-138">参照</span><span class="sxs-lookup"><span data-stu-id="70c56-138">See Also</span></span>  
 [<span data-ttu-id="70c56-139">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="70c56-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="70c56-140">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="70c56-140">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="70c56-141">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="70c56-141">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="70c56-142">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="70c56-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="70c56-143">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="70c56-143">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="70c56-144">MDAInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="70c56-144">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
