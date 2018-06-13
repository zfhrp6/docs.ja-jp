---
title: ICorDebugEval::CallFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86d48461c601b53d4461331a11a0e0ac7ddc6e7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412553"
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction メソッド
指定した関数への呼び出しを設定します。  
  
 このメソッドは、.NET Framework version 2.0 廃止されています。 使用して[icordebugeval 2::callparameterizedfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CallFunction (  
    [in] ICorDebugFunction  *pFunction,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pFunction`  
 [in]呼び出される関数を指定する ICorDebugFunction オブジェクトへのポインター。  
  
 `nArgs`  
 [in]関数の引数の数。  
  
 `ppArgs`  
 [in]ポインターの配列、それぞれのオブジェクトをポイントする ICorDebugValue 関数に渡される引数を指定します。  
  
## <a name="remarks"></a>コメント  
 終了した場合は、仮想`CallFunction`仮想ディスパッチを実行します。 関数は、別のアプリケーション ドメインでは、すべての引数がそのアプリケーション ドメイン内にも限り遷移が発生します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** WindowSee[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 1.1、1.0  
  
## <a name="see-also"></a>関連項目  
 [CallParameterizedFunction メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
