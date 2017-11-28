---
title: "ICLRDomainManager::SetPropertiesForDefaultAppDomain メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fabf42c16dc41e29ca3d14e00e76797fa8f2a9e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="31ebc-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="31ebc-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="31ebc-103">既定のアプリケーション ドメインを初期化するために使用されるプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="31ebc-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31ebc-104">構文</span><span class="sxs-lookup"><span data-stu-id="31ebc-104">Syntax</span></span>  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31ebc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="31ebc-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="31ebc-106">[in]内のエントリの数`pwszPropertyNames`と`pwszPropertyValues`です。</span><span class="sxs-lookup"><span data-stu-id="31ebc-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="31ebc-107">[in]プロパティ名、またはプロパティがない場合は null の配列。</span><span class="sxs-lookup"><span data-stu-id="31ebc-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="31ebc-108">現時点では、このメソッドによって認識される唯一のプロパティ名は、"PARTIAL_TRUST_VISIBLE_ASSEMBLIES"です。</span><span class="sxs-lookup"><span data-stu-id="31ebc-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="31ebc-109">[in]プロパティの値、またはプロパティがない場合は null の配列。</span><span class="sxs-lookup"><span data-stu-id="31ebc-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31ebc-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="31ebc-110">Return Value</span></span>  
 <span data-ttu-id="31ebc-111">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="31ebc-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="31ebc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="31ebc-112">HRESULT</span></span>|<span data-ttu-id="31ebc-113">説明</span><span class="sxs-lookup"><span data-stu-id="31ebc-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="31ebc-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="31ebc-114">S_OK</span></span>|<span data-ttu-id="31ebc-115">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="31ebc-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="31ebc-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="31ebc-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="31ebc-117">`pwszPropertyNames`このメソッドによって認識されないプロパティ名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="31ebc-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31ebc-118">コメント</span><span class="sxs-lookup"><span data-stu-id="31ebc-118">Remarks</span></span>  
 <span data-ttu-id="31ebc-119">"PARTIAL_TRUST_VISIBLE_ASSEMBLIES"のプロパティの値を条件式を持つアセンブリの一覧は、 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 属性を<xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType>フラグは、既定のアプリケーションに部分的に信頼された呼び出し元に表示できるようにします。ドメイン。</span><span class="sxs-lookup"><span data-stu-id="31ebc-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31ebc-120">要件</span><span class="sxs-lookup"><span data-stu-id="31ebc-120">Requirements</span></span>  
 <span data-ttu-id="31ebc-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="31ebc-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31ebc-122">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="31ebc-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="31ebc-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="31ebc-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31ebc-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31ebc-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31ebc-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="31ebc-125">See Also</span></span>  
 [<span data-ttu-id="31ebc-126">ホスティング</span><span class="sxs-lookup"><span data-stu-id="31ebc-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="31ebc-127">ICLRDomainManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="31ebc-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
