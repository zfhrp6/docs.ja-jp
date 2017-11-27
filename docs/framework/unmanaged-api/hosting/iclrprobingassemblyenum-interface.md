---
title: "ICLRProbingAssemblyEnum インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRProbingAssemblyEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRProbingAssemblyEnum
helpviewer_keywords: ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6d810ab6e62c6df1b00305947de552ecdbe82141
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="da0ad-102">ICLRProbingAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="da0ad-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="da0ad-103">ホストを作成またはその id を認識することがなく、共通言語ランタイム (CLR)、内部にあるアセンブリの id 情報を使用して、アセンブリの検索 id を取得できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="da0ad-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da0ad-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="da0ad-104">Methods</span></span>  
  
|<span data-ttu-id="da0ad-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="da0ad-105">Method</span></span>|<span data-ttu-id="da0ad-106">説明</span><span class="sxs-lookup"><span data-stu-id="da0ad-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da0ad-107">Get メソッド</span><span class="sxs-lookup"><span data-stu-id="da0ad-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="da0ad-108">指定したインデックス位置には、アセンブリの id を取得します。</span><span class="sxs-lookup"><span data-stu-id="da0ad-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da0ad-109">コメント</span><span class="sxs-lookup"><span data-stu-id="da0ad-109">Remarks</span></span>  
 <span data-ttu-id="da0ad-110">などのメソッド[iclrassemblyidentitymanager::getprobingassembliesfromreference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)を返す、`ICLRProbingAssemblyEnum`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="da0ad-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da0ad-111">要件</span><span class="sxs-lookup"><span data-stu-id="da0ad-111">Requirements</span></span>  
 <span data-ttu-id="da0ad-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="da0ad-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da0ad-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="da0ad-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da0ad-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="da0ad-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da0ad-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da0ad-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da0ad-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="da0ad-116">See Also</span></span>  
 [<span data-ttu-id="da0ad-117">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="da0ad-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="da0ad-118">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="da0ad-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="da0ad-119">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="da0ad-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
