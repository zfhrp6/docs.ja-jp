---
title: "GetRequestedRuntimeVersion 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeVersion
helpviewer_keywords: GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13309a7362f468d3711176db2adc7a82e3b949d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="bf729-102">GetRequestedRuntimeVersion 関数</span><span class="sxs-lookup"><span data-stu-id="bf729-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="bf729-103">指定されたアプリケーションによって要求された共通言語ランタイム (CLR) のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="bf729-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="bf729-104">そのバージョンがインストールされていない場合は、要求されるバージョンより前にインストールされた最も新しいバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="bf729-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="bf729-105">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="bf729-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf729-106">構文</span><span class="sxs-lookup"><span data-stu-id="bf729-106">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf729-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bf729-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="bf729-108">[in]アプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="bf729-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="bf729-109">[out]正常完了時にバージョン番号の文字列を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="bf729-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="bf729-110">[in]バージョンのバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="bf729-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="bf729-111">[out]バージョン番号の文字列の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="bf729-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf729-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="bf729-112">Return Value</span></span>  
 <span data-ttu-id="bf729-113">このメソッドは、次の値に加え、WinError.h で定義されている標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="bf729-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="bf729-114">リターン コード</span><span class="sxs-lookup"><span data-stu-id="bf729-114">Return code</span></span>|<span data-ttu-id="bf729-115">説明</span><span class="sxs-lookup"><span data-stu-id="bf729-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="bf729-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="bf729-116">S_OK</span></span>|<span data-ttu-id="bf729-117">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="bf729-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="bf729-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="bf729-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="bf729-119">バージョン バッファーは、バージョン文字列を保存するのに十分な大きさではありません。</span><span class="sxs-lookup"><span data-stu-id="bf729-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="bf729-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="bf729-120">E_POINTER</span></span>|<span data-ttu-id="bf729-121">`pdwLength` が null です。</span><span class="sxs-lookup"><span data-stu-id="bf729-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bf729-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="bf729-122">Requirements</span></span>  
 <span data-ttu-id="bf729-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bf729-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf729-124">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bf729-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf729-125">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bf729-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf729-126">**.NET framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf729-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf729-127">参照</span><span class="sxs-lookup"><span data-stu-id="bf729-127">See Also</span></span>  
 [<span data-ttu-id="bf729-128">GetRequestedRuntimeInfo 関数</span><span class="sxs-lookup"><span data-stu-id="bf729-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [<span data-ttu-id="bf729-129">GetVersionFromProcess 関数</span><span class="sxs-lookup"><span data-stu-id="bf729-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [<span data-ttu-id="bf729-130">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="bf729-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
