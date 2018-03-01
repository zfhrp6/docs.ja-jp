---
title: "ICLRReferenceAssemblyEnum インターフェイス"
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
- ICLRReferenceAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum
helpviewer_keywords:
- ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: 8adbf092-c3ba-4bee-b25b-0de6e43a4ce5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a7d2a295c4c35761d0a47e1690cd7b88387cecdb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrreferenceassemblyenum-interface"></a><span data-ttu-id="c8357-102">ICLRReferenceAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8357-102">ICLRReferenceAssemblyEnum Interface</span></span>
<span data-ttu-id="c8357-103">ホスト ファイルを作成またはその id を認識することがなく、共通言語ランタイム (CLR)、内部にあるアセンブリの id データを使用して、ストリームで参照されるアセンブリのセットを操作できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c8357-103">Provides methods that allow the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the common language runtime (CLR), without needing to create or understand those identities.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c8357-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="c8357-104">Methods</span></span>  
  
|<span data-ttu-id="c8357-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c8357-105">Method</span></span>|<span data-ttu-id="c8357-106">説明</span><span class="sxs-lookup"><span data-stu-id="c8357-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c8357-107">Get メソッド</span><span class="sxs-lookup"><span data-stu-id="c8357-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-get-method.md)|<span data-ttu-id="c8357-108">指定したインデックス位置には、アセンブリ id を取得します。</span><span class="sxs-lookup"><span data-stu-id="c8357-108">Gets the assembly identity at the supplied index.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c8357-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="c8357-109">Requirements</span></span>  
 <span data-ttu-id="c8357-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c8357-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8357-111">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c8357-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8357-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="c8357-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8357-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8357-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8357-114">参照</span><span class="sxs-lookup"><span data-stu-id="c8357-114">See Also</span></span>  
 [<span data-ttu-id="c8357-115">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8357-115">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="c8357-116">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8357-116">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="c8357-117">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8357-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
