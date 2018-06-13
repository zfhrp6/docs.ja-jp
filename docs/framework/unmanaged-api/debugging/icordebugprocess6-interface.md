---
title: ICorDebugProcess6 インターフェイス
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 103a37d7549d7ec18617b74c777506b3ad225a18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422859"
---
# <a name="icordebugprocess6-interface"></a>ICorDebugProcess6 インターフェイス
ネイティブ例外デバッグ イベントや仮想モジュール分割でエンコードされたマネージ デバッグ イベントをデコードなどの機能を有効にする ICorDebugProcess インターフェイスを論理的に拡張します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[DecodeEvent メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|特別に作成されたネイティブ例外デバッグ イベントのペイロードにカプセル化されたマネージ デバッグ イベントをデコードします。|  
|[EnableVirtualModuleSplitting メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|仮想モジュール分割を有効または無効にします。|  
|[GetCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|特定のコード アドレスで、マネージ コードに関する情報を取得します。|  
|[GetExportStepInfo メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|マネージ コードのステップ実行に役立つランタイム エクスポート関数の情報を提供します。|  
|[MarkDebuggerAttached メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|.NET Framework クラス ライブラリの <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> メソッドが `true` を返すように、デバッグ対象の内部状態を変更します。|  
|[ProcessStateChanged メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|通知[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)プロセスを実行しています。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このインターフェイスは .NET ネイティブでのみ使用可能です。 インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
