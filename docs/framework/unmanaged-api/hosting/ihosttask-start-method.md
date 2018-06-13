---
title: IHostTask::Start メソッド
ms.date: 03/30/2017
api_name:
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1d931a7e0b6816841170b33ed6d17f05441d609
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441498"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="0e65c-102">IHostTask::Start メソッド</span><span class="sxs-lookup"><span data-stu-id="0e65c-102">IHostTask::Start Method</span></span>
<span data-ttu-id="0e65c-103">ホストが現在のタスクを移動要求[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)インスタンス、中断したからコードを実行できる状態にします。</span><span class="sxs-lookup"><span data-stu-id="0e65c-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e65c-104">構文</span><span class="sxs-lookup"><span data-stu-id="0e65c-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0e65c-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="0e65c-105">Return Value</span></span>  
  
|<span data-ttu-id="0e65c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e65c-106">HRESULT</span></span>|<span data-ttu-id="0e65c-107">説明</span><span class="sxs-lookup"><span data-stu-id="0e65c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e65c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e65c-108">S_OK</span></span>|<span data-ttu-id="0e65c-109">開始は正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="0e65c-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="0e65c-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0e65c-110">E_FAIL</span></span>|<span data-ttu-id="0e65c-111">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0e65c-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0e65c-112">メソッドには、E_FAIL が返される、ときに、共通言語ランタイム (CLR) は、プロセス内で使用可能ではありません。</span><span class="sxs-lookup"><span data-stu-id="0e65c-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="0e65c-113">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="0e65c-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e65c-114">コメント</span><span class="sxs-lookup"><span data-stu-id="0e65c-114">Remarks</span></span>  
 <span data-ttu-id="0e65c-115">`Start` 常にどこに致命的なエラーが発生した場合を除き、s_ok HRESULT 値を返します。</span><span class="sxs-lookup"><span data-stu-id="0e65c-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e65c-116">要件</span><span class="sxs-lookup"><span data-stu-id="0e65c-116">Requirements</span></span>  
 <span data-ttu-id="0e65c-117">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0e65c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e65c-118">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0e65c-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e65c-119">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0e65c-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e65c-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e65c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e65c-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e65c-121">See Also</span></span>  
 [<span data-ttu-id="0e65c-122">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e65c-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="0e65c-123">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e65c-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="0e65c-124">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e65c-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="0e65c-125">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e65c-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
