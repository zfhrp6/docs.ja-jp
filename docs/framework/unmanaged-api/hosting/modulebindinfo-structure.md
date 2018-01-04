---
title: "ModuleBindInfo 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ModuleBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: ModuleBindInfo
helpviewer_keywords: ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399ba2471b4dc7c5e372a56a9dcab8117068a693
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="d9694-102">ModuleBindInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="d9694-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="d9694-103">参照されるモジュールとそれを含むアセンブリに関する詳細情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="d9694-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9694-104">構文</span><span class="sxs-lookup"><span data-stu-id="d9694-104">Syntax</span></span>  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="d9694-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="d9694-105">Members</span></span>  
  
|<span data-ttu-id="d9694-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="d9694-106">Member</span></span>|<span data-ttu-id="d9694-107">説明</span><span class="sxs-lookup"><span data-stu-id="d9694-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="d9694-108">一意の識別子、`IStream`への呼び出しによって返される、 [ihostassemblystore::providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)元となる参照されるモジュールが読み込まれるメソッド。</span><span class="sxs-lookup"><span data-stu-id="d9694-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="d9694-109">参照されるモジュールを含むアセンブリの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="d9694-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="d9694-110">参照されるモジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="d9694-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9694-111">コメント</span><span class="sxs-lookup"><span data-stu-id="d9694-111">Remarks</span></span>  
 <span data-ttu-id="d9694-112">`ModuleBindInfo`パラメーターとして渡される`IHostAssemblyStore::ProvideModule`です。</span><span class="sxs-lookup"><span data-stu-id="d9694-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="d9694-113">ホスト提供の一意識別子`dwAppDomainId`共通言語ランタイム (CLR) にします。</span><span class="sxs-lookup"><span data-stu-id="d9694-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="d9694-114">呼び出した後、 [ihostassemblystore::provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)ランタイム識別子を使用して決定メソッドが返されるかどうかの内容、`IStream`マップされています。</span><span class="sxs-lookup"><span data-stu-id="d9694-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="d9694-115">場合は、ランタイムは、ストリームを再割り当てするのではなく、既存のコピーを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d9694-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="d9694-116">ランタイムへの呼び出しから返されるストリームのルックアップ キーとしてこの識別子を使用するも、`IHostAssemblyStore::ProvideAssembly`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d9694-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="d9694-117">したがって、識別子は、アセンブリの要求だけモジュール同様の要求の一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9694-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9694-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="d9694-118">Requirements</span></span>  
 <span data-ttu-id="d9694-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d9694-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9694-120">**ヘッダー:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="d9694-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="d9694-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d9694-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9694-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9694-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9694-123">参照</span><span class="sxs-lookup"><span data-stu-id="d9694-123">See Also</span></span>  
 [<span data-ttu-id="d9694-124">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="d9694-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="d9694-125">AssemblyBindInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="d9694-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 [<span data-ttu-id="d9694-126">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d9694-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="d9694-127">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d9694-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="d9694-128">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d9694-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
