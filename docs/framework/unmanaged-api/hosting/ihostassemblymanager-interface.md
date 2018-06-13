---
title: IHostAssemblyManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c8c8d17723481fc5b41fe5f3006fe8db2c53d1ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438481"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="35355-102">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35355-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="35355-103">ホストが共通言語ランタイム (CLR) またはホストに読み込む必要のあるアセンブリのセットを指定できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="35355-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="35355-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="35355-104">Methods</span></span>  
  
|<span data-ttu-id="35355-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="35355-105">Method</span></span>|<span data-ttu-id="35355-106">説明</span><span class="sxs-lookup"><span data-stu-id="35355-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="35355-107">GetAssemblyStore メソッド</span><span class="sxs-lookup"><span data-stu-id="35355-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="35355-108">インターフェイス ポインターを取得、 [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)ホストによって読み込まれるアセンブリの一覧を表すです。</span><span class="sxs-lookup"><span data-stu-id="35355-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="35355-109">GetNonHostStoreAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="35355-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="35355-110">インターフェイス ポインターを取得、 [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)ホストに読み込む CLR が期待しているアセンブリの一覧を表すです。</span><span class="sxs-lookup"><span data-stu-id="35355-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35355-111">コメント</span><span class="sxs-lookup"><span data-stu-id="35355-111">Remarks</span></span>  
 <span data-ttu-id="35355-112">ホストが実装する必要はありません`IHostAssemblyManager`または`IHostAssemblyStore`です。</span><span class="sxs-lookup"><span data-stu-id="35355-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="35355-113">ホストが実装する場合`IHostAssemblyManager`もに実装する必要があります`IHostAssemblyStore`です。</span><span class="sxs-lookup"><span data-stu-id="35355-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="35355-114">ランタイムを照会、`IHostAssemblyManager`を呼び出して[ihostcontrol::gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)の初期化時に、 `IID` IID_IHostAssemblyManager のです。</span><span class="sxs-lookup"><span data-stu-id="35355-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35355-115">要件</span><span class="sxs-lookup"><span data-stu-id="35355-115">Requirements</span></span>  
 <span data-ttu-id="35355-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="35355-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35355-117">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="35355-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="35355-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="35355-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35355-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35355-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35355-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="35355-120">See Also</span></span>  
 [<span data-ttu-id="35355-121">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35355-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="35355-122">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35355-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="35355-123">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35355-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="35355-124">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35355-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
