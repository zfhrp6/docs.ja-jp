---
title: "ICorDebugEval2::NewParameterizedObject メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39b69a82f25ab6df5f2bd2f6dc70caf1bf13a0f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newparameterizedobject-method"></a>ICorDebugEval2::NewParameterizedObject メソッド
新しいパラメーター化された型のオブジェクトをインスタンス化し、オブジェクトのコンス トラクター メソッドを呼び出します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pConstructor`  
 [in]ICorDebugFunction を表すオブジェクトをインスタンス化するオブジェクトのコンス トラクターへのポインター。  
  
 `nTypeArgs`  
 [in]型引数の数が渡されます。  
  
 `ppTypeArgs`  
 [in]ICorDebugType を表すオブジェクトがインスタンス化されるオブジェクトの型引数が指すそれぞれが、ポインターの配列。  
  
 `nArgs`  
 [in]引数の数は、コンス トラクターに渡されます。  
  
 `ppArgs`  
 [in]それぞれのオブジェクトをポイントする ICorDebugValue コンス トラクターに渡される引数の値を表す、ポインターの配列。  
  
## <a name="remarks"></a>コメント  
 オブジェクトのコンス トラクターがかかる場合があります<xref:System.Type>パラメーター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
