---
title: "ICorDebugRemote::CreateProcessEx メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemote.CreateProcessEx
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 00709ffe4695ea0b56982cb60df15c2991b49d4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremotecreateprocessex-method"></a>ICorDebugRemote::CreateProcessEx メソッド
デバッガーの下でリモート コンピューター上のプロセスを起動します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRemoteTarget`  
 [in]ポインター、 [ICorDebugRemoteTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)です。 プロセスを起動するリモート コンピューターを決定するために使用します。  
  
 `lpApplicationName`  
 [in]実行中のプロセスによって実行されるモジュールを指定する null で終わる文字列へのポインター。 モジュールは、呼び出し元のプロセスのセキュリティ コンテキストで実行されます。  
  
 `lpCommandLine`  
 [in]実行中のプロセスによって実行されるコマンドラインを指定する null で終わる文字列へのポインター。  
  
 `lpProcessAttributes`  
 [in]リモート デバッグは使用しません。  
  
 `lpThreadAttributes`  
 [in]リモート デバッグは使用しません。  
  
 `bInheritHandles`  
 [in]リモート デバッグは使用しません。  
  
 `dwCreationFlags`  
 [in]リモート デバッグは使用しません。  
  
 `lpEnvironment`  
 [in]新しいプロセスの環境ブロックへのポインター。  
  
 `lpCurrentDirectory`  
 [in]プロセスの現在のディレクトリへの完全パスを指定する null で終わる文字列へのポインター。 このパラメーターが null の場合、新しいプロセスは、呼び出し元プロセスとして同じ現在のドライブとディレクトリがあります。  
  
 `lpStartupInfo`  
 [in]リモート デバッグは使用しません。  
  
 `lpProcessInformation`  
 [in]リモート デバッグは使用しません。  
  
 `debuggingFlags`  
 [in]リモート デバッグは使用しません。  
  
 `ppProcess`  
 [out]プロセスを表す「ICorDebugProcess インターフェイス」オブジェクトのアドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 正常にデバッグするため、リモート コンピューターと返される「ICorDebugProcess インターフェイス」上のプロセスを起動します。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 リモート コンピューター上のプロセスを起動し、デバッグに「ICorDebugProcess インターフェイス」を返すことができません。  
  
## <a name="remarks"></a>コメント  
 混合モード デバッグは Silverlight ではサポートされていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 4.5、4、3.5 SP1  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugRemote インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
