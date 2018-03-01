---
title: "METAHOST_POLICY_FLAGS 列挙体"
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
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 80abed08cc7659d4218dce445be81481bb5a665b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="metahostpolicyflags-enumeration"></a><span data-ttu-id="8e14e-102">METAHOST_POLICY_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="8e14e-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="8e14e-103">ほとんどのランタイム ホストに共通するバインディング ポリシーを提供します。</span><span class="sxs-lookup"><span data-stu-id="8e14e-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="8e14e-104">この列挙体を使って、 [iclrmetahostpolicy::getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8e14e-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e14e-105">構文</span><span class="sxs-lookup"><span data-stu-id="8e14e-105">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="8e14e-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="8e14e-106">Members</span></span>  
  
|<span data-ttu-id="8e14e-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="8e14e-107">Member</span></span>|<span data-ttu-id="8e14e-108">説明</span><span class="sxs-lookup"><span data-stu-id="8e14e-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="8e14e-109">共通言語ランタイム (CLR) は、現在のプロセスに読み込まれると見なしません、高いレベルの互換性ポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="8e14e-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="8e14e-110">代わりに、見なしますインストール済みの Clr のみと、コンポーネントの基本設定アセンブリ ファイル自体、宣言されたビルド対象のバージョン、または構成ファイルから派生したとして。</span><span class="sxs-lookup"><span data-stu-id="8e14e-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="8e14e-111">厳密な一致が見つからない場合に、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft の内容に基づいて、バージョン バインドの結果にアップグレード ポリシーを適用\\です。NETFramework\Policy\Upgrades です。</span><span class="sxs-lookup"><span data-stu-id="8e14e-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="8e14e-112">同じ効果が[RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)です。</span><span class="sxs-lookup"><span data-stu-id="8e14e-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="8e14e-113">呼び出しに提供されたイメージは、新しいプロセスで起動された場合と、バインディングの結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="8e14e-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="8e14e-114">現在、`GetRequestedRuntime`読み込み可能なランタイムのセットを無視し、インストールされているランタイムのセットに対してバインドします。</span><span class="sxs-lookup"><span data-stu-id="8e14e-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="8e14e-115">このフラグを起動するときに、EXE がバインドするランタイムを決定するホストを使用します。</span><span class="sxs-lookup"><span data-stu-id="8e14e-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="8e14e-116">エラー ダイアログ ボックスが表示されます`GetRequestedRuntime`の入力パラメーターに互換性のあるランタイムを検索することはありません。</span><span class="sxs-lookup"><span data-stu-id="8e14e-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="8e14e-117">以降で、 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]、このエラー ダイアログ ボックスは、ユーザーを該当する機能を有効にするかどうかを確認する Windows 機能 ダイアログ ボックスの形式を取ることができます。</span><span class="sxs-lookup"><span data-stu-id="8e14e-117">Beginning with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="8e14e-118">`GetRequestedRuntime`バインディング プロセスに追加の入力としてプロセス イメージ (および対応する構成ファイル) を使用します。</span><span class="sxs-lookup"><span data-stu-id="8e14e-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="8e14e-119">既定では、`GetRequestedRuntime`に切り替えられないプロセス イメージのパス (通常は、プロセスを起動するために使用された EXE) に、ランタイムにバインドを決定する際にします。</span><span class="sxs-lookup"><span data-stu-id="8e14e-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="8e14e-120">`GetRequestedRuntime`情報が、現在の構成ファイルでない場合に適切な SKU がインストールされているかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e14e-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="8e14e-121">これにより、.NET Framework の既定のインストールよりも小さな Sku に正常に失敗する構成ファイルがないアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="8e14e-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="8e14e-122">既定では、 `GetRequestedRuntime` SKU 属性が、構成ファイルで指定されていない限り、適切な SKU がインストールされているかどうかをチェックしません`<supportedRuntime />`要素。</span><span class="sxs-lookup"><span data-stu-id="8e14e-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="8e14e-123">`GetRequestedRuntime`情報が、現在の構成ファイルでない場合に適切な SKU がインストールされているかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e14e-123">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="8e14e-124">これにより、.NET Framework の既定のインストールよりも小さな Sku に正常に失敗する構成ファイルがないアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="8e14e-124">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="8e14e-125">既定では、 `GetRequestedRuntime` SKU 属性が、構成ファイルで指定されていない限り、適切な SKU がインストールされているかどうかをチェックしません`<supportedRuntime />`要素。</span><span class="sxs-lookup"><span data-stu-id="8e14e-125">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="8e14e-126">`GetRequestedRuntime`SEM_FAILCRITICALERRORS を無視する (呼び出すことによって設定される、 [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242)関数)、し、[エラー] ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="8e14e-126">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) function), and show the error dialog box.</span></span> <span data-ttu-id="8e14e-127">既定では、SEM_FAILCRITICALERRORS は、[エラー] ダイアログ ボックスを抑制します。</span><span class="sxs-lookup"><span data-stu-id="8e14e-127">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="8e14e-128">別のプロセスから継承されているし、サイレントのエラーが、シナリオでは望ましくない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8e14e-128">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e14e-129">コメント</span><span class="sxs-lookup"><span data-stu-id="8e14e-129">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e14e-130">必要条件</span><span class="sxs-lookup"><span data-stu-id="8e14e-130">Requirements</span></span>  
 <span data-ttu-id="8e14e-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8e14e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e14e-132">**ヘッダー:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="8e14e-132">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="8e14e-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="8e14e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e14e-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e14e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e14e-135">参照</span><span class="sxs-lookup"><span data-stu-id="8e14e-135">See Also</span></span>  
 [<span data-ttu-id="8e14e-136">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="8e14e-136">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="8e14e-137">GetRequestedRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="8e14e-137">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
