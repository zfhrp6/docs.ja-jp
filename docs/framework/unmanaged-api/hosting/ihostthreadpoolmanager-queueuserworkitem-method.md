---
title: "IHostThreadPoolManager::QueueUserWorkItem メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.QueueUserWorkItem
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9948673d6988de21c83c37538fb4d7c030296e58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="9f018-102">IHostThreadPoolManager::QueueUserWorkItem メソッド</span><span class="sxs-lookup"><span data-stu-id="9f018-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>
<span data-ttu-id="9f018-103">関数の実行をキューに配置し、その関数によって使用されるデータを格納しているオブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="9f018-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="9f018-104">この関数は、スレッドが利用可能になったら実行します。</span><span class="sxs-lookup"><span data-stu-id="9f018-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f018-105">構文</span><span class="sxs-lookup"><span data-stu-id="9f018-105">Syntax</span></span>  
  
```  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f018-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f018-106">Parameters</span></span>  
 `Function`  
 <span data-ttu-id="9f018-107">[in]実行する関数を表す関数のポインター。</span><span class="sxs-lookup"><span data-stu-id="9f018-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="9f018-108">[in]によって使用されるデータを格納しているオブジェクト`Function`です。</span><span class="sxs-lookup"><span data-stu-id="9f018-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="9f018-109">[in]フラグのいずれかの値は、win32 定義されている`QueueUserWorkItem`実行を制御する方法です。</span><span class="sxs-lookup"><span data-stu-id="9f018-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f018-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="9f018-110">Return Value</span></span>  
  
|<span data-ttu-id="9f018-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9f018-111">HRESULT</span></span>|<span data-ttu-id="9f018-112">説明</span><span class="sxs-lookup"><span data-stu-id="9f018-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9f018-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9f018-113">S_OK</span></span>|<span data-ttu-id="9f018-114">`QueueUserWorkItem`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="9f018-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="9f018-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9f018-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9f018-116">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="9f018-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9f018-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9f018-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9f018-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="9f018-118">The call timed out.</span></span>|  
|<span data-ttu-id="9f018-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9f018-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9f018-120">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="9f018-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9f018-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9f018-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9f018-122">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="9f018-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9f018-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9f018-123">E_FAIL</span></span>|<span data-ttu-id="9f018-124">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9f018-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9f018-125">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="9f018-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9f018-126">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="9f018-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f018-127">コメント</span><span class="sxs-lookup"><span data-stu-id="9f018-127">Remarks</span></span>  
 <span data-ttu-id="9f018-128">`QueueUserWorkItem`スレッド プールでワーカー スレッドに作業項目キューに入れます。</span><span class="sxs-lookup"><span data-stu-id="9f018-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="9f018-129">その署名およびパラメーターの型は、対応する Win32 関数の同じ名前を持つものと同じです。</span><span class="sxs-lookup"><span data-stu-id="9f018-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="9f018-130">詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f018-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f018-131">要件</span><span class="sxs-lookup"><span data-stu-id="9f018-131">Requirements</span></span>  
 <span data-ttu-id="9f018-132">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9f018-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f018-133">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9f018-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9f018-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9f018-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f018-135">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f018-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f018-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f018-136">See Also</span></span>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="9f018-137">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f018-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
