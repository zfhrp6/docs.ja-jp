---
title: ICorDebugMDA インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550b39445dfe4d97e712e9a4c73aa0f497b3fce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420967"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA インターフェイス
マネージ デバッグ アシスタント (MDA) メッセージを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetDescription メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|この MDA の説明を含む文字列を取得します。|  
|[GetFlags メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|この MDA に関連付けられているフラグを取得します。|  
|[GetName メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|この MDA の名前を含む文字列を取得します。|  
|[GetOSThreadId メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|この MDA を実行して基になるオペレーティング システムのスレッド識別子を取得します。|  
|[GetXML メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|この MDA に関連付けられている満杯になった XML ストリームを取得します。|  
  
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
 [マネージ デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
