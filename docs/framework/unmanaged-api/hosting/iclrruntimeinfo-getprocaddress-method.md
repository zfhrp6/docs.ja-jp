---
title: ICLRRuntimeInfo::GetProcAddress メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8e50a018016b885a3513cbd885b8e5115f18113
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432922"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="5eb34-102">ICLRRuntimeInfo::GetProcAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="5eb34-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="5eb34-103">このインターフェイスに関連付けられている共通言語ランタイム (CLR) からエクスポートされた、指定された関数のアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="5eb34-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="5eb34-104">このメソッドは、 [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="5eb34-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eb34-105">構文</span><span class="sxs-lookup"><span data-stu-id="5eb34-105">Syntax</span></span>  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5eb34-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5eb34-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="5eb34-107">[in]エクスポートされた関数の名前。</span><span class="sxs-lookup"><span data-stu-id="5eb34-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="5eb34-108">[out]エクスポートされた関数のアドレス。</span><span class="sxs-lookup"><span data-stu-id="5eb34-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5eb34-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="5eb34-109">Return Value</span></span>  
 <span data-ttu-id="5eb34-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="5eb34-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5eb34-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5eb34-111">HRESULT</span></span>|<span data-ttu-id="5eb34-112">説明</span><span class="sxs-lookup"><span data-stu-id="5eb34-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5eb34-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5eb34-113">S_OK</span></span>|<span data-ttu-id="5eb34-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="5eb34-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="5eb34-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="5eb34-115">E_POINTER</span></span>|<span data-ttu-id="5eb34-116">`pszProcName` または `ppProc` が null です。</span><span class="sxs-lookup"><span data-stu-id="5eb34-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="5eb34-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="5eb34-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="5eb34-118">指定された関数は、エクスポートされた関数ではありません。</span><span class="sxs-lookup"><span data-stu-id="5eb34-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5eb34-119">コメント</span><span class="sxs-lookup"><span data-stu-id="5eb34-119">Remarks</span></span>  
 <span data-ttu-id="5eb34-120">このメソッドによって、CLR が読み込まれますが、初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="5eb34-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5eb34-121">要件</span><span class="sxs-lookup"><span data-stu-id="5eb34-121">Requirements</span></span>  
 <span data-ttu-id="5eb34-122">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5eb34-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5eb34-123">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5eb34-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5eb34-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5eb34-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5eb34-125">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5eb34-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eb34-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5eb34-126">See Also</span></span>  
 [<span data-ttu-id="5eb34-127">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5eb34-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="5eb34-128">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5eb34-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="5eb34-129">ホスティング</span><span class="sxs-lookup"><span data-stu-id="5eb34-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
