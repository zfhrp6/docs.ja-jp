---
title: ICorDebugModule Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule
helpviewer_keywords: ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59c24d8305e71aac01843155b86fb54fb1e1263d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule-interface1"></a>ICorDebugModule Interface1
共通言語ランタイム (CLR) モジュールは、実行可能ファイルかダイナミック リンク ライブラリ (DLL) を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateBreakpoint メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|実装されていません。|  
|[EnableClassLoadCallbacks メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|決定するかどうか、 [icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)と[icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)このモジュールのコールバックが呼び出されます。|  
|[EnableJITDebugging メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|・ イン タイム (JIT) コンパイラがこのモジュール内でメソッドのデバッグ情報を保持するかどうかを判断します。|  
|[GetAssembly メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|このモジュールを含むアセンブリを取得します。|  
|[GetBaseAddress メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|モジュールのベース アドレスを取得します。|  
|[GetClassFromToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|メタデータから、ICorDebugClass を取得します。|  
|[GetEditAndContinueSnapshot メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|使用しないでください。|  
|[GetFunctionFromRVA メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|実装されていません。|  
|[GetFunctionFromToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|メタデータ トークンによって指定された関数を取得します。|  
|[GetGlobalVariableValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|指定のグローバル変数の値のオブジェクトを取得します。|  
|[GetMetaDataInterface メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|モジュールのメタデータの検査に使用できるメタデータ インターフェイス ポインターを取得します。|  
|[GetName メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|モジュールのファイル名を取得します。|  
|[GetProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|このモジュールに格納しているプロセスを取得します。|  
|[GetSize メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|モジュールのサイズをバイト単位で取得します。|  
|[GetToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|このモジュールのテーブルのエントリのトークンを取得します。|  
|[IsDynamic メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|モジュールが動的かどうかを示します。|  
|[IsInMemory メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|このモジュールは、メモリ内にのみ存在するかどうかを示します。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
