---
title: "ICLRMetaHostPolicy インターフェイス"
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
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cd9b8d6aef2289833a0bd192b838e6f70ea8c0ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="26245-102">ICLRMetaHostPolicy インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26245-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="26245-103">提供、 [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)メソッドで、ポリシーの条件に基づいた、共通言語ランタイム (CLR) インターフェイスへのポインターを返します、アセンブリ、バージョンおよび構成ファイルを管理します。</span><span class="sxs-lookup"><span data-stu-id="26245-103">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="26245-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="26245-104">Methods</span></span>  
  
|<span data-ttu-id="26245-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="26245-105">Method</span></span>|<span data-ttu-id="26245-106">説明</span><span class="sxs-lookup"><span data-stu-id="26245-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="26245-107">GetRequestedRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="26245-107">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="26245-108">推奨される CLR インターフェイスがポリシーの条件に基づいて、アセンブリ、バージョン、および構成ファイルの管理を提供します。</span><span class="sxs-lookup"><span data-stu-id="26245-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26245-109">コメント</span><span class="sxs-lookup"><span data-stu-id="26245-109">Remarks</span></span>  
 <span data-ttu-id="26245-110">呼び出して、このインターフェイスへの参照を取得することができます、 [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)次のコードに示すように機能します。</span><span class="sxs-lookup"><span data-stu-id="26245-110">You can get a reference to this interface by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  <span data-ttu-id="26245-111">このインターフェイスは実際に読み込んだり、CLR が優先される CLR のバージョンがインストールされるか、読み込まれて使用可能なバージョンに基づく返しますだけでアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="26245-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="26245-112">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]ポリシーに統合 API をホストできるように、特定のニーズを持つホストでは、基本的な機能を使用して意図しない低下を生じることがなく可能性があります。</span><span class="sxs-lookup"><span data-stu-id="26245-112">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="26245-113">たとえば、メソッドが論理的には必要ありませんが、特定の CLR にバインド多く MSCorEE.dll エクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="26245-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="26245-114">[METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)列挙には、ホストの大半によく使われるバインド ポリシーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="26245-114">The [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26245-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="26245-115">Requirements</span></span>  
 <span data-ttu-id="26245-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="26245-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26245-117">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="26245-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="26245-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="26245-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26245-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26245-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26245-120">参照</span><span class="sxs-lookup"><span data-stu-id="26245-120">See Also</span></span>  
 [<span data-ttu-id="26245-121">.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26245-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="26245-122">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26245-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="26245-123">ホスティング</span><span class="sxs-lookup"><span data-stu-id="26245-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
