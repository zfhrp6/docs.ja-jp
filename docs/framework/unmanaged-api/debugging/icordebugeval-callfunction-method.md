---
title: "ICorDebugEval::CallFunction メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.CallFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c2d5582c9ac69692546e9a2310c4d0c9cdde83e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** WindowSee[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 1.1、1.0  
  
## <a name="see-also"></a>参照  
 [CallParameterizedFunction メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
