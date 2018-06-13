---
title: ICLRRuntimeInfo::IsStarted メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8934a2a51ea4bc86166bf99a6087124d03ab11d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434117"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="ee269-102">ICLRRuntimeInfo::IsStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="ee269-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="ee269-103">ランタイムが開始されているかどうかを示す (つまり、かどうか、 [iclrruntimehost::start メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)が呼び出されは成功しました)。</span><span class="sxs-lookup"><span data-stu-id="ee269-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee269-104">構文</span><span class="sxs-lookup"><span data-stu-id="ee269-104">Syntax</span></span>  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee269-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ee269-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="ee269-106">[out]`true`このランタイムが開始された、それ以外の場合は`false`します。</span><span class="sxs-lookup"><span data-stu-id="ee269-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="ee269-107">[out]ランタイムの起動に使用されたフラグを返します。</span><span class="sxs-lookup"><span data-stu-id="ee269-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee269-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="ee269-108">Return Value</span></span>  
 <span data-ttu-id="ee269-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="ee269-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ee269-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ee269-110">HRESULT</span></span>|<span data-ttu-id="ee269-111">説明</span><span class="sxs-lookup"><span data-stu-id="ee269-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ee269-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ee269-112">S_OK</span></span>|<span data-ttu-id="ee269-113">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="ee269-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="ee269-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="ee269-114">E_NOTIMPL</span></span>|<span data-ttu-id="ee269-115">共通言語ランタイム (CLR) のバージョンよりも前で CLR のバージョン、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="ee269-115">The common language runtime (CLR) version is earlier than the CLR version in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee269-116">コメント</span><span class="sxs-lookup"><span data-stu-id="ee269-116">Remarks</span></span>  
 <span data-ttu-id="ee269-117">このメソッドでは機能しません CLR のバージョンで CLR のバージョンより前、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="ee269-117">This method does not work with CLR versions earlier than the CLR version in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee269-118">要件</span><span class="sxs-lookup"><span data-stu-id="ee269-118">Requirements</span></span>  
 <span data-ttu-id="ee269-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ee269-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee269-120">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ee269-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ee269-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ee269-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee269-122">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee269-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee269-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee269-123">See Also</span></span>  
 [<span data-ttu-id="ee269-124">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee269-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="ee269-125">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee269-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="ee269-126">ホスティング</span><span class="sxs-lookup"><span data-stu-id="ee269-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
