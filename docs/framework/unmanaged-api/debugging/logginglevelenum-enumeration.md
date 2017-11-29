---
title: "LoggingLevelEnum 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoggingLevelEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: LoggingLevelEnum
helpviewer_keywords: LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f6041f429c057cea9607df34ec5691be84e2d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum 列挙型
マネージ スレッドがイベントを記録する際にイベント ログに書き込まれる説明メッセージの重大度レベルを示します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`LTraceLevel0`|メッセージは、トレース レベル 0 です。|  
|`LTraceLevel1`|メッセージは、トレース レベル 1 です。|  
|`LTraceLevel2`|メッセージは、トレース レベル 2 です。|  
|`LTraceLevel3`|メッセージは、トレース レベル 3 です。|  
|`LTraceLevel4`|メッセージは、トレース レベル 4 です。|  
|`LStatusLevel0`|メッセージは、ステータス レベル 0 です。|  
|`LStatusLevel1`|メッセージは、レベル 1 の状態です。|  
|`LStatusLevel2`|メッセージは、ステータス レベル 2 です。|  
|`LStatusLevel3`|メッセージは、ステータス レベル 3 です。|  
|`LStatusLevel4`|メッセージは、ステータス レベル 4 です。|  
|`LWarningLevel`|メッセージは、警告レベルです。|  
|`LErrorLevel`|メッセージは、エラー レベルです。|  
|`LPanicLevel`|メッセージは、重大レベルです。|  
  
## <a name="remarks"></a>コメント  
 共通言語ランタイム (CLR) を呼び出す、 [icordebugmanagedcallback::logmessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)マネージ スレッドがイベントを記録するデバッガーに通知します。 CLR の値を渡す、`LoggingLevelEnum`マネージ スレッドが、イベント ログに書き込んで、メッセージの重大度レベルを示す列挙体です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Diagnostics.EventLog>  
 [列挙体のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
