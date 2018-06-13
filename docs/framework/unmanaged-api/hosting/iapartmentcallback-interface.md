---
title: IApartmentCallback インターフェイス
ms.date: 03/30/2017
api_name:
- IApartmentCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IApartmentCallback
helpviewer_keywords:
- IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffa06fd42b5cfa09817bae9f0b3a3810e30f99c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430968"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="41e60-102">IApartmentCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="41e60-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="41e60-103">アパートメント内でコールバックを行うためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="41e60-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="41e60-104">*アパートメント*が同じスレッド アクセス要件を共有するオブジェクトのプロセス内の論理コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="41e60-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41e60-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="41e60-105">Methods</span></span>  
  
|<span data-ttu-id="41e60-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="41e60-106">Method</span></span>|<span data-ttu-id="41e60-107">説明</span><span class="sxs-lookup"><span data-stu-id="41e60-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41e60-108">DoCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="41e60-108">DoCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-docallback-method.md)|<span data-ttu-id="41e60-109">アパートメント内で指定された関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="41e60-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="41e60-110">要件</span><span class="sxs-lookup"><span data-stu-id="41e60-110">Requirements</span></span>  
 <span data-ttu-id="41e60-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="41e60-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41e60-112">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="41e60-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41e60-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="41e60-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41e60-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41e60-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e60-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="41e60-115">See Also</span></span>  
 [<span data-ttu-id="41e60-116">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="41e60-116">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
