---
title: ICorDebugHeapValue2::CreateHandle メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c69d1f83a4591df4d2dcb7fb9724fa582ea28387
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413580"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle メソッド
ICorDebugHeapValue2 オブジェクトによって表されるヒープ値の指定した型のハンドルを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `type`  
 [in]作成されるハンドルの種類を指定する CorDebugHandleType 列挙型の値です。  
  
 `ppHandle`  
 [out]このヒープ値に対して新しいハンドルを表す ICorDebugHandleValue オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>コメント  
 ハンドルは、ヒープの値に関連付けられているアプリケーション ドメインでが作成され、アプリケーション ドメインがアンロードされると無効になります。  
  
 この関数はヒープの値が同じ複数の呼び出しでは、複数のハンドルを作成します。 ハンドルは、ガベージ コレクターのパフォーマンスに影響するために一度にアクティブになっているハンドル (約 256) の数を比較的小さなデバッガーに制限する必要があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
