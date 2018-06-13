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
# <a name="corbindtoruntime-function"></a>CorBindToRuntime 関数
アンマネージ ホストが共通言語ランタイム (CLR: Common Language Runtime) をプロセスに読み込むことを有効にします。  
  
 この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pwszVersion`  
 [入力] 読み込む CLR のバージョンを示す文字列。  
  
 .NET Framework のバージョン番号はピリオドで区切られた 4 つの部分で構成されています: *major.minor.build.revision*です。 `pwszVersion` として渡される文字列は、文字 "v" で始まり、バージョン番号の最初の 3 つの部分がその後に続く必要があります (たとえば "v1.0.1529")。  
  
 いくつかのバージョンの CLR は、以前のバージョンの CLR との互換性を指定するポリシー ステートメントと共にインストールされています。 既定では、スタートアップ shim により、ポリシー ステートメントに対して `pwszVersion` が評価され、要求されたバージョンと互換性がある最新バージョンのランタイムが読み込まれます。 ホストは shim に対し、次に示すように `pwszVersion` パラメーターで値 `STARTUP_LOADER_SAFEMODE` を渡すことにより、ポリシー評価を省略し、`flags` で指定されたバージョンとまったく同じバージョンを読み込ませることができます。  
  
 呼び出し元が null を指定する場合`pwszVersion`ランタイムの最新バージョンが読み込まれます。 Null を渡すことに制御ホストありませんするランタイムのバージョンが読み込まれます。 状況によってはこのような方法が適切なこともありますが、読み込むバージョンを特定させておくことを強くお勧めします。  
  
 `pwszBuildFlavor`  
 [入力] CLR のサーバー ビルドまたはワークステーション ビルドのどちらを読み込むかを指定する文字列。 有効値は `svr` または `wks` です。 ワークステーション ビルドはシングルプロセッサ コンピューターでクライアント アプリケーションを実行するために最適化され、サーバー ビルドはガベージ コレクションでマルチ プロセッサを利用するために最適化されています。  
  
 場合`pwszBuildFlavor`に設定されている null の場合、ワークステーション ビルドが読み込まれます。 シングル プロセッサ コンピューターで実行されている、ときにワークステーション ビルド常に読み込まれると、場合でも`pwszBuildFlavor`に設定されている`svr`です。 ただし場合、`pwszBuildFlavor`に設定されている`svr`同時実行ガベージ コレクションを指定し、(の説明を参照して、`flags`パラメーター)、サーバー ビルドが読み込まれます。  
  
 `rclsid`  
 [in]`CLSID`を実装するいずれかのコクラスの[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)または[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)インターフェイスです。 サポートされている値は CLSID_CorRuntimeHost と CLSID_CLRRuntimeHost です。  
  
 `riid`  
 [入力] 要求された `IID` のインターフェイスの `rclsid`。 サポートされている値は IID_ICorRuntimeHost と IID_ICLRRuntimeHost です。  
  
 `ppv`  
 [出力] 返された `riid` へのインターフェイス ポインター。  
  
## <a name="remarks"></a>コメント  
 `pwszVersion` で指定したランタイムのバージョンが存在しない場合は、`CorBindToRuntimeEx` は CLR_E_SHIM_RUNTIMELOAD の HRESULT 値を返します。  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Windows ID の実行コンテキストとフロー  
 CLR のバージョン 1 では、<xref:System.Security.Principal.WindowsIdentity> オブジェクトは、新しいスレッド、スレッド プール、タイマー コールバックなどの非同期ポイント間をフローしません。 CLR のバージョン 2.0 では、<xref:System.Threading.ExecutionContext> オブジェクトは現在実行しているスレッドに関する情報をラップして非同期ポイント間をフローしますが、アプリケーション ドメインの境界を越えることはありません。 同様に、<xref:System.Security.Principal.WindowsIdentity> オブジェクトもすべての非同期ポイント間をフローします。 したがって、現在スレッドに偽装がある場合は、その偽装もフローします。  
  
 2 つの方法のいずれかでフローを変更できます。  
  
1.  <xref:System.Threading.ExecutionContext> 設定を変更し、スレッド単位ではフローしないようにします (<xref:System.Threading.ExecutionContext.SuppressFlow%2A>、<xref:System.Security.SecurityContext.SuppressFlow%2A>、および <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> の各メソッドを参照)。  
  
2.  処理の既定のモードを、現在のスレッドの <xref:System.Security.Principal.WindowsIdentity> 設定がどの状態でも <xref:System.Threading.ExecutionContext> オブジェクトは非同期ポイント間をフローしない、バージョン 1 互換モードに変更します。 既定のモードを変更する方法は、CLR を読み込むときにマネージ実行可能ファイルを使用するか、アンマネージ ホスト インターフェイスを使用するかに応じて異なります。  
  
    1.  設定する必要があります、マネージ実行可能ファイル、`enabled`の属性、 [ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)要素を`true`です。  
  
    2.  アンマネージ ホスト インターフェイスを使用する場合は、`STARTUP_LEGACY_IMPERSONATION` 関数を呼び出すときの `flags` パラメーターに `CorBindToRuntimeEx` フラグを設定します。  
  
     バージョン 1 互換モードは、その処理全体および処理のすべてのアプリケーション ドメインに適用されます。  
  
## <a name="remarks"></a>コメント  
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)と`CorBindToRuntime`、同じ操作を実行しますが、`CorBindToRuntimeEx`関数では、CLR の動作を指定するフラグを設定することができます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [CorBindToCurrentRuntime 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntimeByCfg 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [CorBindToRuntimeEx 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [CorBindToRuntimeHost 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [ICorRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
