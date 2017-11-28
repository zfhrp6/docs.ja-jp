---
title: "ICorDebugVirtualUnwinder::GetContext メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45a914005e84d33b39d72fce96679e275b921d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>ICorDebugVirtualUnwinder::GetContext メソッド
このアンワインダーの現在のコンテキストを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `contextFlags`  
 [in] (WinNT.h で定義されている) コンテキストのどの部分を返すかを指定するフラグ。  
  
 `cbContextBuf`  
 [in] `contextBuf` のバイト数。  
  
 `contextSize`  
 [out] `contextBuf` に実際に書き込まれたバイト数へのポインター。  
  
 `contextBuf`  
 [out] このアンワインダーの現在のコンテキストが格納されているバイト配列。  
  
## <a name="return-value"></a>戻り値  
 mscordbi によって受信された失敗を示す HRESULT 値は致命的と見なされ、ICorDebug API によって `CORDBG_E_DATA_TARGET_ERROR` が返されます。  
  
## <a name="remarks"></a>コメント  
 初期値を設定する、`contextBuf`呼び出すことによって返されるコンテキスト バッファーへの引数、 [icordebugstackwalk::getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)メソッドです。  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
 アンワインドではレジスタのサブセット (例: 不揮発性レジスタのみ) だけが復元されるため、コンテキストが、実際のメソッド呼び出し時点でのレジスタの状態と正確には一致しないことがあります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugMemoryBuffer インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
