---
title: "ICLRDomainManager インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager
helpviewer_keywords: ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75a7e93d26a5c77484d78ad4632bedf8def6a44b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="bc305-102">ICLRDomainManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bc305-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="bc305-103">ホストが初期化プロパティを指定して既定のアプリケーション ドメインを初期化するために使用されるアプリケーション ドメイン マネージャーを指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="bc305-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bc305-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="bc305-104">Methods</span></span>  
  
|<span data-ttu-id="bc305-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="bc305-105">Method</span></span>|<span data-ttu-id="bc305-106">説明</span><span class="sxs-lookup"><span data-stu-id="bc305-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bc305-107">SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="bc305-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="bc305-108">派生する型を指定、<xref:System.AppDomainManager?displayProperty=nameWithType>の既定のアプリケーション ドメインを初期化するために使用されるアプリケーション ドメイン マネージャーのクラスです。</span><span class="sxs-lookup"><span data-stu-id="bc305-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="bc305-109">SetPropertiesForDefaultAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="bc305-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="bc305-110">既定のアプリケーション ドメインを初期化するために使用されるプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="bc305-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc305-111">コメント</span><span class="sxs-lookup"><span data-stu-id="bc305-111">Remarks</span></span>  
 <span data-ttu-id="bc305-112">このインターフェイスのインスタンスを取得する、 [iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) IID マネージャーの種類を持つメソッド`IID_ICLRDomainManager`です。</span><span class="sxs-lookup"><span data-stu-id="bc305-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc305-113">要件</span><span class="sxs-lookup"><span data-stu-id="bc305-113">Requirements</span></span>  
 <span data-ttu-id="bc305-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bc305-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc305-115">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="bc305-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bc305-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="bc305-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc305-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc305-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc305-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc305-118">See Also</span></span>  
 [<span data-ttu-id="bc305-119">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bc305-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="bc305-120">ホスティング</span><span class="sxs-lookup"><span data-stu-id="bc305-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
