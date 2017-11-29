---
title: "ICLRRuntimeInfo::LoadErrorString メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.LoadErrorString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26fa051e5c4735307edbb443e6615a57190c0ae5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="75140-102">ICLRRuntimeInfo::LoadErrorString メソッド</span><span class="sxs-lookup"><span data-stu-id="75140-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="75140-103">指定されたカルチャに適切なエラー メッセージには、HRESULT 値を変換します。</span><span class="sxs-lookup"><span data-stu-id="75140-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="75140-104">このメソッドには、次の関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="75140-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="75140-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="75140-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="75140-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="75140-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="75140-107">構文</span><span class="sxs-lookup"><span data-stu-id="75140-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75140-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="75140-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="75140-109">[in]変換する HRESULT。</span><span class="sxs-lookup"><span data-stu-id="75140-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="75140-110">[out]指定された HRESULT に関連付けられているメッセージ文字列。</span><span class="sxs-lookup"><span data-stu-id="75140-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="75140-111">[入力、出力].サイズ`pwzbuffer`バッファー オーバーランを回避します。</span><span class="sxs-lookup"><span data-stu-id="75140-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="75140-112">場合`pwzbuffer`が null、`pcchBuffer`の予想サイズは、`pwzbuffer`事前割り当てを許可します。</span><span class="sxs-lookup"><span data-stu-id="75140-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="75140-113">[in]カルチャ識別子。</span><span class="sxs-lookup"><span data-stu-id="75140-113">[in] The culture identifier.</span></span> <span data-ttu-id="75140-114">既定のカルチャを使用するのには、-1 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75140-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75140-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="75140-115">Return Value</span></span>  
 <span data-ttu-id="75140-116">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="75140-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="75140-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="75140-117">HRESULT</span></span>|<span data-ttu-id="75140-118">説明</span><span class="sxs-lookup"><span data-stu-id="75140-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="75140-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="75140-119">S_OK</span></span>|<span data-ttu-id="75140-120">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="75140-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="75140-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="75140-121">E_POINTER</span></span>|<span data-ttu-id="75140-122">`pcchBuffer` が null です。</span><span class="sxs-lookup"><span data-stu-id="75140-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="75140-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="75140-123">E_INVALIDARG</span></span>|<span data-ttu-id="75140-124">`pwzBuffer` が null です。</span><span class="sxs-lookup"><span data-stu-id="75140-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75140-125">要件</span><span class="sxs-lookup"><span data-stu-id="75140-125">Requirements</span></span>  
 <span data-ttu-id="75140-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="75140-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75140-127">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="75140-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="75140-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="75140-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75140-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75140-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75140-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="75140-130">See Also</span></span>  
 [<span data-ttu-id="75140-131">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="75140-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="75140-132">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="75140-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="75140-133">ホスティング</span><span class="sxs-lookup"><span data-stu-id="75140-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
