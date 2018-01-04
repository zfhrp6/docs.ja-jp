---
title: "ICLRRuntimeInfo::GetVersionString メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetVersionString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ae6f21fac359006b6d2e56fdd4ba50fb18bb972
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="90b6e-102">ICLRRuntimeInfo::GetVersionString メソッド</span><span class="sxs-lookup"><span data-stu-id="90b6e-102">ICLRRuntimeInfo::GetVersionString Method</span></span>
<span data-ttu-id="90b6e-103">関連付けられている共通言語ランタイム (CLR) バージョン情報を取得する指定された[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="90b6e-103">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="90b6e-104">このメソッドには、次の関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="90b6e-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="90b6e-105">GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="90b6e-105">GetRequestedRuntimeInfo</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
-   [<span data-ttu-id="90b6e-106">GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="90b6e-106">GetRequestedRuntimeVersion</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="90b6e-107">構文</span><span class="sxs-lookup"><span data-stu-id="90b6e-107">Syntax</span></span>  
  
```  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90b6e-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="90b6e-108">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="90b6e-109">[out]形式で .NET Framework のコンパイル バージョン"v*A*.*B*[.*X*]"です。</span><span class="sxs-lookup"><span data-stu-id="90b6e-109">[out] The .NET Framework compilation version in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="90b6e-110">*A*、 *B*、および*X*はメジャー バージョン、マイナー バージョン、およびビルド番号に対応する 10 進数。</span><span class="sxs-lookup"><span data-stu-id="90b6e-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="90b6e-111">*X*は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="90b6e-111">*X* is optional.</span></span> <span data-ttu-id="90b6e-112">場合*X*が存在しない場合は末尾にピリオドです。</span><span class="sxs-lookup"><span data-stu-id="90b6e-112">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90b6e-113">このパラメーターでは、.NET Framework のバージョンのディレクトリ名を C:\Windows\Microsoft.NET\Framework 下に表示されますに一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90b6e-113">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="90b6e-114">値の例は、"v1.0.3705"、"v1.1.4322"、"v2.0.50727"および"v4.0 です。*x*"ここで、 *x*インストールされているビルドの数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="90b6e-114">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="90b6e-115">"V"プレフィックスが必須である注意してください。</span><span class="sxs-lookup"><span data-stu-id="90b6e-115">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="90b6e-116">[入力、出力].サイズを指定`pwzBuffer`バッファー オーバーランを回避します。</span><span class="sxs-lookup"><span data-stu-id="90b6e-116">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="90b6e-117">場合`pwzBuffer`は`null`、`pchBuffer`の必要なサイズを返します`pwzBuffer`事前割り当て使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="90b6e-117">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90b6e-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="90b6e-118">Return Value</span></span>  
 <span data-ttu-id="90b6e-119">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="90b6e-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="90b6e-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90b6e-120">HRESULT</span></span>|<span data-ttu-id="90b6e-121">説明</span><span class="sxs-lookup"><span data-stu-id="90b6e-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90b6e-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="90b6e-122">S_OK</span></span>|<span data-ttu-id="90b6e-123">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="90b6e-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="90b6e-124">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="90b6e-124">E_POINTER</span></span>|<span data-ttu-id="90b6e-125">`pwzBuffer` または `pchBuffer` が null です。</span><span class="sxs-lookup"><span data-stu-id="90b6e-125">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="90b6e-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="90b6e-126">Requirements</span></span>  
 <span data-ttu-id="90b6e-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="90b6e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90b6e-128">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="90b6e-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="90b6e-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="90b6e-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90b6e-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90b6e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90b6e-131">参照</span><span class="sxs-lookup"><span data-stu-id="90b6e-131">See Also</span></span>  
 [<span data-ttu-id="90b6e-132">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="90b6e-132">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="90b6e-133">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="90b6e-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="90b6e-134">.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="90b6e-134">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="90b6e-135">ホスティング</span><span class="sxs-lookup"><span data-stu-id="90b6e-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
