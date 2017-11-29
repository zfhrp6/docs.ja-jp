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
ms.openlocfilehash: 3467ebcd0b821c2313f3535c5b594ef664546e4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="9309a-102">LoadStringRCEx 関数</span><span class="sxs-lookup"><span data-stu-id="9309a-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="9309a-103">HRESULT 値を、指定したカルチャの適切なエラー メッセージに変換します。</span><span class="sxs-lookup"><span data-stu-id="9309a-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="9309a-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="9309a-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9309a-105">構文</span><span class="sxs-lookup"><span data-stu-id="9309a-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="9309a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9309a-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="9309a-107">[in]カルチャ識別子です。</span><span class="sxs-lookup"><span data-stu-id="9309a-107">[in] A culture identifier.</span></span> <span data-ttu-id="9309a-108">場合、-1 を渡します`lcid`の既定のカルチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="9309a-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="9309a-109">[in]HRESULT。</span><span class="sxs-lookup"><span data-stu-id="9309a-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="9309a-110">[out]正常完了時にエラー メッセージを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="9309a-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="9309a-111">[in]エラー メッセージ バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="9309a-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="9309a-112">[in]無視されます。</span><span class="sxs-lookup"><span data-stu-id="9309a-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="9309a-113">[out]エラー メッセージの長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9309a-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9309a-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="9309a-114">Return Value</span></span>  
 <span data-ttu-id="9309a-115">このメソッドは、次の値に加え、WinError.h で定義されている標準の COM エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="9309a-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="9309a-116">リターン コード</span><span class="sxs-lookup"><span data-stu-id="9309a-116">Return code</span></span>|<span data-ttu-id="9309a-117">説明</span><span class="sxs-lookup"><span data-stu-id="9309a-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="9309a-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="9309a-118">S_OK</span></span>|<span data-ttu-id="9309a-119">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="9309a-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="9309a-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9309a-120">E_INVALIDARG</span></span>|<span data-ttu-id="9309a-121">`szBuffer`null、または`iMax`はゼロ (0) です。</span><span class="sxs-lookup"><span data-stu-id="9309a-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9309a-122">コメント</span><span class="sxs-lookup"><span data-stu-id="9309a-122">Remarks</span></span>  
 <span data-ttu-id="9309a-123">メソッドが正常に完了しない場合`szBuffer`空の文字列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9309a-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9309a-124">要件</span><span class="sxs-lookup"><span data-stu-id="9309a-124">Requirements</span></span>  
 <span data-ttu-id="9309a-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9309a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9309a-126">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9309a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9309a-127">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9309a-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9309a-128">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9309a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9309a-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="9309a-129">See Also</span></span>  
 <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="9309a-130">LoadStringRC 関数</span><span class="sxs-lookup"><span data-stu-id="9309a-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 [<span data-ttu-id="9309a-131">推奨されなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="9309a-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
