---
title: ICLRDebugging::OpenVirtualProcess メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51b5a9ecd85f0d40ac2fe2826cbbe7a56a6228d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408253"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>ICLRDebugging::OpenVirtualProcess メソッド
プロセスに読み込まれている共通言語ランタイム (CLR) モジュールに対応する ICorDebugProcess インターフェイスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `moduleBaseAddress`  
 [in]ターゲット プロセスのモジュールのベース アドレス。 COR_E_NOT_CLR が、指定されたモジュールが CLR モジュールではない場合に返されます。  
  
 `pDataTarget`  
 [in]データ ターゲットの抽象化により、マネージ デバッガーをプロセスの状態を検査します。 デバッガーを実装する必要があります、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)インターフェイスです。 実装する必要があります、 [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)ここでは、デバッグ中、CLR がインストールされていないローカル コンピューター上のシナリオをサポートするインターフェイスです。  
  
 `pLibraryProvider`  
 [in]ライブラリ プロバイダー コールバック インターフェイスを上にロードし、要求時にデバッグ ライブラリのバージョンに固有です。 このパラメーターは必要な場合にのみ`ppProcess`または`pFlags`は`null`します。  
  
 `pMaxDebuggerSupportedVersion`  
 [in]このデバッガーをデバッグできる CLR の最高のバージョン。 メジャー、マイナー、を指定して、このデバッガーをサポートする最新の CLR バージョンからのバージョンをビルドしリビジョン番号を将来のインプレース CLR サービス リリースに合わせて 65535 に設定する必要があります。  
  
 `riidProcess`  
 [in]取得する ICorDebugProcess インターフェイスの ID。 現時点では、可能な値は、IID_CORDEBUGPROCESS3、IID_CORDEBUGPROCESS2、IID_CORDEBUGPROCESS です。  
  
 `ppProcess`  
 [out]によって識別される COM インターフェイスへのポインター`riidProcess`です。  
  
 `pVersion`  
 [入力、出力].CLR のバージョン。 この値は、入力で`null`です。 指していることも、 [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)構造体、その場合は、構造体の`wStructVersion`0 (ゼロ) にフィールドを初期化する必要があります。  
  
 出力では、返された`CLR_DEBUGGING_VERSION`構造体は、CLR のバージョン情報を使用して入力されます。  
  
 `pdwFlags`  
 [out]指定したランタイムの概要情報のフラグです。 参照してください、 [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)フラグの詳細についてはトピックです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_POINTER|`pDataTarget` は `null` です。|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)コールバックがエラーを返しますまたは、有効なハンドルは提供されません。|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget` このバージョンのランタイムの必要なデータ ターゲットのインターフェイスを実装しません。|  
|CORDBG_E_NOT_CLR|指定されたモジュールが CLR モジュールではありません。 メモリが破損している、モジュールが使用できないか、CLR バージョン shim バージョンより新しいために、CLR モジュールを検出できない場合にも、この HRESULT が返されます。|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|このランタイムのバージョンは、このデバッグ モデルをサポートしていません。 現在、デバッグ モデルは前に、のバージョンの CLR でサポートされていません、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。 `pwszVersion`出力パラメーターが設定されている適切な値にこのエラーが発生後します。|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|CLR のバージョンは、このデバッガーでサポートされるバージョンを超えています。 `pwszVersion`出力パラメーターが設定されている適切な値にこのエラーが発生後します。|  
|E_NO_INTERFACE|`riidProcess`インターフェイスは利用できません。|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|`CLR_DEBUGGING_VERSION`構造に認識されている値を持たない`wStructVersion`です。 この時点でのみ指定できる値は 0 です。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>コメント  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
