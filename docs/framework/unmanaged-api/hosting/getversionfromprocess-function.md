---
title: "GetVersionFromProcess 関数"
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
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: db5054ab9b71eb93005fc0315acba82d807487ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="96395-102">GetVersionFromProcess 関数</span><span class="sxs-lookup"><span data-stu-id="96395-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="96395-103">指定されたプロセスのハンドルに関連付けられている共通言語ランタイム (CLR) のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="96395-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="96395-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="96395-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96395-105">構文</span><span class="sxs-lookup"><span data-stu-id="96395-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96395-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="96395-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="96395-107">[in]プロセスへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="96395-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="96395-108">[out]メソッドの正常完了時にバージョン番号の文字列を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="96395-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="96395-109">[in]バージョンのバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="96395-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="96395-110">[out]バージョン番号の文字列の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="96395-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96395-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="96395-111">Return Value</span></span>  
 <span data-ttu-id="96395-112">このメソッドは、次の値に加え、WinError.h で定義されている標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="96395-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="96395-113">リターン コード</span><span class="sxs-lookup"><span data-stu-id="96395-113">Return code</span></span>|<span data-ttu-id="96395-114">説明</span><span class="sxs-lookup"><span data-stu-id="96395-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="96395-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="96395-115">S_OK</span></span>|<span data-ttu-id="96395-116">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="96395-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="96395-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="96395-117">E_INVALIDARG</span></span>|<span data-ttu-id="96395-118">`pVersion`null と`cchBuffer`が null でないまたはその逆です。</span><span class="sxs-lookup"><span data-stu-id="96395-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="96395-119">- または -</span><span class="sxs-lookup"><span data-stu-id="96395-119">-or-</span></span><br /><br /> <span data-ttu-id="96395-120">`hProcess`プロセスに有効なハンドルではありません。</span><span class="sxs-lookup"><span data-stu-id="96395-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="96395-121">- または -</span><span class="sxs-lookup"><span data-stu-id="96395-121">-or-</span></span><br /><br /> <span data-ttu-id="96395-122">CLR が読み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="96395-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="96395-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="96395-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="96395-124">`cchBuffer`null またはバージョン文字列の長さよりも小さいです。</span><span class="sxs-lookup"><span data-stu-id="96395-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="96395-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="96395-125">E_NOTIMPL</span></span>|<span data-ttu-id="96395-126">このメソッドでは、Microsoft Windows 95、Windows 98、または Microsoft Windows Millennium Edition オペレーティング システムで使用できません。</span><span class="sxs-lookup"><span data-stu-id="96395-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="96395-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="96395-127">Requirements</span></span>  
 <span data-ttu-id="96395-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="96395-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96395-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="96395-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="96395-130">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="96395-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96395-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96395-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96395-132">参照</span><span class="sxs-lookup"><span data-stu-id="96395-132">See Also</span></span>  
 [<span data-ttu-id="96395-133">GetRequestedRuntimeInfo 関数</span><span class="sxs-lookup"><span data-stu-id="96395-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [<span data-ttu-id="96395-134">GetRequestedRuntimeVersion 関数</span><span class="sxs-lookup"><span data-stu-id="96395-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [<span data-ttu-id="96395-135">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="96395-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
