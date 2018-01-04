---
title: "CorBindToCurrentRuntime 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type: HeaderDef
f1_keywords: CorBindToCurrentRuntime
helpviewer_keywords: CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9568d9420c686d5a906fb7f90570fe6a1d12046d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="4bc8a-102">CorBindToCurrentRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="4bc8a-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="4bc8a-103">XML ファイルに格納されているバージョン情報を使用して、共通言語ランタイム (CLR: Common Language Runtime) をプロセスに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="4bc8a-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="4bc8a-104">XML ファイルの形式は、標準的なアプリケーション構成ファイルの後にモデル化されます。</span><span class="sxs-lookup"><span data-stu-id="4bc8a-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="4bc8a-105">構成ファイルの詳細については、「[構成ファイル スキーマ](../../../../docs/framework/configure-apps/file-schema/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bc8a-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="4bc8a-106">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="4bc8a-106">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="4bc8a-107">参照してください[プロセスに、共通言語ランタイムを読み込む](http://msdn.microsoft.com/en-us/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f)します。</span><span class="sxs-lookup"><span data-stu-id="4bc8a-107">See [Loading the Common Language Runtime into a Process](http://msdn.microsoft.com/en-us/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bc8a-108">構文</span><span class="sxs-lookup"><span data-stu-id="4bc8a-108">Syntax</span></span>  
  
```  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4bc8a-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4bc8a-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="4bc8a-110">[in]読み込む CLR のバージョンを指定するアプリケーション構成ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="4bc8a-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="4bc8a-111">ファイル名が完全でない場合、呼び出しを行った実行可能ファイルと同じディレクトリにあると見なされます。</span><span class="sxs-lookup"><span data-stu-id="4bc8a-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="4bc8a-112">読み込むランタイムのバージョンがバージョン属性で説明されている、 [ \<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)構成ファイルの要素。</span><span class="sxs-lookup"><span data-stu-id="4bc8a-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="4bc8a-113">バージョンが指定されていない場合、または場合、`<requiredRuntime>`要素が見つかりません、コンピューターにインストールされている CLR の最新バージョンが読み込まれています。</span><span class="sxs-lookup"><span data-stu-id="4bc8a-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="4bc8a-114">[in]`CLSID`を実装するいずれかのコクラスの[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)または[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="4bc8a-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="4bc8a-115">サポートされている値は CLSID_CorRuntimeHost と CLSID_CLRRuntimeHost です。</span><span class="sxs-lookup"><span data-stu-id="4bc8a-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="4bc8a-116">[入力] 要求するインターフェイスの `IID`。</span><span class="sxs-lookup"><span data-stu-id="4bc8a-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="4bc8a-117">サポートされている値は IID_ICorRuntimeHost と IID_ICLRRuntimeHost です。</span><span class="sxs-lookup"><span data-stu-id="4bc8a-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="4bc8a-118">[out]返されたインターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="4bc8a-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bc8a-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="4bc8a-119">Requirements</span></span>  
 <span data-ttu-id="4bc8a-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4bc8a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bc8a-121">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4bc8a-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4bc8a-122">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4bc8a-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bc8a-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bc8a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bc8a-124">参照</span><span class="sxs-lookup"><span data-stu-id="4bc8a-124">See Also</span></span>  
 [<span data-ttu-id="4bc8a-125">CorBindToRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="4bc8a-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="4bc8a-126">CorBindToRuntimeByCfg 関数</span><span class="sxs-lookup"><span data-stu-id="4bc8a-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="4bc8a-127">CorBindToRuntimeEx 関数</span><span class="sxs-lookup"><span data-stu-id="4bc8a-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="4bc8a-128">CorBindToRuntimeHost 関数</span><span class="sxs-lookup"><span data-stu-id="4bc8a-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="4bc8a-129">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4bc8a-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="4bc8a-130">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="4bc8a-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
