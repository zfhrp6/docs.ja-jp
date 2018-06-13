---
title: IGCHost::SetGCStartupLimits メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbe94aa67c9cf9ac587b7fca9f5cbeca4870506b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437210"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="e272c-102">IGCHost::SetGCStartupLimits メソッド</span><span class="sxs-lookup"><span data-stu-id="e272c-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="e272c-103">ジェネレーション 0 のセグメントのサイズと最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="e272c-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e272c-104">以降で、[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]セグメントのサイズを設定することができます、およびサイズの最大のジェネレーション 0 の値より大きい`DWORD`を使用して、 [igchost 2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e272c-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e272c-105">構文</span><span class="sxs-lookup"><span data-stu-id="e272c-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e272c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e272c-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="e272c-107">[in]ガベージ コレクション システムによって使用されるセグメントのサイズ。</span><span class="sxs-lookup"><span data-stu-id="e272c-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="e272c-108">[in]ジェネレーション 0 の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="e272c-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e272c-109">コメント</span><span class="sxs-lookup"><span data-stu-id="e272c-109">Remarks</span></span>  
 <span data-ttu-id="e272c-110">`SetGCStartupLimits`メソッドを 1 回だけ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e272c-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="e272c-111">これらの値は、後で変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="e272c-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e272c-112">要件</span><span class="sxs-lookup"><span data-stu-id="e272c-112">Requirements</span></span>  
 <span data-ttu-id="e272c-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e272c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e272c-114">**ヘッダー:** GCHost.idl、GCHost.h</span><span class="sxs-lookup"><span data-stu-id="e272c-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="e272c-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e272c-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e272c-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e272c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e272c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e272c-117">See Also</span></span>  
 [<span data-ttu-id="e272c-118">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e272c-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
