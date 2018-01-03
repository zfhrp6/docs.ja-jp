---
title: "ICorDebugDataTarget2::CreateVirtualUnwinder メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bffbf95fc38cba6f311e0641b35e2696bd34099
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a>ICorDebugDataTarget2::CreateVirtualUnwinder メソッド
初期コンテキストからアンワインドを開始する新しいスタック アンワインダーを作成します (これは、必ずしもスレッドのリーフではありません)。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
 nativeThreadID  
 [入力] スタックをアンワインドするスレッドのネイティブ スレッド ID。  
  
 contextFlags  
 [入力] コンテキストのどの部分が `initialContext` で定義されるかを指定するフラグ。  
  
 cbContext  
 [入力] `initialContext` のサイズ。  
  
 initialContext  
 [入力] コンテキストのデータ。  
  
 ppUnwinder  
 [出力] ICorDebugVirtualUnwinder インターフェイス オブジェクトのアドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  
 正常終了した場合は、`S_OK`。 それ以外の `HRESULT` は失敗を示します。 失敗した`HRESULT`mscordbi によって受信された致命的と見なされ、により[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)を返すメソッド`CORDBG_E_DATA_TARGET_ERROR`です。  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugDataTarget2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
