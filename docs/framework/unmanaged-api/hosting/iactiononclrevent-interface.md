---
title: "IActionOnCLREvent インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IActionOnCLREvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IActionOnCLREvent
helpviewer_keywords: IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eecc04fea993de3c502d1a203f0023c81c3b7909
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="35d9f-102">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35d9f-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="35d9f-103">提供、 [iactiononclrevent::onevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)への呼び出しを使用して、登録されているイベントのコールバックを実行するメソッドに、 [iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="35d9f-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="35d9f-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="35d9f-104">Methods</span></span>  
  
|<span data-ttu-id="35d9f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="35d9f-105">Method</span></span>|<span data-ttu-id="35d9f-106">説明</span><span class="sxs-lookup"><span data-stu-id="35d9f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="35d9f-107">OnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="35d9f-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="35d9f-108">登録されたイベントのコールバックを実行します。</span><span class="sxs-lookup"><span data-stu-id="35d9f-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="35d9f-109">要件</span><span class="sxs-lookup"><span data-stu-id="35d9f-109">Requirements</span></span>  
 <span data-ttu-id="35d9f-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="35d9f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35d9f-111">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="35d9f-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="35d9f-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="35d9f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35d9f-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35d9f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35d9f-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="35d9f-114">See Also</span></span>  
 [<span data-ttu-id="35d9f-115">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="35d9f-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="35d9f-116">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35d9f-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="35d9f-117">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35d9f-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="35d9f-118">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35d9f-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
