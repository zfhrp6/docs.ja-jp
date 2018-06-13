---
title: ICorDebugEval2::CallParameterizedFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77d9ec0cf1cbca63382e7f29de85c2f9566dc2bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416167"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction メソッド
コンス トラクターは、クラス内で入れ子にできる指定の ICorDebugFunction への呼び出しを設定<xref:System.Type>パラメーター、またはそれ自体がとれる<xref:System.Type>パラメーター。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pFunction`  
 [in]ポインター、`ICorDebugFunction`に呼び出される関数を表すオブジェクト。  
  
 `nTypeArgs`  
 [in]関数が受け取る引数の数。  
  
 `ppTypeArgs`  
 [in]関数の引数を表す ICorDebugType オブジェクトを指し示すそれぞれが、ポインターの配列。  
  
 `nArgs`  
 [in]値の数は、関数に渡されます。  
  
 `ppArgs`  
 [in]関数の引数の値を表す ICorDebugValue オブジェクトを指し示すそれぞれが、ポインターの配列が渡されます。  
  
## <a name="remarks"></a>コメント  
 `CallParameterizedFunction` 同様に、 [icordebugeval::callfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)関数は、型パラメーターを持つクラスの内部である可能性があります、する点を除いてかかる場合があります自体の型パラメーター、またはその両方です。 クラスのしてから、関数、型引数を最初に指定してください。  
  
 関数は、別のアプリケーション ドメインでは、遷移が発生します。 ただし、すべての型と値の引数は、対象のアプリケーション ドメインにする必要があります。  
  
 関数の評価は、限られたシナリオでのみ実行できます。 場合`CallParameterizedFunction`または`ICorDebugEval::CallFunction`失敗した場合、返された HRESULT エラーに対する最も一般的な原因が示されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
