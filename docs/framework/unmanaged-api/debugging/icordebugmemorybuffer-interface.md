---
title: "ICorDebugMemoryBuffer インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80002d064c48a90236a64a3d0a56fab5877cf411
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmemorybuffer-interface"></a>ICorDebugMemoryBuffer インターフェイス
メモリ内のバッファーを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetSize メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|メモリ バッファーのサイズ (バイト単位) を取得します。|  
|[GetStartAddress メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|メモリ バッファーの開始アドレスを取得します。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このインターフェイスは .NET ネイティブでのみ使用可能です。 .NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
