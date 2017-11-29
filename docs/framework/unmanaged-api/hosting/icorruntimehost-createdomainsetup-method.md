---
title: "ICorRuntimeHost::CreateDomainSetup メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomainSetup
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca09788ea403e2a60d6de0cb6834fdc90261b770
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="93a23-102">ICorRuntimeHost::CreateDomainSetup メソッド</span><span class="sxs-lookup"><span data-stu-id="93a23-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="93a23-103">インターフェイス ポインターの型を IAppDomainSetup を取得、<xref:System.AppDomainSetup?displayProperty=nameWithType>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="93a23-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="93a23-104">`IAppDomainSetup`作成する前に、アプリケーション ドメインの側面を構成する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="93a23-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93a23-105">構文</span><span class="sxs-lookup"><span data-stu-id="93a23-105">Syntax</span></span>  
  
```  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93a23-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="93a23-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="93a23-107">[out]インターフェイス ポインター、<xref:System.AppDomainSetup?displayProperty=nameWithType>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="93a23-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="93a23-108">このパラメーターとして型指定`IUnknown`呼び出し元は一般に呼び出す必要がありますので、`QueryInterface`型のインターフェイス ポインターを取得するには、このポインターを`IAppDomainSetup`です。</span><span class="sxs-lookup"><span data-stu-id="93a23-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93a23-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="93a23-109">Return Value</span></span>  
  
|<span data-ttu-id="93a23-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="93a23-110">HRESULT</span></span>|<span data-ttu-id="93a23-111">説明</span><span class="sxs-lookup"><span data-stu-id="93a23-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93a23-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="93a23-112">S_OK</span></span>|<span data-ttu-id="93a23-113">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="93a23-113">The operation was successful.</span></span>|  
|<span data-ttu-id="93a23-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="93a23-114">S_FALSE</span></span>|<span data-ttu-id="93a23-115">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="93a23-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="93a23-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="93a23-116">E_FAIL</span></span>|<span data-ttu-id="93a23-117">未知の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="93a23-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="93a23-118">メソッドには、E_FAIL が返されます、共通言語ランタイム (CLR) は、プロセスで使用可能なできなくします。</span><span class="sxs-lookup"><span data-stu-id="93a23-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="93a23-119">Api をホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="93a23-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="93a23-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="93a23-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="93a23-121">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="93a23-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93a23-122">コメント</span><span class="sxs-lookup"><span data-stu-id="93a23-122">Remarks</span></span>  
 <span data-ttu-id="93a23-123">このメソッドから返されるポインターは通常のパラメーターとして渡さ、 [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="93a23-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93a23-124">要件</span><span class="sxs-lookup"><span data-stu-id="93a23-124">Requirements</span></span>  
 <span data-ttu-id="93a23-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="93a23-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93a23-126">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="93a23-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93a23-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="93a23-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93a23-128">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="93a23-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a23-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="93a23-129">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [<span data-ttu-id="93a23-130">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93a23-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
