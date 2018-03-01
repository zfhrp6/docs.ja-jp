---
title: "ICLRRuntimeHost::ExecuteInDefaultAppDomain メソッド"
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
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ec4cf37150cab7b52066a884b6fe117b0e611106
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="358ce-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="358ce-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="358ce-103">指定したマネージ アセンブリで、指定した型の指定したメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="358ce-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="358ce-104">構文</span><span class="sxs-lookup"><span data-stu-id="358ce-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,   
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="358ce-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="358ce-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="358ce-106">[in]パス、<xref:System.Reflection.Assembly>を定義する、<xref:System.Type>メソッドが呼び出される、します。</span><span class="sxs-lookup"><span data-stu-id="358ce-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="358ce-107">[in]名前、<xref:System.Type>に呼び出すメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="358ce-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="358ce-108">[in]呼び出すメソッドの名前です。</span><span class="sxs-lookup"><span data-stu-id="358ce-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="358ce-109">[in]メソッドに渡す文字列パラメーター。</span><span class="sxs-lookup"><span data-stu-id="358ce-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="358ce-110">[out]呼び出されたメソッドで返される整数値。</span><span class="sxs-lookup"><span data-stu-id="358ce-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="358ce-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="358ce-111">Return Value</span></span>  
  
|<span data-ttu-id="358ce-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="358ce-112">HRESULT</span></span>|<span data-ttu-id="358ce-113">説明</span><span class="sxs-lookup"><span data-stu-id="358ce-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="358ce-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="358ce-114">S_OK</span></span>|<span data-ttu-id="358ce-115">`ExecuteInDefaultAppDomain`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="358ce-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="358ce-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="358ce-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="358ce-117">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="358ce-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="358ce-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="358ce-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="358ce-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="358ce-119">The call timed out.</span></span>|  
|<span data-ttu-id="358ce-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="358ce-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="358ce-121">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="358ce-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="358ce-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="358ce-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="358ce-123">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="358ce-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="358ce-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="358ce-124">E_FAIL</span></span>|<span data-ttu-id="358ce-125">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="358ce-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="358ce-126">メソッドから E_FAIL が返された場合、CRL はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="358ce-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="358ce-127">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="358ce-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="358ce-128">コメント</span><span class="sxs-lookup"><span data-stu-id="358ce-128">Remarks</span></span>  
 <span data-ttu-id="358ce-129">呼び出されたメソッドは、次のシグネチャが必要です。</span><span class="sxs-lookup"><span data-stu-id="358ce-129">The invoked method must have the following signature:</span></span>  
  
```  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="358ce-130">ここで`pwzMethodName`呼び出されたメソッドの名前を表すと`pwzArgument`そのメソッドにパラメーターとして渡される文字列値を表します。</span><span class="sxs-lookup"><span data-stu-id="358ce-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="358ce-131">S_OK HRESULT 値が設定されている場合`pReturnValue`が呼び出されたメソッドで返された整数値に設定します。</span><span class="sxs-lookup"><span data-stu-id="358ce-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="358ce-132">それ以外の場合、`pReturnValue`が設定されていません。</span><span class="sxs-lookup"><span data-stu-id="358ce-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="358ce-133">必要条件</span><span class="sxs-lookup"><span data-stu-id="358ce-133">Requirements</span></span>  
 <span data-ttu-id="358ce-134">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="358ce-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="358ce-135">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="358ce-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="358ce-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="358ce-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="358ce-137">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="358ce-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358ce-138">参照</span><span class="sxs-lookup"><span data-stu-id="358ce-138">See Also</span></span>  
 [<span data-ttu-id="358ce-139">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="358ce-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
