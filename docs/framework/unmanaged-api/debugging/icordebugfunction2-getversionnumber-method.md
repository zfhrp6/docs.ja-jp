---
title: ICorDebugFunction2::GetVersionNumber メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdd2151c4886959647de4f9e27a20a93ffc07429
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420054"
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber メソッド
この関数のエディット コンティニュ バージョンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pnVersion`  
 [out]ICorDebugFunction2 オブジェクトによって表される関数のバージョン番号を示す整数へのポインター。  
  
## <a name="remarks"></a>コメント  
 ランタイムの追跡、デバッグ セッション中に各モジュールに行われた編集の数。 関数のバージョン番号は 1 つの関数を導入した編集数よりも詳細です。 関数の元のバージョンは 1 です。 数は、モジュールのされるたびに増加[icordebugmodule 2::applychanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)でそのモジュールが呼び出されます。 したがって、最初と 3 番目の呼び出しで、関数の本体が置き換えられた場合`ICorDebugModule2::ApplyChanges`、`GetVersionNumber`バージョン 1、2、または 4 その関数のバージョンではない 3 を返す可能性があります。 (その関数がないバージョン 3 です。)  
  
 バージョン番号は、モジュールごとに個別に追跡されます。 したがって、モジュール 1 および第 2 章に none で 4 つの編集を実行するとモジュール 1 で、[次へ] の編集は、その 6 のバージョン番号をモジュール 1 で編集されたすべての関数に割り当てられます。 編集する場合は、同じモジュール 2、第 2 章の関数は 2 のバージョン番号を取得します。  
  
 バージョン番号を取得して、`GetVersionNumber`メソッドによって取得されるよりも低い場合があります[icordebugfunction::getcurrentversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)です。  
  
 [Icordebugcode::getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)メソッドとして同じ操作を実行`ICorDebugFunction2::GetVersionNumber`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
