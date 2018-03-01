---
title: "IGCHost2::SetGCStartupLimitsEx メソッド"
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
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f8ed2b2aa43fcf925b6202ab339209904e7c53af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="98edf-102">IGCHost2::SetGCStartupLimitsEx メソッド</span><span class="sxs-lookup"><span data-stu-id="98edf-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="98edf-103">ジェネレーション 0 のセグメントのサイズと最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="98edf-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98edf-104">構文</span><span class="sxs-lookup"><span data-stu-id="98edf-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="98edf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="98edf-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="98edf-106">[in]ガベージ コレクション システムによって使用されるセグメントのサイズ。</span><span class="sxs-lookup"><span data-stu-id="98edf-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="98edf-107">[in]ジェネレーション 0 の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="98edf-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98edf-108">コメント</span><span class="sxs-lookup"><span data-stu-id="98edf-108">Remarks</span></span>  
 <span data-ttu-id="98edf-109">値を`SetGCStartupLimitsEx`ホストを起動する前に、セットを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="98edf-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="98edf-110">これらの値は、後で変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="98edf-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98edf-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="98edf-111">Requirements</span></span>  
 <span data-ttu-id="98edf-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="98edf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98edf-113">**ヘッダー:** GCHost.idl、GCHost.h</span><span class="sxs-lookup"><span data-stu-id="98edf-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="98edf-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="98edf-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98edf-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98edf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98edf-116">参照</span><span class="sxs-lookup"><span data-stu-id="98edf-116">See Also</span></span>  
 [<span data-ttu-id="98edf-117">IGCHost2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98edf-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
