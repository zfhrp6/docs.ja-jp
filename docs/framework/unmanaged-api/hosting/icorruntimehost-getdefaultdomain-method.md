---
title: "ICorRuntimeHost::GetDefaultDomain メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.GetDefaultDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c482247a0a227c202bb81db09d13ad9af71e60f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="54c14-102">ICorRuntimeHost::GetDefaultDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="54c14-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="54c14-103">型のインターフェイス ポインターを取得<xref:System._AppDomain?displayProperty=nameWithType>現在のプロセスの既定のドメインを表すです。</span><span class="sxs-lookup"><span data-stu-id="54c14-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54c14-104">構文</span><span class="sxs-lookup"><span data-stu-id="54c14-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54c14-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="54c14-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="54c14-106">[out]型のインターフェイス ポインター<xref:System._AppDomain?displayProperty=nameWithType>を<xref:System.AppDomain>プロセスの既定のアプリケーション ドメインを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="54c14-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="54c14-107">このポインターが型指定された`IUnknown`呼び出し元は一般に呼び出す必要がありますので、`QueryInterface`型のインターフェイス ポインターを取得する<xref:System._AppDomain?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="54c14-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54c14-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="54c14-108">Return Value</span></span>  
  
|<span data-ttu-id="54c14-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54c14-109">HRESULT</span></span>|<span data-ttu-id="54c14-110">説明</span><span class="sxs-lookup"><span data-stu-id="54c14-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54c14-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="54c14-111">S_OK</span></span>|<span data-ttu-id="54c14-112">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="54c14-112">The operation was successful.</span></span>|  
|<span data-ttu-id="54c14-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="54c14-113">S_FALSE</span></span>|<span data-ttu-id="54c14-114">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="54c14-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="54c14-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="54c14-115">E_FAIL</span></span>|<span data-ttu-id="54c14-116">未知の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="54c14-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="54c14-117">メソッドには、E_FAIL が返されます、共通言語ランタイム (CLR) は、プロセスで使用可能なできなくします。</span><span class="sxs-lookup"><span data-stu-id="54c14-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="54c14-118">Api をホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="54c14-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="54c14-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="54c14-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="54c14-120">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="54c14-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="54c14-121">要件</span><span class="sxs-lookup"><span data-stu-id="54c14-121">Requirements</span></span>  
 <span data-ttu-id="54c14-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="54c14-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54c14-123">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="54c14-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54c14-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="54c14-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54c14-125">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="54c14-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c14-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="54c14-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="54c14-127">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54c14-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
