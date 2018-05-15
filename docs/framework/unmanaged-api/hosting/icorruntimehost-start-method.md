---
title: ICorRuntimeHost::Start メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96e8d80e2dff88aa5a589f864278b4a4e9cc76ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="fac95-102">ICorRuntimeHost::Start メソッド</span><span class="sxs-lookup"><span data-stu-id="fac95-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="fac95-103">共通言語ランタイム (CLR) を開始します。</span><span class="sxs-lookup"><span data-stu-id="fac95-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fac95-104">構文</span><span class="sxs-lookup"><span data-stu-id="fac95-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fac95-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="fac95-105">Return Value</span></span>  
  
|<span data-ttu-id="fac95-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fac95-106">HRESULT</span></span>|<span data-ttu-id="fac95-107">説明</span><span class="sxs-lookup"><span data-stu-id="fac95-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fac95-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="fac95-108">S_OK</span></span>|<span data-ttu-id="fac95-109">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="fac95-109">The operation was successful.</span></span>|  
|<span data-ttu-id="fac95-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="fac95-110">S_FALSE</span></span>|<span data-ttu-id="fac95-111">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="fac95-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="fac95-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fac95-112">E_FAIL</span></span>|<span data-ttu-id="fac95-113">未知の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="fac95-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="fac95-114">メソッドでは、E_FAIL を返します、CLR はプロセス内で使用できなくします。</span><span class="sxs-lookup"><span data-stu-id="fac95-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="fac95-115">Api をホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="fac95-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fac95-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fac95-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fac95-117">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="fac95-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fac95-118">コメント</span><span class="sxs-lookup"><span data-stu-id="fac95-118">Remarks</span></span>  
 <span data-ttu-id="fac95-119">呼び出す必要は通常、`Start`メソッド、CLR がマネージ コードを実行する最初の要求時に自動的に開始されるためです。</span><span class="sxs-lookup"><span data-stu-id="fac95-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fac95-120">要件</span><span class="sxs-lookup"><span data-stu-id="fac95-120">Requirements</span></span>  
 <span data-ttu-id="fac95-121">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fac95-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fac95-122">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fac95-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fac95-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="fac95-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fac95-124">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="fac95-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fac95-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="fac95-125">See Also</span></span>  
 [<span data-ttu-id="fac95-126">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fac95-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
