---
title: "GetRequestedRuntimeVersionForCLSID 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeVersionForCLSID
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeVersionForCLSID
helpviewer_keywords: GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a5b9e4b186b6c9b91c1182e8700268f0e1c038f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="e7af5-102">GetRequestedRuntimeVersionForCLSID 関数</span><span class="sxs-lookup"><span data-stu-id="e7af5-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="e7af5-103">適切な共通言語ランタイム (CLR) のバージョン情報に、指定したクラスを取得`CLSID`です。</span><span class="sxs-lookup"><span data-stu-id="e7af5-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="e7af5-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="e7af5-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7af5-105">構文</span><span class="sxs-lookup"><span data-stu-id="e7af5-105">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7af5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e7af5-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="e7af5-107">[in] `CLSID`のコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="e7af5-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="e7af5-108">[out] 正常完了時にバージョン番号の文字列を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="e7af5-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="e7af5-109">[in] ワイド文字単位のサイズの`pVersion`バッファー。</span><span class="sxs-lookup"><span data-stu-id="e7af5-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="e7af5-110">[out]返されたバッファーの長さ、(バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="e7af5-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="e7af5-111">[in] CLSID_RESOLUTION_FLAGS 値のいずれか。</span><span class="sxs-lookup"><span data-stu-id="e7af5-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="e7af5-112">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e7af5-112">The following values are supported:</span></span>  
  
-   <span data-ttu-id="e7af5-113">CLSID_RESOLUTION_DEFAULT: (0x0) 既定の相互運用機能の動作を指定する必要がありますを使用します。</span><span class="sxs-lookup"><span data-stu-id="e7af5-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
-   <span data-ttu-id="e7af5-114">CLSID_RESOLUTION_REGISTERED: (0x1)、レジストリが検索するかや、ポリシーに shim を適用を指定する必要がありますを適用します。</span><span class="sxs-lookup"><span data-stu-id="e7af5-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7af5-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="e7af5-115">Return Value</span></span>  
  
|<span data-ttu-id="e7af5-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7af5-116">HRESULT</span></span>|<span data-ttu-id="e7af5-117">説明</span><span class="sxs-lookup"><span data-stu-id="e7af5-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7af5-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="e7af5-118">S_OK</span></span>|<span data-ttu-id="e7af5-119">関数が正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="e7af5-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="e7af5-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e7af5-120">E_INVALIDARG</span></span>|<span data-ttu-id="e7af5-121">パラメーターのいずれかが無効な型または形式です。</span><span class="sxs-lookup"><span data-stu-id="e7af5-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="e7af5-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="e7af5-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="e7af5-123">`pVersion`バッファーがバージョン文字列全体を保持するのに十分ではありません。</span><span class="sxs-lookup"><span data-stu-id="e7af5-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="e7af5-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="e7af5-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="e7af5-125">指定した登録されているクラスはありません`CLSID`です。</span><span class="sxs-lookup"><span data-stu-id="e7af5-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="e7af5-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="e7af5-126">E_POINTER</span></span>|<span data-ttu-id="e7af5-127">`dwLength`null、または`cchBuffer`バージョン文字列を保持するために十分な大きさが、`pVersion`が null です。</span><span class="sxs-lookup"><span data-stu-id="e7af5-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e7af5-128">要件</span><span class="sxs-lookup"><span data-stu-id="e7af5-128">Requirements</span></span>  
 <span data-ttu-id="e7af5-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e7af5-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7af5-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e7af5-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7af5-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7af5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7af5-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7af5-132">See Also</span></span>  
 [<span data-ttu-id="e7af5-133">推奨されなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="e7af5-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
