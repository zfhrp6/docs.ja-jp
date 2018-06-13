---
title: ICLRMetaHost::QueryLegacyV2RuntimeBinding メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1664c47e580730fb0000465f9010e024c64fec2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432945"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="93b50-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding メソッド</span><span class="sxs-lookup"><span data-stu-id="93b50-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="93b50-103">レガシ アクティブ化ポリシーが関連付けられて、たとえばを使用してランタイムを表すインターフェイスを返します、`useLegacyV2RuntimeActivationPolicy`属性を[\<スタートアップ > 要素](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)ダイレクトを使用して、構成ファイルのエントリApi のレガシ アクティブ化のまたは呼び出すことによって、 [iclrruntimeinfo::bindaslegacyv2runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="93b50-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93b50-104">構文</span><span class="sxs-lookup"><span data-stu-id="93b50-104">Syntax</span></span>  
  
```  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93b50-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="93b50-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="93b50-106">[in]このパラメーターの唯一の有効な値は Required.Currently`IID_ICLRRuntimeInfo`です。</span><span class="sxs-lookup"><span data-stu-id="93b50-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="93b50-107">[out] 必須。</span><span class="sxs-lookup"><span data-stu-id="93b50-107">[out] Required.</span></span> <span data-ttu-id="93b50-108">このメソッドが戻るときへのポインターを含む、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)はレガシ アクティブ化ポリシーにバインドされているランタイムを表すインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="93b50-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93b50-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="93b50-109">Return Value</span></span>  
 <span data-ttu-id="93b50-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="93b50-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="93b50-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="93b50-111">HRESULT</span></span>|<span data-ttu-id="93b50-112">説明</span><span class="sxs-lookup"><span data-stu-id="93b50-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93b50-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="93b50-113">S_OK</span></span>|<span data-ttu-id="93b50-114">メソッドは正常に完了し、レガシ アクティブ化ポリシーにバインドされているランタイムが返されました。</span><span class="sxs-lookup"><span data-stu-id="93b50-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="93b50-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="93b50-115">S_FALSE</span></span>|<span data-ttu-id="93b50-116">メソッドは正常に完了しましたが、レガシ ランタイムはまだバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="93b50-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="93b50-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="93b50-117">E_NOINTERFACE</span></span>|<span data-ttu-id="93b50-118">メソッドで、レガシ アクティブ化ポリシーにバインドされているランタイムが見つかりましたが、`riid` はそのランタイムでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="93b50-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93b50-119">コメント</span><span class="sxs-lookup"><span data-stu-id="93b50-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93b50-120">要件</span><span class="sxs-lookup"><span data-stu-id="93b50-120">Requirements</span></span>  
 <span data-ttu-id="93b50-121">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="93b50-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93b50-122">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="93b50-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="93b50-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="93b50-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93b50-124">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93b50-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b50-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="93b50-125">See Also</span></span>  
 [<span data-ttu-id="93b50-126">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93b50-126">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="93b50-127">ホスティング</span><span class="sxs-lookup"><span data-stu-id="93b50-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
