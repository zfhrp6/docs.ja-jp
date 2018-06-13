---
title: ICorDebugStepper Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 339b823e5e9f38ffd175c79e379e28ccc3565c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423287"
---
# <a name="icordebugstepper-interface1"></a>ICorDebugStepper Interface1
デバッガーが実行するコード実行内のステップを表します。コマンドの発行から完了までの間は識別子として機能します。これを使用するとステップをキャンセルできます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Deactivate メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|この原因`ICorDebugStepper`を受信した最後のステップ コマンドをキャンセルします。|  
|[IsActive メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|示す値を取得するかどうかこの`ICorDebugStepper`ステップが現在実行中です。|  
|[SetInterceptMask メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|ステップ インできるコードの型を指定する CorDebugIntercept 値を設定します。|  
|[SetRangeIL メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|示す値を設定するかどうかを呼び出す[icordebugstepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)にステップ スルーされるが、メソッドの Microsoft intermediate language (MSIL) コードまたはネイティブ コードへの相対引数の値を渡します。|  
|[SetUnmappedStopMask メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|マップ解除したコードの実行が停止しメッセージの種類を指定する CorDebugUnmappedStop 値を設定します。|  
|[Step メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|この原因`ICorDebugStepper`シングル ステップ実行にその格納スレッドおよび必要に応じて、スレッド内で呼び出される関数をシングル ステップ実行を続行します。|  
|[StepOut メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|この原因`ICorDebugStepper`ときに完了してその格納スレッドを 1 ステップを現在のフレームが呼び出し元のフレームにコントロールを返します。|  
|[StepRange メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|この原因`ICorDebugStepper`シングル ステップ実行し、その格納スレッド場合に返されるに指定された範囲の最後のタスクを超えるコードに到達します。|  
  
## <a name="remarks"></a>コメント  
 `ICorDebugStepper`インターフェイスは、次の目的で機能します。  
  
-   ステップ コマンドが発行して、そのコマンドの完了の間で識別子として機能します。  
  
-   実行できるすべてのステップ実行をカプセル化する中央のインターフェイスを提供します。  
  
-   処理の途中でステップ実行の操作をキャンセルする方法を提供します。  
  
 スレッドあたり 1 つ以上のステッパことができます。 たとえば、関数のステップ オーバー中に、ブレークポイントにヒットする可能性があり、ユーザーがその関数内の新しいステップ実行操作を開始することもします。 この状況に対処する方法を決定する、デバッガーの責任です。 デバッガーは、元のステップ実行操作をキャンセルするか 2 つの操作を入れ子にできます。 `ICorDebugStepper`インターフェイスが 2 つの選択肢をサポートしています。  
  
 ステッパは、共通言語ランタイム (CLR) は、マーシャ リングされたクロス スレッド呼び出しを行う場合、スレッド間で移行可能性があります。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
