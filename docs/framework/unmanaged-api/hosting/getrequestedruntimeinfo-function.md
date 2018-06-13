---
title: GetRequestedRuntimeInfo 関数
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f37be8e3d2e92147e9f13954ab64396062ade2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434982"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo 関数
アプリケーションによって要求された共通言語ランタイム (CLR) のバージョンとのディレクトリ情報を取得します。  
  
 この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,   
    [in]  LPCWSTR  pwszVersion,   
    [in]  LPCWSTR  pConfigurationFile,   
    [in]  DWORD    startupFlags,   
    [in]  DWORD    runtimeInfoFlags,   
    [out] LPWSTR   pDirectory,   
    [in]  DWORD    dwDirectory,   
    [out] DWORD   *dwDirectoryLength,   
    [out] LPWSTR   pVersion,   
    [in]  DWORD    cchBuffer,   
    [out] DWORD   *dwlength  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pExe`  
 [in]アプリケーションの名前。  
  
 `pwszVersion`  
 [in]ランタイムのバージョン番号を指定する文字列。  
  
 `pConfigurationFile`  
 [in]関連付けられている構成ファイルの名前`pExe`です。  
  
 `startupFlags`  
 [in]1 つ以上の[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列挙値。  
  
 `runtimeInfoFlags`  
 [in]1 つ以上の[RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)列挙値。  
  
 `pDirectory`  
 [out]正常完了時にランタイムへのディレクトリ パスを格納するバッファー。  
  
 `dwDirectory`  
 [in]ディレクトリのバッファーの長さ。  
  
 `dwDirectoryLength`  
 [out]ディレクトリのパス文字列の長さへのポインター。  
  
 `pVersion`  
 [out]正常完了時にランタイムのバージョン番号を格納するバッファー。  
  
 `cchBuffer`  
 [in]バージョン文字列バッファーの長さ。  
  
 `dwlength`  
 [out]バージョン文字列の長さへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の値に加え、WinError.h で定義されている標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|ERROR_INSUFFICIENT_BUFFER|ディレクトリ バッファーは、ディレクトリ パスを格納するのに十分な大きさではありません。<br /><br /> または<br /><br /> バージョン バッファーは、バージョン文字列を保存するのに十分な大きさではありません。|  
  
## <a name="remarks"></a>コメント  
 `GetRequestedRuntimeInfo`メソッドは、必ずしもコンピューターにインストールされている最新バージョンではないと、プロセスに読み込まれるバージョンのランタイム情報を返します。  
  
 .NET Framework version 2.0 を使用してインストールされている最新のバージョンに関する情報を取得できます、`GetRequestedRuntimeInfo`メソッドを次のようにします。  
  
-   指定して、 `pExe`、 `pwszVersion`、および`pConfigurationFile`null として使用されるパラメーター。  
  
-   RUNTIME_INFO_UPGRADE_VERSION フラグを指定、`RUNTIME_INFO_FLAGS`の列挙体、`runtimeInfoFlags`パラメーター。  
  
 `GetRequestedRuntimeInfo`メソッドでは、次のような状況では、最新の CLR バージョンは返しません。  
  
-   特定の CLR バージョンを読み込むように指定するアプリケーション構成ファイルが存在します。 Null を指定した場合でも、.NET Framework が構成ファイルを使用ことに注意してください、`pConfigurationFile`パラメーター。  
  
-   [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) CLR の以前のバージョンを指定するメソッドが呼び出されました。  
  
-   以前のバージョンの CLR 用にコンパイルされたアプリケーションは現在実行中です。  
  
 `runtimeInfoFlags`パラメーターを指定できますのみ定数のいずれかのアーキテクチャの`RUNTIME_INFO_FLAGS`一度に列挙します。  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [GetRequestedRuntimeVersion 関数](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [GetVersionFromProcess 関数](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
