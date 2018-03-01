---
title: "IActionOnCLREvent インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4b51784f07a90faa9eeb29c18a784d4fbc2c4654
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="9e5e0-102">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e5e0-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="9e5e0-103">提供、 [iactiononclrevent::onevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)への呼び出しを使用して、登録されているイベントのコールバックを実行するメソッドに、 [iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9e5e0-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e5e0-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="9e5e0-104">Methods</span></span>  
  
|<span data-ttu-id="9e5e0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9e5e0-105">Method</span></span>|<span data-ttu-id="9e5e0-106">説明</span><span class="sxs-lookup"><span data-stu-id="9e5e0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e5e0-107">OnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="9e5e0-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="9e5e0-108">登録されたイベントのコールバックを実行します。</span><span class="sxs-lookup"><span data-stu-id="9e5e0-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9e5e0-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="9e5e0-109">Requirements</span></span>  
 <span data-ttu-id="9e5e0-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9e5e0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e5e0-111">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e5e0-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e5e0-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9e5e0-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e5e0-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e5e0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e5e0-114">参照</span><span class="sxs-lookup"><span data-stu-id="9e5e0-114">See Also</span></span>  
 [<span data-ttu-id="9e5e0-115">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="9e5e0-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="9e5e0-116">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e5e0-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="9e5e0-117">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e5e0-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="9e5e0-118">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e5e0-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
