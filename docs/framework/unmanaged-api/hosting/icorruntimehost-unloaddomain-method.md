---
title: ICorRuntimeHost::UnloadDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.UnloadDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4db96133315b23a2d0b4bd32b597ee03f5d697b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438117"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="bd0d1-102">ICorRuntimeHost::UnloadDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="bd0d1-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="bd0d1-103">現在のプロセスから指定されたアプリケーション ドメインをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="bd0d1-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd0d1-104">構文</span><span class="sxs-lookup"><span data-stu-id="bd0d1-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd0d1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bd0d1-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="bd0d1-106">[in]型のポインター<xref:System._AppDomain?displayProperty=nameWithType>をアンロードできるドメインを表すです。</span><span class="sxs-lookup"><span data-stu-id="bd0d1-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd0d1-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="bd0d1-107">Return Value</span></span>  
  
|<span data-ttu-id="bd0d1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bd0d1-108">HRESULT</span></span>|<span data-ttu-id="bd0d1-109">説明</span><span class="sxs-lookup"><span data-stu-id="bd0d1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bd0d1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bd0d1-110">S_OK</span></span>|<span data-ttu-id="bd0d1-111">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="bd0d1-111">The operation was successful.</span></span>|  
|<span data-ttu-id="bd0d1-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="bd0d1-112">S_FALSE</span></span>|<span data-ttu-id="bd0d1-113">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="bd0d1-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="bd0d1-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bd0d1-114">E_FAIL</span></span>|<span data-ttu-id="bd0d1-115">未知の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="bd0d1-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="bd0d1-116">メソッドには、E_FAIL が返されます、共通言語ランタイム (CLR) は、プロセスで使用可能なできなくします。</span><span class="sxs-lookup"><span data-stu-id="bd0d1-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="bd0d1-117">Api をホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="bd0d1-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bd0d1-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bd0d1-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bd0d1-119">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="bd0d1-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bd0d1-120">要件</span><span class="sxs-lookup"><span data-stu-id="bd0d1-120">Requirements</span></span>  
 <span data-ttu-id="bd0d1-121">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bd0d1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd0d1-122">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bd0d1-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd0d1-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="bd0d1-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd0d1-124">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="bd0d1-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd0d1-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd0d1-125">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="bd0d1-126">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bd0d1-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
