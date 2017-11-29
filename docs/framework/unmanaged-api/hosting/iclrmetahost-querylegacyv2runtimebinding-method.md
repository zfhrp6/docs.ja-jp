---
title: "ICLRMetaHost::QueryLegacyV2RuntimeBinding メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.RequestRuntimeLoadedNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c273a1690828e37c8f7fcf5071e42e5bb2c58228
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="9d6d6-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding メソッド</span><span class="sxs-lookup"><span data-stu-id="9d6d6-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="9d6d6-103">レガシ アクティブ化ポリシーが関連付けられて、たとえばを使用してランタイムを表すインターフェイスを返します、`useLegacyV2RuntimeActivationPolicy`属性を[\<スタートアップ > 要素](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)ダイレクトを使用して、構成ファイルのエントリApi のレガシ アクティブ化のまたは呼び出すことによって、 [iclrruntimeinfo::bindaslegacyv2runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9d6d6-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d6d6-104">構文</span><span class="sxs-lookup"><span data-stu-id="9d6d6-104">Syntax</span></span>  
  
```  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d6d6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9d6d6-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="9d6d6-106">[in]このパラメーターの唯一の有効な値は Required.Currently`IID_ICLRRuntimeInfo`です。</span><span class="sxs-lookup"><span data-stu-id="9d6d6-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="9d6d6-107">[out] 必須。</span><span class="sxs-lookup"><span data-stu-id="9d6d6-107">[out] Required.</span></span> <span data-ttu-id="9d6d6-108">このメソッドが戻るときへのポインターを含む、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)はレガシ アクティブ化ポリシーにバインドされているランタイムを表すインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="9d6d6-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d6d6-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="9d6d6-109">Return Value</span></span>  
 <span data-ttu-id="9d6d6-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="9d6d6-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9d6d6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d6d6-111">HRESULT</span></span>|<span data-ttu-id="9d6d6-112">説明</span><span class="sxs-lookup"><span data-stu-id="9d6d6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d6d6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d6d6-113">S_OK</span></span>|<span data-ttu-id="9d6d6-114">メソッドは正常に完了し、レガシ アクティブ化ポリシーにバインドされているランタイムが返されました。</span><span class="sxs-lookup"><span data-stu-id="9d6d6-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="9d6d6-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9d6d6-115">S_FALSE</span></span>|<span data-ttu-id="9d6d6-116">メソッドは正常に完了しましたが、レガシ ランタイムはまだバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="9d6d6-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="9d6d6-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="9d6d6-117">E_NOINTERFACE</span></span>|<span data-ttu-id="9d6d6-118">メソッドで、レガシ アクティブ化ポリシーにバインドされているランタイムが見つかりましたが、`riid` はそのランタイムでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9d6d6-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d6d6-119">コメント</span><span class="sxs-lookup"><span data-stu-id="9d6d6-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d6d6-120">要件</span><span class="sxs-lookup"><span data-stu-id="9d6d6-120">Requirements</span></span>  
 <span data-ttu-id="9d6d6-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9d6d6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d6d6-122">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9d6d6-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9d6d6-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9d6d6-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d6d6-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d6d6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6d6-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d6d6-125">See Also</span></span>  
 [<span data-ttu-id="9d6d6-126">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9d6d6-126">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="9d6d6-127">ホスティング</span><span class="sxs-lookup"><span data-stu-id="9d6d6-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
