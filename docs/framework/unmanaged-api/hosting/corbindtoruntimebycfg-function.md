---
title: "CorBindToRuntimeByCfg 関数"
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
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2dccd777ef20f68d091cfdd7939c57a1f8d42ad5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="3153a-102">CorBindToRuntimeByCfg 関数</span><span class="sxs-lookup"><span data-stu-id="3153a-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="3153a-103">共通言語ランタイム (CLR) を XML ファイルから読み取られたバージョン情報を使用して、プロセスに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="3153a-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="3153a-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="3153a-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3153a-105">構文</span><span class="sxs-lookup"><span data-stu-id="3153a-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,   
    [out] LPVOID FAR*  ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3153a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3153a-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="3153a-107">[in]ポインター、`IStream`を XML ファイルを読み込むオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3153a-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="3153a-108">[in]将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="3153a-108">[in] Reserved for future use.</span></span> <span data-ttu-id="3153a-109">値として 0 (ゼロ) を使用します。</span><span class="sxs-lookup"><span data-stu-id="3153a-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="3153a-110">[in]値、 [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) CLR の起動時の動作を指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="3153a-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="3153a-111">[in]`CLSID`を実装するいずれかのコクラスの[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)または[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3153a-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="3153a-112">サポートされている値は CLSID_CorRuntimeHost と CLSID_CLRRuntimeHost です。</span><span class="sxs-lookup"><span data-stu-id="3153a-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="3153a-113">[in]`IID`いずれかの`ICorRuntimeHost`または`ICLRRuntimeHost`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3153a-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="3153a-114">サポートされている値は IID_ICorRuntimeHost と IID_ICLRRuntimeHost です。</span><span class="sxs-lookup"><span data-stu-id="3153a-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="3153a-115">[out]返されるインターフェイスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3153a-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3153a-116">コメント</span><span class="sxs-lookup"><span data-stu-id="3153a-116">Remarks</span></span>  
 <span data-ttu-id="3153a-117">XML ファイルの形式は、標準的なアプリケーション構成ファイルの後にモデル化されます。</span><span class="sxs-lookup"><span data-stu-id="3153a-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="3153a-118">XML ファイルの詳細については、次を参照してください。[構成ファイル スキーマ](../../../../docs/framework/configure-apps/file-schema/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="3153a-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3153a-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="3153a-119">Requirements</span></span>  
 <span data-ttu-id="3153a-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3153a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3153a-121">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3153a-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3153a-122">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3153a-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3153a-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3153a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3153a-124">参照</span><span class="sxs-lookup"><span data-stu-id="3153a-124">See Also</span></span>  
 [<span data-ttu-id="3153a-125">CorBindToCurrentRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="3153a-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="3153a-126">CorBindToRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="3153a-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="3153a-127">CorBindToRuntimeEx 関数</span><span class="sxs-lookup"><span data-stu-id="3153a-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="3153a-128">CorBindToRuntimeHost 関数</span><span class="sxs-lookup"><span data-stu-id="3153a-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="3153a-129">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3153a-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="3153a-130">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="3153a-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
