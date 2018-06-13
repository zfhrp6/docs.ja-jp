---
title: ICorDebugModule2 Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 537023cf117477b54117799fc9ea62e894bb6591
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419141"
---
# <a name="icordebugmodule2-interface1"></a>ICorDebugModule2 Interface1
ICorDebugModule インターフェイスを論理的に拡張として機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ApplyChanges メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|実行中のプロセスにメタデータの変更と Microsoft intermediate language (MSIL) コードの変更を適用します。|  
|[GetJITCompilerFlags メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|この・ イン タイム (JIT) コンパイルを制御するフラグを取得`ICorDebugModule2`です。|  
|[ResolveAssembly メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|指定したメタデータ トークンによって参照されるアセンブリを解決します。|  
|[SetJITCompilerFlags メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|この JIT コンパイルを制御するフラグを設定`ICorDebugModule2`です。|  
|[SetJMCStatus メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|これですべてのクラスのすべてのメソッドのだけマイ コードのみ (JMC) 状態に設定`ICorDebugModule2`を除き、指定した値を`pTokens`配列で、その逆の値に設定します。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
