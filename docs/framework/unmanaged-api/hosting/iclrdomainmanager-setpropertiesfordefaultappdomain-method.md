---
title: ICLRDomainManager::SetPropertiesForDefaultAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18db77b42af47b76bf1b3b66748d586c4c41dbd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433555"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="102d4-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="102d4-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="102d4-103">既定のアプリケーション ドメインを初期化するために使用されるプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="102d4-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="102d4-104">構文</span><span class="sxs-lookup"><span data-stu-id="102d4-104">Syntax</span></span>  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="102d4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="102d4-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="102d4-106">[in]内のエントリの数`pwszPropertyNames`と`pwszPropertyValues`です。</span><span class="sxs-lookup"><span data-stu-id="102d4-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="102d4-107">[in]プロパティ名、またはプロパティがない場合は null の配列。</span><span class="sxs-lookup"><span data-stu-id="102d4-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="102d4-108">現時点では、このメソッドによって認識される唯一のプロパティ名は、"PARTIAL_TRUST_VISIBLE_ASSEMBLIES"です。</span><span class="sxs-lookup"><span data-stu-id="102d4-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="102d4-109">[in]プロパティの値、またはプロパティがない場合は null の配列。</span><span class="sxs-lookup"><span data-stu-id="102d4-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="102d4-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="102d4-110">Return Value</span></span>  
 <span data-ttu-id="102d4-111">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="102d4-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="102d4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="102d4-112">HRESULT</span></span>|<span data-ttu-id="102d4-113">説明</span><span class="sxs-lookup"><span data-stu-id="102d4-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="102d4-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="102d4-114">S_OK</span></span>|<span data-ttu-id="102d4-115">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="102d4-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="102d4-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="102d4-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="102d4-117">`pwszPropertyNames` このメソッドによって認識されないプロパティ名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="102d4-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="102d4-118">コメント</span><span class="sxs-lookup"><span data-stu-id="102d4-118">Remarks</span></span>  
 <span data-ttu-id="102d4-119">"PARTIAL_TRUST_VISIBLE_ASSEMBLIES"のプロパティの値を条件式を持つアセンブリの一覧は、 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 属性を<xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType>フラグは、既定のアプリケーションに部分的に信頼された呼び出し元に表示できるようにします。ドメイン。</span><span class="sxs-lookup"><span data-stu-id="102d4-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="102d4-120">要件</span><span class="sxs-lookup"><span data-stu-id="102d4-120">Requirements</span></span>  
 <span data-ttu-id="102d4-121">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="102d4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="102d4-122">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="102d4-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="102d4-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="102d4-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="102d4-124">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="102d4-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="102d4-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="102d4-125">See Also</span></span>  
 [<span data-ttu-id="102d4-126">ホスティング</span><span class="sxs-lookup"><span data-stu-id="102d4-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="102d4-127">ICLRDomainManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="102d4-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
