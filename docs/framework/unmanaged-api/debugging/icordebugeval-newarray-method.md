---
title: "ICorDebugEval::NewArray メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewArray
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db9b5f7241e2be53cfbc2c6cea3da1b0182c3eb6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray メソッド
指定した要素の型および次元の新しい配列を割り当てます。  
  
 このメソッドは、.NET Framework version 2.0 廃止されています。 使用して[icordebugeval 2::newparameterizedarray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `elementType`  
 [in]配列の要素の型を指定する CorElementType 列挙型の値です。  
  
 `pElementClass`  
 [in]要素のクラスを指定する ICorDebugClass オブジェクトへのポインター。 この値を要素の型がプリミティブ型の場合は null にすることがあります。  
  
 `rank`  
 [in]配列の次元の数。 .NET Framework 2.0 でこの値は 1 にする必要があります。  
  
 `dims`  
 [in]配列の各次元のバイト単位のサイズ。  
  
 `lowBounds`  
 [in] オプション。 配列の各次元の下限値です。 この値を省略すると、各次元の下限を 0 が使われます。  
  
## <a name="remarks"></a>コメント  
 配列は常に、現在のスレッドが実行しているアプリケーション ドメインに作成します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 1.1、1.0
