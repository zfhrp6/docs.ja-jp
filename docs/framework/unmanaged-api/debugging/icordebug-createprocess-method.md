---
title: ICorDebug::CreateProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 044f94a567dc4bc2b169ba2a5f2a5d7b4f98e516
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess メソッド
プロセスと、デバッガーの制御下で、プライマリ スレッドが起動します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateProcess (  
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
    [out] ICorDebugProcess            **ppProcess  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `lpApplicationName`  
 [in]実行中のプロセスによって実行されるモジュールを指定する null で終わる文字列へのポインター。 モジュールは、呼び出し元のプロセスのセキュリティ コンテキストで実行されます。  
  
 `lpCommandLine`  
 [in]実行中のプロセスによって実行されるコマンドラインを指定する null で終わる文字列へのポインター。 アプリケーション名 (たとえば、"SomeApp.exe") は、最初の引数である必要があります。  
  
 `lpProcessAttributes`  
 [in]Win32 へのポインター`SECURITY_ATTRIBUTES`をプロセスのセキュリティ記述子を指定します。 場合`lpProcessAttributes`は null、既定のセキュリティ記述子は、プロセスを取得します。  
  
 `lpThreadAttributes`  
 [in]Win32 へのポインター`SECURITY_ATTRIBUTES`をプロセスのプライマリ スレッドのセキュリティ記述子を指定します。 場合`lpThreadAttributes`は null、既定のセキュリティ記述子は、スレッドを取得します。  
  
 `bInheritHandles`  
 [in]設定`true`呼び出し元のプロセスで継承可能な各ハンドルが、実行中のプロセスによって継承されたことを示すために、または`false`ハンドルを継承しないことを示すためにします。 継承されたハンドルは、元のハンドルと同じ値とアクセス権限を持っています。  
  
 `dwCreationFlags`  
 [in]ビットごとの組み合わせ、 [Win32 プロセス作成フラグ](http://go.microsoft.com/fwlink/?linkid=69981)優先順位クラスと実行中のプロセスの動作を制御します。  
  
 `lpEnvironment`  
 [in]新しいプロセスの環境ブロックへのポインター。  
  
 `lpCurrentDirectory`  
 [in]プロセスの現在のディレクトリへの完全パスを指定する null で終わる文字列へのポインター。 このパラメーターが null の場合、新しいプロセスは、呼び出し元プロセスとして同じ現在のドライブとディレクトリがあります。  
  
 `lpStartupInfo`  
 [in]Win32 へのポインター`STARTUPINFOW`ウィンドウ ステーション、デスクトップ、標準のハンドル、および実行中のプロセスのメイン ウィンドウの外観を指定します。  
  
 `lpProcessInformation`  
 [in]Win32 へのポインター`PROCESS_INFORMATION`を起動するプロセスに関する識別情報を指定します。  
  
 `debuggingFlags`  
 [in]デバッグ オプションを指定する CorDebugCreateProcessFlags 列挙型の値です。  
  
 `ppProcess`  
 [out]ICorDebugProcess を表す、オブジェクト、プロセスのアドレスへのポインター。  
  
## <a name="remarks"></a>コメント  
 このメソッドのパラメーターは、Win32 のと同じ`CreateProcess`メソッドです。  
  
 アンマネージ混合モード デバッグを有効にするには設定`dwCreationFlags`DEBUG_PROCESS に&#124;DEBUG_ONLY_THIS_PROCESS です。 マネージ デバッグのみを使用する場合は、これらのフラグを設定しないでください。  
  
 デバッガーとプロセスが (アタッチされたプロセス) をデバッグするかどうか、単一のコンソールを共有し、相互運用機能デバッグを使用する場合は、可能であれば接続されているプロセスがコンソールのロックを保持し、デバッグ イベントで停止します。 デバッガーは、コンソールを使用するあらゆる試みをブロックし、されます。 この問題を回避するで防ぐを設定、`dwCreationFlags`パラメーター。  
  
 相互運用機能デバッグは IA 64 ベースおよび AMD64 ベースのプラットフォームなど Win9x と x86 以外のプラットフォームではサポートされていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
