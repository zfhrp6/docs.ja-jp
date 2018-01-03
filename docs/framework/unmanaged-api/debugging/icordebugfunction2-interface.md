---
title: ICorDebugFunction2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2
helpviewer_keywords: ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ac3a4cd5ec2aff1b60cd51ca33d411e5cc81eb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2-interface1"></a>ICorDebugFunction2 Interface1
非ユーザー コードをスキップするデバッグ手順で マイ コードのみをサポートする ICorDebugFunction インターフェイスを論理的に拡張します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumerateNativeCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|(まだ実装されていません。)ICorDebugFunction2 オブジェクトによって参照された関数のネイティブ コードのステートメントを含む ICorDebugCodeEnum へのインターフェイス ポインターを取得します。|  
|[GetJMCStatus メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|この関数はユーザー コードとしてマークされているかどうかを示す値を取得します。|  
|[GetVersionNumber メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|この関数のエディット コンティニュ バージョンを取得します。|  
|[SetJMCStatus メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|マイ コードのみのマークをこの関数のステップ インします。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
