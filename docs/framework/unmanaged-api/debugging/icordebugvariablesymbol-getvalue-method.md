---
title: "ICorDebugVariableSymbol::GetValue メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 789bca88ea2f2d87ebfc73275b4a7569fcbe8cc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>ICorDebugVariableSymbol::GetValue メソッド
変数の値をバイト配列として取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `offset`  
 [in] 値を読み取る変数内の開始オフセットです。 このパラメーターは、オブジェクトのメンバー フィールドを読み取る際に使用されます。  
  
 `cbContext`  
 [in] `context` 引数のバイト単位のサイズ。  
  
 `context`  
 [in] 値の読み取りに使用されるスレッド コンテキスト。  
  
 `cbValue`  
 [in] `pValue` バッファーのバイト単位のサイズ。  
  
 `pcbValue`  
 [out] `pValue` バッファーに実際に書き込まれたバイト数。  
  
 `pValue`  
 [out] 変数の値が格納されているバイト配列。  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugVariableSymbol インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
