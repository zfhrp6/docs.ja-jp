---
title: "ICLRRuntimeInfo::GetProcAddress メソッド"
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
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2878b23a2f848657e1d26b3bfb8395f8897c0632
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="edaf7-102">ICLRRuntimeInfo::GetProcAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="edaf7-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="edaf7-103">このインターフェイスに関連付けられている共通言語ランタイム (CLR) からエクスポートされた、指定された関数のアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="edaf7-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="edaf7-104">このメソッドは、 [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="edaf7-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edaf7-105">構文</span><span class="sxs-lookup"><span data-stu-id="edaf7-105">Syntax</span></span>  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="edaf7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="edaf7-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="edaf7-107">[in]エクスポートされた関数の名前。</span><span class="sxs-lookup"><span data-stu-id="edaf7-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="edaf7-108">[out]エクスポートされた関数のアドレス。</span><span class="sxs-lookup"><span data-stu-id="edaf7-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="edaf7-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="edaf7-109">Return Value</span></span>  
 <span data-ttu-id="edaf7-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="edaf7-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="edaf7-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="edaf7-111">HRESULT</span></span>|<span data-ttu-id="edaf7-112">説明</span><span class="sxs-lookup"><span data-stu-id="edaf7-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="edaf7-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="edaf7-113">S_OK</span></span>|<span data-ttu-id="edaf7-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="edaf7-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="edaf7-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="edaf7-115">E_POINTER</span></span>|<span data-ttu-id="edaf7-116">`pszProcName` または `ppProc` が null です。</span><span class="sxs-lookup"><span data-stu-id="edaf7-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="edaf7-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="edaf7-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="edaf7-118">指定された関数は、エクスポートされた関数ではありません。</span><span class="sxs-lookup"><span data-stu-id="edaf7-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edaf7-119">コメント</span><span class="sxs-lookup"><span data-stu-id="edaf7-119">Remarks</span></span>  
 <span data-ttu-id="edaf7-120">このメソッドによって、CLR が読み込まれますが、初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="edaf7-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edaf7-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="edaf7-121">Requirements</span></span>  
 <span data-ttu-id="edaf7-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="edaf7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edaf7-123">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="edaf7-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="edaf7-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="edaf7-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="edaf7-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edaf7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edaf7-126">参照</span><span class="sxs-lookup"><span data-stu-id="edaf7-126">See Also</span></span>  
 [<span data-ttu-id="edaf7-127">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="edaf7-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="edaf7-128">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="edaf7-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="edaf7-129">ホスティング</span><span class="sxs-lookup"><span data-stu-id="edaf7-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
