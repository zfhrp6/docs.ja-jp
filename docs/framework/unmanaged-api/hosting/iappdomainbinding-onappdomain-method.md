---
title: "IAppDomainBinding::OnAppDomain メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppDomainBinding.OnAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: OnAppDomain
helpviewer_keywords:
- IAppDomainBinding::OnAppDomain method [.NET Framework hosting]
- OnAppDomain method [.NET Framework hosting]
ms.assetid: b419dcc9-e8aa-484b-af0d-0f40358edb99
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f5350b9c44c04a4faee3b5026bc2b97ff549d4b4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="37911-102">IAppDomainBinding::OnAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="37911-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="37911-103">共通言語ランタイム (CLR) にアプリケーション ドメインが作成されているホストに通知によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="37911-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37911-104">構文</span><span class="sxs-lookup"><span data-stu-id="37911-104">Syntax</span></span>  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37911-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="37911-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="37911-106">[in]ポインター、 [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx)を新しいアプリケーション ドメインを表すインターフェイス オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="37911-106">[in] A pointer to an [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37911-107">要件</span><span class="sxs-lookup"><span data-stu-id="37911-107">Requirements</span></span>  
 <span data-ttu-id="37911-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="37911-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37911-109">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="37911-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37911-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="37911-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37911-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37911-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37911-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="37911-112">See Also</span></span>  
 [<span data-ttu-id="37911-113">IAppDomainBinding インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37911-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
