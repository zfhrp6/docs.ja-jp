---
title: "LoadStringRCEx 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadStringRCEx
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: LoadStringRCEx
helpviewer_keywords: LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b046387b5ae365ece694509b302f7ac3a7e066a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="8035e-102">LoadStringRCEx 関数</span><span class="sxs-lookup"><span data-stu-id="8035e-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="8035e-103">HRESULT 値を、指定したカルチャの適切なエラー メッセージに変換します。</span><span class="sxs-lookup"><span data-stu-id="8035e-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="8035e-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="8035e-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8035e-105">構文</span><span class="sxs-lookup"><span data-stu-id="8035e-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,   
    [in]  UINT    iResouceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet,   
    [out] int    *pcwchUsed  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8035e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8035e-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="8035e-107">[in]カルチャ識別子です。</span><span class="sxs-lookup"><span data-stu-id="8035e-107">[in] A culture identifier.</span></span> <span data-ttu-id="8035e-108">場合、-1 を渡します`lcid`の既定のカルチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="8035e-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="8035e-109">[in]HRESULT。</span><span class="sxs-lookup"><span data-stu-id="8035e-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="8035e-110">[out]正常完了時にエラー メッセージを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="8035e-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="8035e-111">[in]エラー メッセージ バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="8035e-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="8035e-112">[in]無視されます。</span><span class="sxs-lookup"><span data-stu-id="8035e-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="8035e-113">[out]エラー メッセージの長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8035e-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8035e-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="8035e-114">Return Value</span></span>  
 <span data-ttu-id="8035e-115">このメソッドは、次の値に加え、WinError.h で定義されている標準の COM エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="8035e-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="8035e-116">リターン コード</span><span class="sxs-lookup"><span data-stu-id="8035e-116">Return code</span></span>|<span data-ttu-id="8035e-117">説明</span><span class="sxs-lookup"><span data-stu-id="8035e-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="8035e-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="8035e-118">S_OK</span></span>|<span data-ttu-id="8035e-119">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="8035e-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="8035e-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8035e-120">E_INVALIDARG</span></span>|<span data-ttu-id="8035e-121">`szBuffer`null、または`iMax`はゼロ (0) です。</span><span class="sxs-lookup"><span data-stu-id="8035e-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8035e-122">コメント</span><span class="sxs-lookup"><span data-stu-id="8035e-122">Remarks</span></span>  
 <span data-ttu-id="8035e-123">メソッドが正常に完了しない場合`szBuffer`空の文字列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8035e-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8035e-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="8035e-124">Requirements</span></span>  
 <span data-ttu-id="8035e-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8035e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8035e-126">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8035e-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8035e-127">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8035e-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8035e-128">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8035e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8035e-129">参照</span><span class="sxs-lookup"><span data-stu-id="8035e-129">See Also</span></span>  
 <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="8035e-130">LoadStringRC 関数</span><span class="sxs-lookup"><span data-stu-id="8035e-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 [<span data-ttu-id="8035e-131">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="8035e-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
