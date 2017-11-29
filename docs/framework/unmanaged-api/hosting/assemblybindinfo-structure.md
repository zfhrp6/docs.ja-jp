---
title: "AssemblyBindInfo 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyBindInfo
helpviewer_keywords: AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4f23c8269c7dd7f85ad0f848c1dee2ed0bf903c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="e3439-102">AssemblyBindInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="e3439-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="e3439-103">参照アセンブリに関する詳細情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="e3439-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3439-104">構文</span><span class="sxs-lookup"><span data-stu-id="e3439-104">Syntax</span></span>  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="e3439-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="e3439-105">Members</span></span>  
  
|<span data-ttu-id="e3439-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e3439-106">Member</span></span>|<span data-ttu-id="e3439-107">説明</span><span class="sxs-lookup"><span data-stu-id="e3439-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="e3439-108">一意の識別子、`IStream`への呼び出しによって返される[ihostassemblystore::provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)、参照アセンブリが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="e3439-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="e3439-109">参照するアセンブリの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="e3439-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="e3439-110">バインディング ポリシー値を適用した後、参照するアセンブリの識別子。</span><span class="sxs-lookup"><span data-stu-id="e3439-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="e3439-111">1 つ、 [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)のどのバージョン管理ポリシーでは、存在する場合、する必要がありますアセンブリに適用される、参照先を示す値。</span><span class="sxs-lookup"><span data-stu-id="e3439-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3439-112">コメント</span><span class="sxs-lookup"><span data-stu-id="e3439-112">Remarks</span></span>  
 <span data-ttu-id="e3439-113">ホスト提供の一意識別子`dwAppDomainId`共通言語ランタイム (CLR) にします。</span><span class="sxs-lookup"><span data-stu-id="e3439-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="e3439-114">呼び出しの後に`IHostAssemblyStore::ProvideAssembly`を返します、ランタイムでは、識別子を使用して、確認するかどうかの内容、`IStream`マップされています。</span><span class="sxs-lookup"><span data-stu-id="e3439-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="e3439-115">場合は、ランタイムは、ストリームを再割り当てするのではなく、既存のコピーを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e3439-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="e3439-116">ランタイムも識別子を使用してこのルックアップ キーとしてから返されるストリームへの呼び出し[ihostassemblystore::providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="e3439-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="e3439-117">したがって、識別子とアセンブリの要求のモジュールの要求に対して一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3439-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3439-118">要件</span><span class="sxs-lookup"><span data-stu-id="e3439-118">Requirements</span></span>  
 <span data-ttu-id="e3439-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e3439-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3439-120">**ヘッダー:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="e3439-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="e3439-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e3439-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3439-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3439-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3439-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3439-123">See Also</span></span>  
 [<span data-ttu-id="e3439-124">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="e3439-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="e3439-125">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e3439-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="e3439-126">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e3439-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="e3439-127">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e3439-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="e3439-128">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e3439-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="e3439-129">ModuleBindInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="e3439-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
