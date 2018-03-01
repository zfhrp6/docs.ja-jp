---
title: "ICorRuntimeHost::CurrentDomain メソッド"
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
- ICorRuntimeHost.CurrentDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1ac437d924b6f5b290db117260701b554e29b6e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="0a8c6-102">ICorRuntimeHost::CurrentDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="0a8c6-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="0a8c6-103">型のインターフェイス ポインターを取得<xref:System.AppDomain?displayProperty=nameWithType>を表す現在のスレッドで読み込まれているドメインです。</span><span class="sxs-lookup"><span data-stu-id="0a8c6-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a8c6-104">構文</span><span class="sxs-lookup"><span data-stu-id="0a8c6-104">Syntax</span></span>  
  
```  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a8c6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a8c6-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="0a8c6-106">[out]型のポインター<xref:System.AppDomain?displayProperty=nameWithType>スレッドの現在のアプリケーション ドメインを表すです。</span><span class="sxs-lookup"><span data-stu-id="0a8c6-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="0a8c6-107">このポインターが型指定された`IUnknown`呼び出し元は一般に呼び出す必要がありますので、`QueryInterface`型のポインターを取得する<xref:System._AppDomain>です。</span><span class="sxs-lookup"><span data-stu-id="0a8c6-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a8c6-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a8c6-108">Return Value</span></span>  
  
|<span data-ttu-id="0a8c6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a8c6-109">HRESULT</span></span>|<span data-ttu-id="0a8c6-110">説明</span><span class="sxs-lookup"><span data-stu-id="0a8c6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a8c6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a8c6-111">S_OK</span></span>|<span data-ttu-id="0a8c6-112">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="0a8c6-112">The operation was successful.</span></span>|  
|<span data-ttu-id="0a8c6-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0a8c6-113">S_FALSE</span></span>|<span data-ttu-id="0a8c6-114">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="0a8c6-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="0a8c6-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0a8c6-115">E_FAIL</span></span>|<span data-ttu-id="0a8c6-116">未知の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0a8c6-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="0a8c6-117">メソッドには、E_FAIL が返されます、共通言語ランタイム (CLR) は、プロセスで使用可能なできなくします。</span><span class="sxs-lookup"><span data-stu-id="0a8c6-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="0a8c6-118">Api をホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="0a8c6-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0a8c6-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0a8c6-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0a8c6-120">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="0a8c6-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a8c6-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="0a8c6-121">Requirements</span></span>  
 <span data-ttu-id="0a8c6-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0a8c6-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a8c6-123">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0a8c6-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a8c6-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0a8c6-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a8c6-125">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="0a8c6-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a8c6-126">参照</span><span class="sxs-lookup"><span data-stu-id="0a8c6-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="0a8c6-127">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a8c6-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
