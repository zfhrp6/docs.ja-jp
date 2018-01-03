---
title: "ICorDebugEval::NewObject メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98c885e7ffd4b35bcc3af34757509910c78c0c90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalnewobject-method"></a>ICorDebugEval::NewObject メソッド
オブジェクトの新しいインスタンスを割り当てるし、指定したコンス トラクター メソッドを呼び出します。  
  
 このメソッドは、.NET Framework version 2.0 廃止されています。 使用して[icordebugeval 2::newparameterizedobject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pConstructor`  
 [in]呼び出されるコンス トラクターです。  
  
 `nArgs`  
 [in] `ppArgs` 配列のサイズ。  
  
 `ppArgs`  
 [in]ICorDebugValue オブジェクトのコンス トラクターに渡される引数を表す配列。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 1.1、1.0  
  
## <a name="see-also"></a>参照  
 [NewParameterizedObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
