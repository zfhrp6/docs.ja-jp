---
title: "ICorRuntimeHost::CreateDomainEx メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomainEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2a577e1bd8765c7359e521b007bea943de7a984
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="72641-102">ICorRuntimeHost::CreateDomainEx メソッド</span><span class="sxs-lookup"><span data-stu-id="72641-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="72641-103">アプリケーション ドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="72641-103">Creates an application domain.</span></span> <span data-ttu-id="72641-104">呼び出し元が、型のインターフェイス ポインターを受け取ります<xref:System._AppDomain>、型のインスタンスに<xref:System.AppDomain?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="72641-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="72641-105">この方法では、呼び出し、返されたその他の機能を構成する IAppDomainSetup インスタンス<xref:System._AppDomain>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="72641-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72641-106">構文</span><span class="sxs-lookup"><span data-stu-id="72641-106">Syntax</span></span>  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72641-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="72641-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="72641-108">[in]ドメインにわかりやすい名前を指定するために使用する省略可能なパラメーター。</span><span class="sxs-lookup"><span data-stu-id="72641-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="72641-109">このフレンドリ名は、ドメインを識別するデバッガーなどのユーザー インターフェイスで表示できます。</span><span class="sxs-lookup"><span data-stu-id="72641-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="72641-110">[in]型の省略可能なインターフェイス ポインター`IAppDomainSetup`への呼び出しによって取得した、 [icorruntimehost::createdomainsetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="72641-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="72641-111">[in]ポインターの省略可能な配列`IIdentity`権限セットを確立するためにセキュリティ ポリシーによってマップされている証拠を表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="72641-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="72641-112">`IIdentity`オブジェクトを取得するには呼び出すことによって、 [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="72641-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="72641-113">[out]型のインターフェイス ポインター<xref:System._AppDomain>のインスタンスに<xref:System.AppDomain?displayProperty=nameWithType>ドメインをさらに制御を使用できます。</span><span class="sxs-lookup"><span data-stu-id="72641-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72641-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="72641-114">Return Value</span></span>  
  
|<span data-ttu-id="72641-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72641-115">HRESULT</span></span>|<span data-ttu-id="72641-116">説明</span><span class="sxs-lookup"><span data-stu-id="72641-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72641-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="72641-117">S_OK</span></span>|<span data-ttu-id="72641-118">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="72641-118">The operation was successful.</span></span>|  
|<span data-ttu-id="72641-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="72641-119">S_FALSE</span></span>|<span data-ttu-id="72641-120">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="72641-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="72641-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72641-121">E_FAIL</span></span>|<span data-ttu-id="72641-122">未知の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="72641-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="72641-123">メソッドには、E_FAIL が返されます、共通言語ランタイム (CLR) は、プロセスで使用可能なできなくします。</span><span class="sxs-lookup"><span data-stu-id="72641-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="72641-124">Api をホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="72641-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="72641-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="72641-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="72641-126">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="72641-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72641-127">コメント</span><span class="sxs-lookup"><span data-stu-id="72641-127">Remarks</span></span>  
 <span data-ttu-id="72641-128">`CreateDomainEx`機能を拡張[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)を渡す、呼び出し元を許可することで、`IAppDomainSetup`アプリケーション ドメインを構成するためのプロパティ値を持つインスタンス。</span><span class="sxs-lookup"><span data-stu-id="72641-128">`CreateDomainEx` extends the capabilities of [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72641-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="72641-129">Requirements</span></span>  
 <span data-ttu-id="72641-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="72641-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72641-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="72641-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72641-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="72641-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72641-133">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="72641-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72641-134">参照</span><span class="sxs-lookup"><span data-stu-id="72641-134">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [<span data-ttu-id="72641-135">CreateDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="72641-135">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)  
 [<span data-ttu-id="72641-136">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72641-136">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
