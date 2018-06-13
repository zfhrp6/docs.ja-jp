---
title: ICLROnEventManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c22dfa99d8069c060a525a9ae2cbef73d6625898
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434104"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="82c87-102">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82c87-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="82c87-103">ホストが登録および共通言語ランタイム (CLR) イベントに対するコールバックを登録解除できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="82c87-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82c87-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="82c87-104">Methods</span></span>  
  
|<span data-ttu-id="82c87-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="82c87-105">Method</span></span>|<span data-ttu-id="82c87-106">説明</span><span class="sxs-lookup"><span data-stu-id="82c87-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82c87-107">RegisterActionOnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="82c87-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="82c87-108">指定したイベントのコールバック ポインターを登録します。</span><span class="sxs-lookup"><span data-stu-id="82c87-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="82c87-109">UnregisterActionOnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="82c87-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="82c87-110">指定されたイベントに対して以前に登録されたコールバック ポインターを登録解除します。</span><span class="sxs-lookup"><span data-stu-id="82c87-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82c87-111">コメント</span><span class="sxs-lookup"><span data-stu-id="82c87-111">Remarks</span></span>  
 <span data-ttu-id="82c87-112">参照を取得しているホストを登録およびイベント コールバックを登録解除、`ICLROnEventManager`を呼び出して、 [iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="82c87-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82c87-113">により記述されたイベント[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) 2 回以上とアンロードまたは CLR を無効にすることを通知するさまざまなスレッドから起動されることができます。</span><span class="sxs-lookup"><span data-stu-id="82c87-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82c87-114">要件</span><span class="sxs-lookup"><span data-stu-id="82c87-114">Requirements</span></span>  
 <span data-ttu-id="82c87-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="82c87-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82c87-116">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="82c87-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82c87-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="82c87-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82c87-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82c87-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82c87-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="82c87-119">See Also</span></span>  
 [<span data-ttu-id="82c87-120">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="82c87-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="82c87-121">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82c87-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="82c87-122">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82c87-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="82c87-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82c87-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
