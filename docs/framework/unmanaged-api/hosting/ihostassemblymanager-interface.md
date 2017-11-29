---
title: "IHostAssemblyManager インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyManager
helpviewer_keywords: IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b3761063201a48303884fdecddddf02558cd4e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="774d4-102">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="774d4-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="774d4-103">ホストが共通言語ランタイム (CLR) またはホストに読み込む必要のあるアセンブリのセットを指定できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="774d4-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="774d4-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="774d4-104">Methods</span></span>  
  
|<span data-ttu-id="774d4-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="774d4-105">Method</span></span>|<span data-ttu-id="774d4-106">説明</span><span class="sxs-lookup"><span data-stu-id="774d4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="774d4-107">GetAssemblyStore メソッド</span><span class="sxs-lookup"><span data-stu-id="774d4-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="774d4-108">インターフェイス ポインターを取得、 [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)ホストによって読み込まれるアセンブリの一覧を表すです。</span><span class="sxs-lookup"><span data-stu-id="774d4-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="774d4-109">GetNonHostStoreAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="774d4-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="774d4-110">インターフェイス ポインターを取得、 [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)ホストに読み込む CLR が期待しているアセンブリの一覧を表すです。</span><span class="sxs-lookup"><span data-stu-id="774d4-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="774d4-111">コメント</span><span class="sxs-lookup"><span data-stu-id="774d4-111">Remarks</span></span>  
 <span data-ttu-id="774d4-112">ホストが実装する必要はありません`IHostAssemblyManager`または`IHostAssemblyStore`です。</span><span class="sxs-lookup"><span data-stu-id="774d4-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="774d4-113">ホストが実装する場合`IHostAssemblyManager`もに実装する必要があります`IHostAssemblyStore`です。</span><span class="sxs-lookup"><span data-stu-id="774d4-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="774d4-114">ランタイムを照会、`IHostAssemblyManager`を呼び出して[ihostcontrol::gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)の初期化時に、 `IID` IID_IHostAssemblyManager のです。</span><span class="sxs-lookup"><span data-stu-id="774d4-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="774d4-115">要件</span><span class="sxs-lookup"><span data-stu-id="774d4-115">Requirements</span></span>  
 <span data-ttu-id="774d4-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="774d4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="774d4-117">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="774d4-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="774d4-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="774d4-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="774d4-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="774d4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="774d4-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="774d4-120">See Also</span></span>  
 [<span data-ttu-id="774d4-121">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="774d4-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="774d4-122">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="774d4-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="774d4-123">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="774d4-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="774d4-124">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="774d4-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
