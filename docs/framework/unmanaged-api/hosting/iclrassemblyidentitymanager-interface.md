---
title: "ICLRAssemblyIdentityManager インターフェイス"
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
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 168c67eb701d7dfc461553cfe32ed43dcea5e844
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="de055-102">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de055-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="de055-103">ホストとアセンブリに関する共通言語ランタイム (CLR) 間の通信をサポートするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="de055-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="de055-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="de055-104">Methods</span></span>  
  
|<span data-ttu-id="de055-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="de055-105">Method</span></span>|<span data-ttu-id="de055-106">説明</span><span class="sxs-lookup"><span data-stu-id="de055-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="de055-107">GetBindingIdentityFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="de055-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="de055-108">指定したファイル パスにあるアセンブリのデータのバインドのアセンブリ id を取得します。</span><span class="sxs-lookup"><span data-stu-id="de055-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="de055-109">GetBindingIdentityFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="de055-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="de055-110">指定したストリーム内のアセンブリの標準アセンブリの id データを取得します。</span><span class="sxs-lookup"><span data-stu-id="de055-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="de055-111">GetCLRAssemblyReferenceList メソッド</span><span class="sxs-lookup"><span data-stu-id="de055-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="de055-112">取得、 [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)部分アセンブリ id の指定された一覧からのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="de055-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="de055-113">GetProbingAssembliesFromReference メソッド</span><span class="sxs-lookup"><span data-stu-id="de055-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="de055-114">取得、 [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)列挙子を指定された id を持つアセンブリによって参照されるアセンブリの id。</span><span class="sxs-lookup"><span data-stu-id="de055-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="de055-115">GetReferencedAssembliesFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="de055-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="de055-116">取得、 [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)インスタンスを指定したファイル パスにあるアセンブリによって参照されるアセンブリの一覧を含むです。</span><span class="sxs-lookup"><span data-stu-id="de055-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="de055-117">GetReferencedAssembliesFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="de055-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="de055-118">ポインターを取得、`ICLRReferenceAssemblyEnum`指定のストリーム内のアセンブリによって参照されるアセンブリのアセンブリ id データを格納しているオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="de055-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="de055-119">IsStronglyNamed メソッド</span><span class="sxs-lookup"><span data-stu-id="de055-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="de055-120">指定したアセンブリは厳密な名前かどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="de055-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de055-121">コメント</span><span class="sxs-lookup"><span data-stu-id="de055-121">Remarks</span></span>  
 <span data-ttu-id="de055-122">使用して`ICLRAssemblyIdentityManager`のインスタンスを取得`ICLRAssemblyReferenceList`およびアセンブリ id を列挙します。</span><span class="sxs-lookup"><span data-stu-id="de055-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de055-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="de055-123">Requirements</span></span>  
 <span data-ttu-id="de055-124">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="de055-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de055-125">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="de055-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="de055-126">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="de055-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de055-127">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de055-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de055-128">参照</span><span class="sxs-lookup"><span data-stu-id="de055-128">See Also</span></span>  
 [<span data-ttu-id="de055-129">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de055-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="de055-130">ICLRProbingAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de055-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [<span data-ttu-id="de055-131">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de055-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
