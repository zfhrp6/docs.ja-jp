---
title: "ICorDebugEval2::NewParameterizedObjectNoConstructor メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 27e4693b39f9ce27ac18eb2fa542b5a0196f21cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a>ICorDebugEval2::NewParameterizedObjectNoConstructor メソッド
コンス トラクター メソッドを呼び出さずに、指定したクラスの新しい型のパラメーター化されたオブジェクトをインスタンス化します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pClass`  
 [in]インスタンス化されるオブジェクトのクラスを表す ICorDebugClass オブジェクトへのポインター。  
  
 `nTypeArgs`  
 [in]型引数の数が渡されます。  
  
 `ppTypeArgs`  
 [in]ICorDebugType を表すオブジェクトがインスタンス化されるオブジェクトの型引数が指すそれぞれが、ポインターの配列。  
  
## <a name="remarks"></a>コメント  
 `NewParameterizedObjectNoConstructor`メソッドには、型引数の数が正しくない場合は失敗または型引数の間違った型が渡されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
