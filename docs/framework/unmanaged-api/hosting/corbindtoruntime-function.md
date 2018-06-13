---
title: CorBindToRuntime 関数
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36b15c607026ea9ce583ecda02bcb8ac43900310
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435752"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="9ba2c-102">CorBindToRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="9ba2c-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="9ba2c-103">アンマネージ ホストが共通言語ランタイム (CLR: Common Language Runtime) をプロセスに読み込むことを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="9ba2c-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ba2c-105">構文</span><span class="sxs-lookup"><span data-stu-id="9ba2c-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ba2c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ba2c-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="9ba2c-107">[入力] 読み込む CLR のバージョンを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="9ba2c-108">.NET Framework のバージョン番号はピリオドで区切られた 4 つの部分で構成されています: *major.minor.build.revision*です。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="9ba2c-109">`pwszVersion` として渡される文字列は、文字 "v" で始まり、バージョン番号の最初の 3 つの部分がその後に続く必要があります (たとえば "v1.0.1529")。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="9ba2c-110">いくつかのバージョンの CLR は、以前のバージョンの CLR との互換性を指定するポリシー ステートメントと共にインストールされています。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="9ba2c-111">既定では、スタートアップ shim により、ポリシー ステートメントに対して `pwszVersion` が評価され、要求されたバージョンと互換性がある最新バージョンのランタイムが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="9ba2c-112">ホストは shim に対し、次に示すように `pwszVersion` パラメーターで値 `STARTUP_LOADER_SAFEMODE` を渡すことにより、ポリシー評価を省略し、`flags` で指定されたバージョンとまったく同じバージョンを読み込ませることができます。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="9ba2c-113">呼び出し元が null を指定する場合`pwszVersion`ランタイムの最新バージョンが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="9ba2c-114">Null を渡すことに制御ホストありませんするランタイムのバージョンが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="9ba2c-115">状況によってはこのような方法が適切なこともありますが、読み込むバージョンを特定させておくことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="9ba2c-116">[入力] CLR のサーバー ビルドまたはワークステーション ビルドのどちらを読み込むかを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="9ba2c-117">有効値は `svr` または `wks` です。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="9ba2c-118">ワークステーション ビルドはシングルプロセッサ コンピューターでクライアント アプリケーションを実行するために最適化され、サーバー ビルドはガベージ コレクションでマルチ プロセッサを利用するために最適化されています。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="9ba2c-119">場合`pwszBuildFlavor`に設定されている null の場合、ワークステーション ビルドが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="9ba2c-120">シングル プロセッサ コンピューターで実行されている、ときにワークステーション ビルド常に読み込まれると、場合でも`pwszBuildFlavor`に設定されている`svr`です。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="9ba2c-121">ただし場合、`pwszBuildFlavor`に設定されている`svr`同時実行ガベージ コレクションを指定し、(の説明を参照して、`flags`パラメーター)、サーバー ビルドが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="9ba2c-122">[in]`CLSID`を実装するいずれかのコクラスの[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)または[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="9ba2c-123">サポートされている値は CLSID_CorRuntimeHost と CLSID_CLRRuntimeHost です。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="9ba2c-124">[入力] 要求された `IID` のインターフェイスの `rclsid`。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="9ba2c-125">サポートされている値は IID_ICorRuntimeHost と IID_ICLRRuntimeHost です。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="9ba2c-126">[出力] 返された `riid` へのインターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ba2c-127">コメント</span><span class="sxs-lookup"><span data-stu-id="9ba2c-127">Remarks</span></span>  
 <span data-ttu-id="9ba2c-128">`pwszVersion` で指定したランタイムのバージョンが存在しない場合は、`CorBindToRuntimeEx` は CLR_E_SHIM_RUNTIMELOAD の HRESULT 値を返します。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="9ba2c-129">Windows ID の実行コンテキストとフロー</span><span class="sxs-lookup"><span data-stu-id="9ba2c-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="9ba2c-130">CLR のバージョン 1 では、<xref:System.Security.Principal.WindowsIdentity> オブジェクトは、新しいスレッド、スレッド プール、タイマー コールバックなどの非同期ポイント間をフローしません。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="9ba2c-131">CLR のバージョン 2.0 では、<xref:System.Threading.ExecutionContext> オブジェクトは現在実行しているスレッドに関する情報をラップして非同期ポイント間をフローしますが、アプリケーション ドメインの境界を越えることはありません。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="9ba2c-132">同様に、<xref:System.Security.Principal.WindowsIdentity> オブジェクトもすべての非同期ポイント間をフローします。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="9ba2c-133">したがって、現在スレッドに偽装がある場合は、その偽装もフローします。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="9ba2c-134">2 つの方法のいずれかでフローを変更できます。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-134">You can alter the flow in two ways:</span></span>  
  
1.  <span data-ttu-id="9ba2c-135"><xref:System.Threading.ExecutionContext> 設定を変更し、スレッド単位ではフローしないようにします (<xref:System.Threading.ExecutionContext.SuppressFlow%2A>、<xref:System.Security.SecurityContext.SuppressFlow%2A>、および <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> の各メソッドを参照)。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2.  <span data-ttu-id="9ba2c-136">処理の既定のモードを、現在のスレッドの <xref:System.Security.Principal.WindowsIdentity> 設定がどの状態でも <xref:System.Threading.ExecutionContext> オブジェクトは非同期ポイント間をフローしない、バージョン 1 互換モードに変更します。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="9ba2c-137">既定のモードを変更する方法は、CLR を読み込むときにマネージ実行可能ファイルを使用するか、アンマネージ ホスト インターフェイスを使用するかに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1.  <span data-ttu-id="9ba2c-138">設定する必要があります、マネージ実行可能ファイル、`enabled`の属性、 [ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)要素を`true`です。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2.  <span data-ttu-id="9ba2c-139">アンマネージ ホスト インターフェイスを使用する場合は、`STARTUP_LEGACY_IMPERSONATION` 関数を呼び出すときの `flags` パラメーターに `CorBindToRuntimeEx` フラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="9ba2c-140">バージョン 1 互換モードは、その処理全体および処理のすべてのアプリケーション ドメインに適用されます。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ba2c-141">コメント</span><span class="sxs-lookup"><span data-stu-id="9ba2c-141">Remarks</span></span>  
 <span data-ttu-id="9ba2c-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)と`CorBindToRuntime`、同じ操作を実行しますが、`CorBindToRuntimeEx`関数では、CLR の動作を指定するフラグを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ba2c-143">要件</span><span class="sxs-lookup"><span data-stu-id="9ba2c-143">Requirements</span></span>  
 <span data-ttu-id="9ba2c-144">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ba2c-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ba2c-145">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ba2c-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ba2c-146">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ba2c-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ba2c-147">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ba2c-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba2c-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ba2c-148">See Also</span></span>  
 [<span data-ttu-id="9ba2c-149">CorBindToCurrentRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="9ba2c-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="9ba2c-150">CorBindToRuntimeByCfg 関数</span><span class="sxs-lookup"><span data-stu-id="9ba2c-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="9ba2c-151">CorBindToRuntimeEx 関数</span><span class="sxs-lookup"><span data-stu-id="9ba2c-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="9ba2c-152">CorBindToRuntimeHost 関数</span><span class="sxs-lookup"><span data-stu-id="9ba2c-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="9ba2c-153">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ba2c-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 <span data-ttu-id="9ba2c-154">
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span><span class="sxs-lookup"><span data-stu-id="9ba2c-154">[Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span></span>
