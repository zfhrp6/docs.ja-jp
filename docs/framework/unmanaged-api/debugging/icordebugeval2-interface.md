---
title: ICorDebugEval2 Interface1
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
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ac816d2b2dce6c9c76813bf4247bac7ca40da5f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2-interface1"></a>ICorDebugEval2 Interface1
"ICorDebugEval"の拡張のジェネリック型のサポートを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CallParameterizedFunction メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|指定された"ICorDebugFunction"、型コンス トラクターが型パラメーターを受け取るか、型パラメーターを受け取り、それ自体の内部で入れ子にできるへの呼び出しを設定します。|  
|[CreateValueForType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|Null またはゼロの初期値を持つ新しい"ICorDebugValue"に指定した型のポインターを取得します。|  
|[NewParameterizedArray メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|指定した要素の型および次元の新しい配列を割り当てます。|  
|[NewParameterizedObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|新しいパラメーター化された型のオブジェクトをインスタンス化し、オブジェクトのコンス トラクター メソッドを呼び出します。|  
|[NewParameterizedObjectNoConstructor メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|コンス トラクター メソッドを呼び出さずに、指定したクラスの新しい型のパラメーター化されたオブジェクトをインスタンス化します。|  
|[NewStringWithLength メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|指定された内容を指定された長さの新しい文字列を作成します。|  
|[RudeAbort メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|計算の中止この`ICorDebugEval2`は現在を実行します。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
