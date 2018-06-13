---
title: ICorDebugEval2::NewParameterizedArray メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 552d2fa8a7c35066e32fb9f8e9455b3092b1e65b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413281"
---
# <a name="icordebugeval2newparameterizedarray-method"></a>ICorDebugEval2::NewParameterizedArray メソッド
指定した要素の型および次元の新しい配列を割り当てます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pElementType`  
 [in]配列に格納されている要素の型を表す ICorDebugType オブジェクトへのポインター。  
  
 `rank`  
 [in]配列の次元の数。 .NET Framework version 2.0 では、この値は 1 にする必要があります。  
  
 `dims`  
 [in]配列の各次元のバイト単位のサイズ。  
  
 `lowBounds`  
 [in] オプション。 配列の各次元の下限値です。 この値を省略すると、各次元の下限を 0 が使われます。  
  
## <a name="remarks"></a>コメント  
 配列の要素のジェネリック型のインスタンスがあります。 配列は常に、現在のスレッドが実行されているアプリケーション ドメインに作成します。 .NET Framework 2.0 の値で`rank`1 にする必要があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
