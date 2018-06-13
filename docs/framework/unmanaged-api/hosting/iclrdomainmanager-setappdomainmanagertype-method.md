---
title: ICLRDomainManager::SetAppDomainManagerType メソッド
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea10f9b7d23d8ca6a94d05cac6e586b434c000d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435544"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="5146f-102">ICLRDomainManager::SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="5146f-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="5146f-103">派生する型を指定、<xref:System.AppDomainManager?displayProperty=nameWithType>の既定のアプリケーション ドメインを初期化するために使用されるアプリケーション ドメイン マネージャーのクラスです。</span><span class="sxs-lookup"><span data-stu-id="5146f-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5146f-104">構文</span><span class="sxs-lookup"><span data-stu-id="5146f-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5146f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5146f-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="5146f-106">[in]アプリケーション ドメイン マネージャーの種類; を含むアセンブリの表示名例:"AdMgrExample、バージョン 1.0.0.0、Culture = neutral, PublicKeyToken = 6856bccf150f00b3 を ="。</span><span class="sxs-lookup"><span data-stu-id="5146f-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="5146f-107">[in]名前空間を含む、アプリケーション ドメイン マネージャーの型名。</span><span class="sxs-lookup"><span data-stu-id="5146f-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="5146f-108">[in]組み合わせた[EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)アプリケーション ドメイン マネージャーに関する情報を提供する列挙値。</span><span class="sxs-lookup"><span data-stu-id="5146f-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5146f-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="5146f-109">Return Value</span></span>  
 <span data-ttu-id="5146f-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="5146f-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5146f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5146f-111">HRESULT</span></span>|<span data-ttu-id="5146f-112">説明</span><span class="sxs-lookup"><span data-stu-id="5146f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5146f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5146f-113">S_OK</span></span>|<span data-ttu-id="5146f-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="5146f-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="5146f-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5146f-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5146f-116">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="5146f-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5146f-117">コメント</span><span class="sxs-lookup"><span data-stu-id="5146f-117">Remarks</span></span>  
 <span data-ttu-id="5146f-118">現在、のみ定義されている値を`dwInitializeDomainFlags`は`eInitializeNewDomainFlags_NoSecurityChanges`、これによりは、共通言語ランタイム (CLR) の実行中のセキュリティ設定をアプリケーション ドメイン マネージャーが変更はこと、<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5146f-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5146f-119">これにより、条件付きのアセンブリの読み込みを最適化するために CLR <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 属性です。</span><span class="sxs-lookup"><span data-stu-id="5146f-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="5146f-120">このアセンブリのセットの推移的閉包が大きい場合は、起動時間が大幅に向上をこれがあります。</span><span class="sxs-lookup"><span data-stu-id="5146f-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5146f-121">ホストを指定する場合`eInitializeNewDomainFlags_NoSecurityChanges`アプリケーション ドメイン マネージャー、<xref:System.InvalidOperationException>が、アプリケーション ドメインのセキュリティを変更するあらゆる試みが行われた場合にスローされます。</span><span class="sxs-lookup"><span data-stu-id="5146f-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="5146f-122">呼び出す、 [iclrcontrol::setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)はメソッドを呼び出すことと同じ`ICLRDomainManager::SetAppDomainManagerType`で`eInitializeNewDomainFlags_None`です。</span><span class="sxs-lookup"><span data-stu-id="5146f-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5146f-123">要件</span><span class="sxs-lookup"><span data-stu-id="5146f-123">Requirements</span></span>  
 <span data-ttu-id="5146f-124">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5146f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5146f-125">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5146f-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5146f-126">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5146f-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5146f-127">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5146f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5146f-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="5146f-128">See Also</span></span>  
 [<span data-ttu-id="5146f-129">ホスティング</span><span class="sxs-lookup"><span data-stu-id="5146f-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="5146f-130">ICLRDomainManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5146f-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 [<span data-ttu-id="5146f-131">EInitializeNewDomainFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="5146f-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
