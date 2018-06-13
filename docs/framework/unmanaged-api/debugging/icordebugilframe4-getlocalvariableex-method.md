---
title: ICorDebugILFrame4::GetLocalVariableEx メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a82f092a0f10fd621ac4facdee201fa239e1c1b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414530"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>ICorDebugILFrame4::GetLocalVariableEx メソッド
[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 この中間言語 (IL) スタック フレーム内の指定されたローカル変数の値を取得して、オプションでプロファイラー ReJIT インストルメンテーションに追加された変数にアクセスできます。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `flags`  
 [in][ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)プロファイラー ReJIT インストルメンテーションに追加された変数がフレームに含まれるかどうかを指定する列挙体メンバーです。  
  
 `dwIndex`  
 [in] IL スタック フレーム内のローカル変数のインデックス。  
  
 `ppValue`  
 [out]取得した値を表す"ICorDebugValue"オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>コメント  
 このメソッドがに似ていますが、 [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)メソッドを除いて、任意でアクセスする変数がプロファイラー ReJIT インストルメンテーションに追加します。 このメソッドを呼び出すと、`flags`の値`ILCODE_ORIGINAL_IL`は呼び出すことと同じ[GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)以外の場合は、メソッドはローカル変数を追加、インストルメント化されてそれらの変数にアクセスできません。 `ILCODE_REJIT_IL` は、デバッガーがプロファイラー ReJIT インストルメンテーションに追加されたローカル変数にアクセスできるようにします。 IL がインストルメントされていない場合、メソッドは `E_INVALIDARG` を返します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugILFrame4 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: ハウツー ガイド](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
