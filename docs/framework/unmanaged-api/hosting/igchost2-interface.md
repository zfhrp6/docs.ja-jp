---
title: IGCHost2 インターフェイス
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c6cbf44bd02a45b9b99d2dad63fc5bd6219c4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437678"
---
# <a name="igchost2-interface"></a><span data-ttu-id="2a21f-102">IGCHost2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a21f-102">IGCHost2 Interface</span></span>
<span data-ttu-id="2a21f-103">ガベージ コレクション システムに関する情報を取得して、ガベージ コレクションの一部の側面を制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="2a21f-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a21f-104">新しい開発では、ことをお勧めを使用すること、 [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)インターフェイスの代わりにします。</span><span class="sxs-lookup"><span data-stu-id="2a21f-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a21f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="2a21f-105">Methods</span></span>  
  
|<span data-ttu-id="2a21f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="2a21f-106">Method</span></span>|<span data-ttu-id="2a21f-107">説明</span><span class="sxs-lookup"><span data-stu-id="2a21f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a21f-108">SetGCStartupLimitsEx メソッド</span><span class="sxs-lookup"><span data-stu-id="2a21f-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="2a21f-109">ジェネレーション 0 のセグメントのサイズと最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="2a21f-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="2a21f-110">により、ジェネレーション 0 とセグメントのサイズよりも大きい`DWORD`です。</span><span class="sxs-lookup"><span data-stu-id="2a21f-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a21f-111">要件</span><span class="sxs-lookup"><span data-stu-id="2a21f-111">Requirements</span></span>  
 <span data-ttu-id="2a21f-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2a21f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a21f-113">**ヘッダー:** GCHost.idl、GCHost.h</span><span class="sxs-lookup"><span data-stu-id="2a21f-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="2a21f-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="2a21f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a21f-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a21f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a21f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a21f-116">See Also</span></span>  
 [<span data-ttu-id="2a21f-117">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a21f-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="2a21f-118">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a21f-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="2a21f-119">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="2a21f-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
