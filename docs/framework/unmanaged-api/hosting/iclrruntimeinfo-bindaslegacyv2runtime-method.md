---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 690287bf54f98c19298504ee3058a59ef88a87f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433162"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="fbf74-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime メソッド</span><span class="sxs-lookup"><span data-stu-id="fbf74-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="fbf74-103">すべてレガシ共通言語ランタイム (CLR) バージョン 2 のアクティブ化ポリシーの決定の現在のランタイムにバインドします。</span><span class="sxs-lookup"><span data-stu-id="fbf74-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbf74-104">構文</span><span class="sxs-lookup"><span data-stu-id="fbf74-104">Syntax</span></span>  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fbf74-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="fbf74-105">Return Value</span></span>  
 <span data-ttu-id="fbf74-106">このメソッドは、次の特定の Hresult を返します。</span><span class="sxs-lookup"><span data-stu-id="fbf74-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="fbf74-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fbf74-107">HRESULT</span></span>|<span data-ttu-id="fbf74-108">説明</span><span class="sxs-lookup"><span data-stu-id="fbf74-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fbf74-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="fbf74-109">S_OK</span></span>|<span data-ttu-id="fbf74-110">バインディングが成功したか、このランタイムがレガシ CLR バージョン 2 のアクティブ化のポリシー実行時に既にバインドされています。</span><span class="sxs-lookup"><span data-stu-id="fbf74-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="fbf74-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="fbf74-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="fbf74-112">異なるランタイムは、従来の CLR バージョン 2 のアクティブ化ポリシーに既にバインドされています。</span><span class="sxs-lookup"><span data-stu-id="fbf74-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbf74-113">コメント</span><span class="sxs-lookup"><span data-stu-id="fbf74-113">Remarks</span></span>  
 <span data-ttu-id="fbf74-114">現在のランタイムがすべてレガシ CLR バージョン 2 のアクティブ化ポリシーの決定に既にバインドされている場合 (たとえばを使用して、`useLegacyV2RuntimeActivationPolicy`属性を[\<スタートアップ > 要素](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)構成ファイルで)、このメソッドエラーの結果を返しません代わりと同様、メソッドがレガシ アクティブ化ポリシーを正常にバインドしたかどうかに、結果は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="fbf74-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbf74-115">要件</span><span class="sxs-lookup"><span data-stu-id="fbf74-115">Requirements</span></span>  
 <span data-ttu-id="fbf74-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fbf74-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbf74-117">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="fbf74-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fbf74-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="fbf74-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbf74-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbf74-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf74-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbf74-120">See Also</span></span>  
 [<span data-ttu-id="fbf74-121">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fbf74-121">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="fbf74-122">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fbf74-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="fbf74-123">ホスティング</span><span class="sxs-lookup"><span data-stu-id="fbf74-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="fbf74-124">\<startup> 要素</span><span class="sxs-lookup"><span data-stu-id="fbf74-124">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
