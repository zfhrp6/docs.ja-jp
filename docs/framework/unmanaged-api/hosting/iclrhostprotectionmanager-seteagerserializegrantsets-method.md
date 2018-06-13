---
title: ICLRHostProtectionManager::SetEagerSerializeGrantSets メソッド
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9bddaa25ba83570389a9d70ac1a9f60357f533c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432223"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="eec5d-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets メソッド</span><span class="sxs-lookup"><span data-stu-id="eec5d-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="eec5d-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="eec5d-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eec5d-104">構文</span><span class="sxs-lookup"><span data-stu-id="eec5d-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="eec5d-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="eec5d-105">Return Value</span></span>  
  
|<span data-ttu-id="eec5d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eec5d-106">HRESULT</span></span>|<span data-ttu-id="eec5d-107">説明</span><span class="sxs-lookup"><span data-stu-id="eec5d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eec5d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="eec5d-108">S_OK</span></span>|<span data-ttu-id="eec5d-109">`SetEagerSerializeGrantSets` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="eec5d-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="eec5d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eec5d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eec5d-111">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="eec5d-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eec5d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eec5d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eec5d-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="eec5d-113">The call timed out.</span></span>|  
|<span data-ttu-id="eec5d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eec5d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eec5d-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="eec5d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eec5d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eec5d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eec5d-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="eec5d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eec5d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eec5d-118">E_FAIL</span></span>|<span data-ttu-id="eec5d-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="eec5d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eec5d-120">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="eec5d-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eec5d-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="eec5d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eec5d-122">要件</span><span class="sxs-lookup"><span data-stu-id="eec5d-122">Requirements</span></span>  
 <span data-ttu-id="eec5d-123">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="eec5d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eec5d-124">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eec5d-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eec5d-125">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="eec5d-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eec5d-126">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eec5d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eec5d-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="eec5d-127">See Also</span></span>  
 [<span data-ttu-id="eec5d-128">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eec5d-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="eec5d-129">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eec5d-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
