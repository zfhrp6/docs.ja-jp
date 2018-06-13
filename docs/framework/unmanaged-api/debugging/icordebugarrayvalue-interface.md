---
title: ICorDebugArrayValue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a96f2b21e524f03ea3290be268244eaceeb5c7f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408178"
---
# <a name="icordebugarrayvalue-interface1"></a>ICorDebugArrayValue Interface1
1 次元または多次元配列を表す ICorDebugHeapValue のサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBaseIndicies メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|配列内の各次元の基本のインデックスを取得します。|  
|[GetCount メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|配列の要素の合計数を取得します。|  
|[GetDimensions メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|配列の次元を取得します。|  
|[GetElement メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|配列内の特定の要素を表す値を取得します。|  
|[GetElementAtPosition メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|0 から始まる 1 次元の配列として、配列を扱う方法の指定された位置に要素を取得します。|  
|[GetElementType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|配列内の要素の単純型を取得します。|  
|[GetRank メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|配列のディメンションの数を取得します。|  
|[HasBaseIndicies メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|配列の基本のインデックスがあるかどうかを判断します。|  
  
## <a name="remarks"></a>コメント  
 `ICorDebugArrayValue` 1 次元と多次元の両方の配列をサポートします。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
