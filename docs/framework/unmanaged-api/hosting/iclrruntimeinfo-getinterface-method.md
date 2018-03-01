---
title: "ICLRRuntimeInfo::GetInterface メソッド"
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
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3c5150a10a813da85fc035c7bfa43a7647fac308
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="f43a9-102">ICLRRuntimeInfo::GetInterface メソッド</span><span class="sxs-lookup"><span data-stu-id="f43a9-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="f43a9-103">現在のプロセスに CLR を読み込んで、ランタイム、インターフェイス ポインターをなど返します[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)、 [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)、および[IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="f43a9-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="f43a9-104">このメソッドはすべて、 `CorBindTo`\* で機能、 [CLR をホストしている関数の非推奨](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)セクションです。</span><span class="sxs-lookup"><span data-stu-id="f43a9-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f43a9-105">構文</span><span class="sxs-lookup"><span data-stu-id="f43a9-105">Syntax</span></span>  
  
```  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f43a9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f43a9-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="f43a9-107">[in]コクラスの CLSID インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="f43a9-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="f43a9-108">[in]要求された IID`rclsid`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="f43a9-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="f43a9-109">[out]照会されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f43a9-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f43a9-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="f43a9-110">Return Value</span></span>  
 <span data-ttu-id="f43a9-111">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="f43a9-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f43a9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f43a9-112">HRESULT</span></span>|<span data-ttu-id="f43a9-113">説明</span><span class="sxs-lookup"><span data-stu-id="f43a9-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f43a9-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f43a9-114">S_OK</span></span>|<span data-ttu-id="f43a9-115">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="f43a9-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="f43a9-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f43a9-116">E_POINTER</span></span>|<span data-ttu-id="f43a9-117">`ppUnk` が null です。</span><span class="sxs-lookup"><span data-stu-id="f43a9-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="f43a9-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f43a9-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f43a9-119">十分なメモリが要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="f43a9-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="f43a9-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="f43a9-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="f43a9-121">異なるランタイムは、従来の CLR バージョン 2 のアクティブ化ポリシーに既にバインドされています。</span><span class="sxs-lookup"><span data-stu-id="f43a9-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f43a9-122">コメント</span><span class="sxs-lookup"><span data-stu-id="f43a9-122">Remarks</span></span>  
 <span data-ttu-id="f43a9-123">このメソッドによって、CLR が読み込まれますが、初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="f43a9-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="f43a9-124">次の表は、サポートされる組み合わせの`rclsid`と`riid`です。</span><span class="sxs-lookup"><span data-stu-id="f43a9-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="f43a9-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="f43a9-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="f43a9-126">IID_IMetaDataDispenser、IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="f43a9-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="f43a9-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="f43a9-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="f43a9-128">IID_IMetaDataDispenser、IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="f43a9-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="f43a9-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="f43a9-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="f43a9-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="f43a9-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="f43a9-131">Clsid_clrruntimehost です。</span><span class="sxs-lookup"><span data-stu-id="f43a9-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="f43a9-132">Iid_iclrruntimehost です。</span><span class="sxs-lookup"><span data-stu-id="f43a9-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="f43a9-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="f43a9-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="f43a9-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="f43a9-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="f43a9-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="f43a9-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="f43a9-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="f43a9-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="f43a9-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="f43a9-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="f43a9-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="f43a9-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f43a9-139">必要条件</span><span class="sxs-lookup"><span data-stu-id="f43a9-139">Requirements</span></span>  
 <span data-ttu-id="f43a9-140">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f43a9-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f43a9-141">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f43a9-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f43a9-142">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="f43a9-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f43a9-143">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f43a9-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f43a9-144">参照</span><span class="sxs-lookup"><span data-stu-id="f43a9-144">See Also</span></span>  
 [<span data-ttu-id="f43a9-145">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f43a9-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="f43a9-146">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f43a9-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="f43a9-147">ホスティング</span><span class="sxs-lookup"><span data-stu-id="f43a9-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
