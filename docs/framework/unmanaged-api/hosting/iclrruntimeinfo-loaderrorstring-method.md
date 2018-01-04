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
ms.workload: dotnet
ms.openlocfilehash: d6253844e931b7b9126b2df28c7977eaa1d92d70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="9ca14-102">ICLRRuntimeInfo::LoadErrorString メソッド</span><span class="sxs-lookup"><span data-stu-id="9ca14-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="9ca14-103">指定されたカルチャに適切なエラー メッセージには、HRESULT 値を変換します。</span><span class="sxs-lookup"><span data-stu-id="9ca14-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="9ca14-104">このメソッドには、次の関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="9ca14-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="9ca14-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="9ca14-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="9ca14-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="9ca14-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="9ca14-107">構文</span><span class="sxs-lookup"><span data-stu-id="9ca14-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ca14-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ca14-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="9ca14-109">[in]変換する HRESULT。</span><span class="sxs-lookup"><span data-stu-id="9ca14-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="9ca14-110">[out]指定された HRESULT に関連付けられているメッセージ文字列。</span><span class="sxs-lookup"><span data-stu-id="9ca14-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="9ca14-111">[入力、出力].サイズ`pwzbuffer`バッファー オーバーランを回避します。</span><span class="sxs-lookup"><span data-stu-id="9ca14-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="9ca14-112">場合`pwzbuffer`が null、`pcchBuffer`の予想サイズは、`pwzbuffer`事前割り当てを許可します。</span><span class="sxs-lookup"><span data-stu-id="9ca14-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="9ca14-113">[in]カルチャ識別子。</span><span class="sxs-lookup"><span data-stu-id="9ca14-113">[in] The culture identifier.</span></span> <span data-ttu-id="9ca14-114">既定のカルチャを使用するのには、-1 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ca14-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ca14-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ca14-115">Return Value</span></span>  
 <span data-ttu-id="9ca14-116">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="9ca14-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9ca14-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ca14-117">HRESULT</span></span>|<span data-ttu-id="9ca14-118">説明</span><span class="sxs-lookup"><span data-stu-id="9ca14-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ca14-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ca14-119">S_OK</span></span>|<span data-ttu-id="9ca14-120">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="9ca14-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="9ca14-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="9ca14-121">E_POINTER</span></span>|<span data-ttu-id="9ca14-122">`pcchBuffer` が null です。</span><span class="sxs-lookup"><span data-stu-id="9ca14-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="9ca14-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9ca14-123">E_INVALIDARG</span></span>|<span data-ttu-id="9ca14-124">`pwzBuffer` が null です。</span><span class="sxs-lookup"><span data-stu-id="9ca14-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ca14-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="9ca14-125">Requirements</span></span>  
 <span data-ttu-id="9ca14-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ca14-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ca14-127">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9ca14-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9ca14-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9ca14-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ca14-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ca14-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca14-130">参照</span><span class="sxs-lookup"><span data-stu-id="9ca14-130">See Also</span></span>  
 [<span data-ttu-id="9ca14-131">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ca14-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="9ca14-132">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ca14-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="9ca14-133">ホスティング</span><span class="sxs-lookup"><span data-stu-id="9ca14-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
