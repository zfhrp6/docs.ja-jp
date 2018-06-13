---
title: ICLRProbingAssemblyEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum
helpviewer_keywords:
- ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c295a5633dedf1f0c85a9a697fea5524ee03fafc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432699"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="f4e73-102">ICLRProbingAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4e73-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="f4e73-103">ホストを作成またはその id を認識することがなく、共通言語ランタイム (CLR)、内部にあるアセンブリの id 情報を使用して、アセンブリの検索 id を取得できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f4e73-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4e73-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f4e73-104">Methods</span></span>  
  
|<span data-ttu-id="f4e73-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f4e73-105">Method</span></span>|<span data-ttu-id="f4e73-106">説明</span><span class="sxs-lookup"><span data-stu-id="f4e73-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4e73-107">Get メソッド</span><span class="sxs-lookup"><span data-stu-id="f4e73-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="f4e73-108">指定したインデックス位置には、アセンブリの id を取得します。</span><span class="sxs-lookup"><span data-stu-id="f4e73-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4e73-109">コメント</span><span class="sxs-lookup"><span data-stu-id="f4e73-109">Remarks</span></span>  
 <span data-ttu-id="f4e73-110">などのメソッド[iclrassemblyidentitymanager::getprobingassembliesfromreference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)を返す、`ICLRProbingAssemblyEnum`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="f4e73-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4e73-111">要件</span><span class="sxs-lookup"><span data-stu-id="f4e73-111">Requirements</span></span>  
 <span data-ttu-id="f4e73-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f4e73-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4e73-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f4e73-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4e73-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="f4e73-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4e73-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4e73-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4e73-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4e73-116">See Also</span></span>  
 [<span data-ttu-id="f4e73-117">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4e73-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="f4e73-118">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4e73-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="f4e73-119">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4e73-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
