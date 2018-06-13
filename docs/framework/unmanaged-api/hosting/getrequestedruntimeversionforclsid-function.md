---
title: GetRequestedRuntimeVersionForCLSID 関数
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8d3a7168ce0ee3484384ae0e2d10ca00367fc9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432860"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="e6c85-102">GetRequestedRuntimeVersionForCLSID 関数</span><span class="sxs-lookup"><span data-stu-id="e6c85-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="e6c85-103">適切な共通言語ランタイム (CLR) のバージョン情報に、指定したクラスを取得`CLSID`です。</span><span class="sxs-lookup"><span data-stu-id="e6c85-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="e6c85-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="e6c85-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6c85-105">構文</span><span class="sxs-lookup"><span data-stu-id="e6c85-105">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6c85-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e6c85-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="e6c85-107">[in] `CLSID`のコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="e6c85-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="e6c85-108">[out] 正常完了時にバージョン番号の文字列を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="e6c85-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="e6c85-109">[in] ワイド文字単位のサイズの`pVersion`バッファー。</span><span class="sxs-lookup"><span data-stu-id="e6c85-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="e6c85-110">[out]返されたバッファーの長さ、(バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="e6c85-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="e6c85-111">[in] CLSID_RESOLUTION_FLAGS 値のいずれか。</span><span class="sxs-lookup"><span data-stu-id="e6c85-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="e6c85-112">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e6c85-112">The following values are supported:</span></span>  
  
-   <span data-ttu-id="e6c85-113">CLSID_RESOLUTION_DEFAULT: (0x0) 既定の相互運用機能の動作を指定する必要がありますを使用します。</span><span class="sxs-lookup"><span data-stu-id="e6c85-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
-   <span data-ttu-id="e6c85-114">CLSID_RESOLUTION_REGISTERED: (0x1)、レジストリが検索するかや、ポリシーに shim を適用を指定する必要がありますを適用します。</span><span class="sxs-lookup"><span data-stu-id="e6c85-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6c85-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="e6c85-115">Return Value</span></span>  
  
|<span data-ttu-id="e6c85-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6c85-116">HRESULT</span></span>|<span data-ttu-id="e6c85-117">説明</span><span class="sxs-lookup"><span data-stu-id="e6c85-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6c85-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6c85-118">S_OK</span></span>|<span data-ttu-id="e6c85-119">関数が正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="e6c85-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="e6c85-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e6c85-120">E_INVALIDARG</span></span>|<span data-ttu-id="e6c85-121">パラメーターのいずれかが無効な型または形式です。</span><span class="sxs-lookup"><span data-stu-id="e6c85-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="e6c85-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="e6c85-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="e6c85-123">`pVersion`バッファーがバージョン文字列全体を保持するのに十分ではありません。</span><span class="sxs-lookup"><span data-stu-id="e6c85-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="e6c85-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="e6c85-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="e6c85-125">指定した登録されているクラスはありません`CLSID`です。</span><span class="sxs-lookup"><span data-stu-id="e6c85-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="e6c85-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="e6c85-126">E_POINTER</span></span>|<span data-ttu-id="e6c85-127">`dwLength` null、または`cchBuffer`バージョン文字列を保持するために十分な大きさが、`pVersion`が null です。</span><span class="sxs-lookup"><span data-stu-id="e6c85-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6c85-128">要件</span><span class="sxs-lookup"><span data-stu-id="e6c85-128">Requirements</span></span>  
 <span data-ttu-id="e6c85-129">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e6c85-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6c85-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e6c85-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6c85-131">**.NET framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6c85-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c85-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6c85-132">See Also</span></span>  
 <span data-ttu-id="e6c85-133">
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span><span class="sxs-lookup"><span data-stu-id="e6c85-133">[Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span></span>
