---
title: "LoadStringRC 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadStringRC
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: LoadStringRC
helpviewer_keywords: LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc93adf575af7f2803b20f24a3261a447772ffd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="loadstringrc-function"></a><span data-ttu-id="b6bc3-102">LoadStringRC 関数</span><span class="sxs-lookup"><span data-stu-id="b6bc3-102">LoadStringRC Function</span></span>
<span data-ttu-id="b6bc3-103">現在のスレッドの既定のカルチャを使用して、HRESULT 値をエラー メッセージに変換します。</span><span class="sxs-lookup"><span data-stu-id="b6bc3-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="b6bc3-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="b6bc3-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6bc3-105">構文</span><span class="sxs-lookup"><span data-stu-id="b6bc3-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6bc3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b6bc3-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="b6bc3-107">[in]HRESULT。</span><span class="sxs-lookup"><span data-stu-id="b6bc3-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="b6bc3-108">[out]正常完了時にエラー メッセージを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="b6bc3-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="b6bc3-109">[in]エラー メッセージ バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="b6bc3-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="b6bc3-110">[in]無視されます。</span><span class="sxs-lookup"><span data-stu-id="b6bc3-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6bc3-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="b6bc3-111">Return Value</span></span>  
 <span data-ttu-id="b6bc3-112">このメソッドは、次の値に加え、WinError.h で定義されている標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="b6bc3-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="b6bc3-113">リターン コード</span><span class="sxs-lookup"><span data-stu-id="b6bc3-113">Return code</span></span>|<span data-ttu-id="b6bc3-114">説明</span><span class="sxs-lookup"><span data-stu-id="b6bc3-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b6bc3-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6bc3-115">S_OK</span></span>|<span data-ttu-id="b6bc3-116">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="b6bc3-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="b6bc3-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b6bc3-117">E_INVALIDARG</span></span>|<span data-ttu-id="b6bc3-118">`szBuffer`null または`iMax`はゼロ (0) です。</span><span class="sxs-lookup"><span data-stu-id="b6bc3-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6bc3-119">コメント</span><span class="sxs-lookup"><span data-stu-id="b6bc3-119">Remarks</span></span>  
 <span data-ttu-id="b6bc3-120">メソッドが正常に完了しない場合`szBuffer`空の文字列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b6bc3-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6bc3-121">要件</span><span class="sxs-lookup"><span data-stu-id="b6bc3-121">Requirements</span></span>  
 <span data-ttu-id="b6bc3-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6bc3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6bc3-123">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b6bc3-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6bc3-124">**ライブラリ:** MSCorEE.dll と Mscorwks.dll です。</span><span class="sxs-lookup"><span data-stu-id="b6bc3-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="b6bc3-125">Mscorwks.dll の代わりに MSCorEE.dll を使用して、正しいバージョンの .NET Framework を対象にすることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b6bc3-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="b6bc3-126">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6bc3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6bc3-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6bc3-127">See Also</span></span>  
 [<span data-ttu-id="b6bc3-128">LoadStringRCEx 関数</span><span class="sxs-lookup"><span data-stu-id="b6bc3-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 [<span data-ttu-id="b6bc3-129">推奨されなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="b6bc3-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
