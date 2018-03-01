---
title: ICorDebugValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c3464b4ad963b2fe764cefc5868440b7748f8c4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue-interface1"></a>ICorDebugValue Interface1
デバッグ中のプロセス内の値を表します。 値には、読み取り/書き込み値を指定できます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateBreakpoint メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|このメソッドは現在実装されていません。|  
|[GetAddress メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|このアドレスを取得`ICorDebugValue`オブジェクトで、デバッグされている処理を行っています。|  
|[GetSize メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|サイズを取得します (バイト単位) のこの`ICorDebugValue`オブジェクト。|  
|[GetType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|これのプリミティブ型を取得`ICorDebugValue`オブジェクト。|  
  
## <a name="remarks"></a>コメント  
 一般が返される値オブジェクトの所有権が渡されます。 受信者は、オブジェクトが終了したときに、オブジェクトからの参照を削除します。  
  
 ここで、値を取得した、に応じて値のままになる有効なプロセスが再開されます。 そのため、一般に、値はならない保持の呼び出しで、 [icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)メソッドです。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
    
    
    
    
 [ICorDebugValue3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
