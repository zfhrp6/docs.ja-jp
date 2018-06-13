---
title: ComCallUnmarshal コクラス
ms.date: 03/30/2017
api_name:
- ComCallUnmarshal Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ComCallUnmarshal
helpviewer_keywords:
- ComCallUnmarshal coclass [.NET Framework hosting]
ms.assetid: 2adb5827-2268-4914-a1c6-f62b61880a45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7884d53630ca13a30d7b4efd55d46684a9dd7d30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427643"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="d8622-102">ComCallUnmarshal コクラス</span><span class="sxs-lookup"><span data-stu-id="d8622-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="d8622-103">インターフェイス ポインターのマーシャ リングを管理するためのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="d8622-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8622-104">構文</span><span class="sxs-lookup"><span data-stu-id="d8622-104">Syntax</span></span>  
  
```  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="d8622-105">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d8622-105">Interfaces</span></span>  
  
|<span data-ttu-id="d8622-106">Interface</span><span class="sxs-lookup"><span data-stu-id="d8622-106">Interface</span></span>|<span data-ttu-id="d8622-107">説明</span><span class="sxs-lookup"><span data-stu-id="d8622-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="d8622-108">作成、初期化、およびクライアント プロセスでプロキシを管理するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d8622-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8622-109">要件</span><span class="sxs-lookup"><span data-stu-id="d8622-109">Requirements</span></span>  
 <span data-ttu-id="d8622-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d8622-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8622-111">**ヘッダー:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="d8622-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="d8622-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d8622-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8622-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8622-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8622-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8622-114">See Also</span></span>  
 [<span data-ttu-id="d8622-115">ホスト コクラス</span><span class="sxs-lookup"><span data-stu-id="d8622-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
