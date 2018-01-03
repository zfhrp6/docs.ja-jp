---
title: "ICorDebugMutableDataTarget インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e638b01b30f7969ac3116c6c2725fb4cb3768a68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmutabledatatarget-interface"></a>ICorDebugMutableDataTarget インターフェイス
拡張、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)変更可能なデータ ターゲットをサポートするインターフェイスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ContinueStatusChanged メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|指定のスレッド上にある未処理のデバッグ イベントの継続状態を変更します。|  
|[SetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|スレッドのコンテキスト (レジスタの値) を設定します。|  
|[WriteVirtual メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|ターゲット プロセスのアドレス空間にメモリを書き込みます。|  
  
## <a name="remarks"></a>コメント  
 この拡張機能、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)デバッグ ツール (たとえば、ライブ侵デバッグを実行する場合など) ターゲット プロセスを変更することによってインターフェイスを実装することができます。  
  
 これらのメソッドすべては省略可能です。つまり、このインターフェイスを実装しない場合や、これらのメソッドに対する呼び出しに失敗する場合にも、コア検査に基づくデバッグ機能は失われません。  これらのメソッドからの失敗 `HRESULT` すべては、ICorDebug メソッドからの `HRESULT` として伝達されます。  
  
 1 回の ICorDebug メソッド呼び出しによって複数の変更が行われる可能性があること、および関連する変更をトランザクションごとに適用するメカニズムがないこと (すべてに適用するか、まったく適用しないかのどちらか) に注意してください。  つまり、(同じ ICorDebug 呼び出しの) 他のユーザーが正常に完了した後に変更を失敗すると、ターゲット プロセスは一貫性のない状態のままになり、デバッグが信頼性に欠ける結果になる可能性があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
