---
title: ICLRRuntimeInfo::IsLoadable メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e60c3b06453e0f447249bddf5d4da5c240576577
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="7928d-102">ICLRRuntimeInfo::IsLoadable メソッド</span><span class="sxs-lookup"><span data-stu-id="7928d-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="7928d-103">このインターフェイスに関連付けられているランタイムを考慮に入れて、現在のプロセスに読み込めるかどうかを示す他のランタイムをプロセスに既に読み込まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7928d-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7928d-104">構文</span><span class="sxs-lookup"><span data-stu-id="7928d-104">Syntax</span></span>  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7928d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7928d-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="7928d-106">[out]`true` 、現在のプロセスに読み込まれます。 それ以外の場合、このランタイムができた場合`false`です。</span><span class="sxs-lookup"><span data-stu-id="7928d-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7928d-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="7928d-107">Return Value</span></span>  
 <span data-ttu-id="7928d-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="7928d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7928d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7928d-109">HRESULT</span></span>|<span data-ttu-id="7928d-110">説明</span><span class="sxs-lookup"><span data-stu-id="7928d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7928d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7928d-111">S_OK</span></span>|<span data-ttu-id="7928d-112">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="7928d-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="7928d-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7928d-113">E_POINTER</span></span>|<span data-ttu-id="7928d-114">`pbLoadable` が null です。</span><span class="sxs-lookup"><span data-stu-id="7928d-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7928d-115">コメント</span><span class="sxs-lookup"><span data-stu-id="7928d-115">Remarks</span></span>  
 <span data-ttu-id="7928d-116">別のランタイムが既にプロセスに読み込まれていて、インプロセスのサイド バイ サイド実行でこのインターフェイスに関連付けられているランタイムを読み込むことができます`pbLoadable`返します`true`です。</span><span class="sxs-lookup"><span data-stu-id="7928d-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="7928d-117">2 つのランタイムはサイド バイ サイドでプロセスを実行できない場合`pbLoadable`返します`false`です。</span><span class="sxs-lookup"><span data-stu-id="7928d-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="7928d-118">たとえば、共通言語ランタイム (CLR) バージョン 4 では、サイド バイ サイド CLR バージョン 2.0 を使用して同じプロセス内または CLR バージョン 1.1 を実行できます。</span><span class="sxs-lookup"><span data-stu-id="7928d-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="7928d-119">ただし、CLR バージョン 1.1 および CLR バージョン 2.0 では、サイド バイ サイドでプロセスを実行できません。</span><span class="sxs-lookup"><span data-stu-id="7928d-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="7928d-120">かどうかに、プロセスのランタイムは読み込まれません、このメソッドは常`true`です。</span><span class="sxs-lookup"><span data-stu-id="7928d-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7928d-121">要件</span><span class="sxs-lookup"><span data-stu-id="7928d-121">Requirements</span></span>  
 <span data-ttu-id="7928d-122">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7928d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7928d-123">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7928d-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7928d-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="7928d-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7928d-125">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7928d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7928d-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="7928d-126">See Also</span></span>  
 [<span data-ttu-id="7928d-127">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7928d-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="7928d-128">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7928d-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="7928d-129">ホスティング</span><span class="sxs-lookup"><span data-stu-id="7928d-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
