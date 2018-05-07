---
title: ICorDebugILFrame4::GetCodeEx メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: edaea49d95eeb9856b949f118f16aa49e528f7ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx メソッド
[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 このスタック フレームが実行中のコードに対するポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `flags`  
 [in][ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)フレーム プロファイラーの ReJIT 要求によって定義された中間言語 (IL) が含まれるかどうかを示す列挙メンバー。  
  
 `ppCode`  
 [out]このスタック フレームが実行されているコードを表す"ICorDebugCode"オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>コメント  
 このメソッドがに似ていますが、 [icordebugframe::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)メソッド、任意でアクセスするコード プロファイラーの ReJIT 要求によって定義される点が異なります。 このメソッドを呼び出すと、`flags`の値`ILCODE_ORIGINAL_IL`を呼び出すことと同じです[GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)以外の場合は、メソッドはインストルメント化されて、IL をアクセス可能にすることはできません。 `ILCODE_REJIT_IL` を使用するとデバッガーは、プロファイラーの ReJIT 要求で定義された IL にアクセスできます。 IL がインストルメントされていない場合`ppCode`は**null**が返されます`S_OK`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugILFrame4 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: ハウツー ガイド](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
