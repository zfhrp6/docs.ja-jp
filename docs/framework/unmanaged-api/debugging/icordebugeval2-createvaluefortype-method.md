---
title: ICorDebugEval2::CreateValueForType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 683457c249915708becadaeda9dec265666e2023
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412108"
---
# <a name="icordebugeval2createvaluefortype-method"></a>ICorDebugEval2::CreateValueForType メソッド
0 または null の初期値を持つ、指定した型の新しい ICorDebugValue へのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pType`  
 [in]型を表す ICorDebugType オブジェクトへのポインター。  
  
 `ppValue`  
 [out]アドレスへのポインター、`ICorDebugValue`値を表すオブジェクト。  
  
## <a name="remarks"></a>コメント  
 `CreateValueForType` 一般化[icordebugeval::createvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)ことで、任意のオブジェクトの種類を指定するなど構築された型など`List<int>`です。 このメソッドの唯一の目的では、関数の評価に渡すことができる値を生成します。  
  
 種類は、クラスまたは値型にする必要があります。 このメソッドを使用して、配列の値または文字列値を作成することはできません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
