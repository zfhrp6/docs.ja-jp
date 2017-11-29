---
title: "IGCHost2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost2
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost2
helpviewer_keywords: IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c6706696e3fd5158d2b49a4d114d978a26510b67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="igchost2-interface"></a><span data-ttu-id="b5463-102">IGCHost2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b5463-102">IGCHost2 Interface</span></span>
<span data-ttu-id="b5463-103">ガベージ コレクション システムに関する情報を取得して、ガベージ コレクションの一部の側面を制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b5463-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5463-104">新しい開発では、ことをお勧めを使用すること、 [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)インターフェイスの代わりにします。</span><span class="sxs-lookup"><span data-stu-id="b5463-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b5463-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b5463-105">Methods</span></span>  
  
|<span data-ttu-id="b5463-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b5463-106">Method</span></span>|<span data-ttu-id="b5463-107">説明</span><span class="sxs-lookup"><span data-stu-id="b5463-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5463-108">SetGCStartupLimitsEx メソッド</span><span class="sxs-lookup"><span data-stu-id="b5463-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="b5463-109">ジェネレーション 0 のセグメントのサイズと最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="b5463-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="b5463-110">により、ジェネレーション 0 とセグメントのサイズよりも大きい`DWORD`です。</span><span class="sxs-lookup"><span data-stu-id="b5463-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5463-111">要件</span><span class="sxs-lookup"><span data-stu-id="b5463-111">Requirements</span></span>  
 <span data-ttu-id="b5463-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b5463-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5463-113">**ヘッダー:** GCHost.idl、GCHost.h</span><span class="sxs-lookup"><span data-stu-id="b5463-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="b5463-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b5463-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5463-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5463-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5463-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5463-116">See Also</span></span>  
 [<span data-ttu-id="b5463-117">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b5463-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="b5463-118">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b5463-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="b5463-119">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="b5463-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
