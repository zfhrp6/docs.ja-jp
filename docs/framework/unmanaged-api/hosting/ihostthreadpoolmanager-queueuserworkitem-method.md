---
title: IHostThreadPoolManager::QueueUserWorkItem メソッド
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.QueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b458739db024bdbe8cf0fb5a12a5d5f508d332da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441722"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="29e02-102">IHostThreadPoolManager::QueueUserWorkItem メソッド</span><span class="sxs-lookup"><span data-stu-id="29e02-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>
<span data-ttu-id="29e02-103">関数の実行をキューに配置し、その関数によって使用されるデータを格納しているオブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="29e02-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="29e02-104">この関数は、スレッドが利用可能になったら実行します。</span><span class="sxs-lookup"><span data-stu-id="29e02-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29e02-105">構文</span><span class="sxs-lookup"><span data-stu-id="29e02-105">Syntax</span></span>  
  
```  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29e02-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="29e02-106">Parameters</span></span>  
 `Function`  
 <span data-ttu-id="29e02-107">[in]実行する関数を表す関数のポインター。</span><span class="sxs-lookup"><span data-stu-id="29e02-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="29e02-108">[in]によって使用されるデータを格納しているオブジェクト`Function`です。</span><span class="sxs-lookup"><span data-stu-id="29e02-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="29e02-109">[in]フラグのいずれかの値は、win32 定義されている`QueueUserWorkItem`実行を制御する方法です。</span><span class="sxs-lookup"><span data-stu-id="29e02-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29e02-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="29e02-110">Return Value</span></span>  
  
|<span data-ttu-id="29e02-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29e02-111">HRESULT</span></span>|<span data-ttu-id="29e02-112">説明</span><span class="sxs-lookup"><span data-stu-id="29e02-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29e02-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="29e02-113">S_OK</span></span>|<span data-ttu-id="29e02-114">`QueueUserWorkItem` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="29e02-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="29e02-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="29e02-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="29e02-116">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="29e02-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="29e02-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="29e02-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="29e02-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="29e02-118">The call timed out.</span></span>|  
|<span data-ttu-id="29e02-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="29e02-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="29e02-120">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="29e02-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="29e02-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="29e02-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="29e02-122">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="29e02-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="29e02-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="29e02-123">E_FAIL</span></span>|<span data-ttu-id="29e02-124">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="29e02-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="29e02-125">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="29e02-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="29e02-126">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="29e02-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29e02-127">コメント</span><span class="sxs-lookup"><span data-stu-id="29e02-127">Remarks</span></span>  
 <span data-ttu-id="29e02-128">`QueueUserWorkItem` スレッド プールでワーカー スレッドに作業項目キューに入れます。</span><span class="sxs-lookup"><span data-stu-id="29e02-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="29e02-129">その署名およびパラメーターの型は、対応する Win32 関数の同じ名前を持つものと同じです。</span><span class="sxs-lookup"><span data-stu-id="29e02-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="29e02-130">詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="29e02-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29e02-131">要件</span><span class="sxs-lookup"><span data-stu-id="29e02-131">Requirements</span></span>  
 <span data-ttu-id="29e02-132">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="29e02-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29e02-133">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="29e02-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29e02-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="29e02-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29e02-135">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29e02-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29e02-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="29e02-136">See Also</span></span>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="29e02-137">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29e02-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
