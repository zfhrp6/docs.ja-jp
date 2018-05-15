---
title: IActionOnCLREvent インターフェイス
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24191e93d0d8b27d01a914cae76c9ff4e0a7182d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="d38e7-102">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d38e7-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="d38e7-103">提供、 [iactiononclrevent::onevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)への呼び出しを使用して、登録されているイベントのコールバックを実行するメソッドに、 [iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d38e7-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d38e7-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="d38e7-104">Methods</span></span>  
  
|<span data-ttu-id="d38e7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d38e7-105">Method</span></span>|<span data-ttu-id="d38e7-106">説明</span><span class="sxs-lookup"><span data-stu-id="d38e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d38e7-107">OnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="d38e7-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="d38e7-108">登録されたイベントのコールバックを実行します。</span><span class="sxs-lookup"><span data-stu-id="d38e7-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d38e7-109">要件</span><span class="sxs-lookup"><span data-stu-id="d38e7-109">Requirements</span></span>  
 <span data-ttu-id="d38e7-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d38e7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d38e7-111">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d38e7-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d38e7-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d38e7-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d38e7-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d38e7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d38e7-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d38e7-114">See Also</span></span>  
 [<span data-ttu-id="d38e7-115">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="d38e7-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="d38e7-116">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d38e7-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="d38e7-117">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d38e7-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="d38e7-118">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d38e7-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
