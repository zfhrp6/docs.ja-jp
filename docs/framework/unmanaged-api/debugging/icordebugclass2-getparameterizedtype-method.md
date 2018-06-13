---
title: ICorDebugClass2::GetParameterizedType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.GetParameterizedType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a5b3a28c7250a16e78e199bceff7c9e64517319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408214"
---
# <a name="icordebugclass2getparameterizedtype-method"></a>ICorDebugClass2::GetParameterizedType メソッド
このクラスの型宣言を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `elementType`  
 [in]このクラスの要素の型を指定する CorElementType 列挙型の値: この ICorDebugClass2 が値型を表している場合、ELEMENT_TYPE_VALUETYPE にこの値を設定します。 この場合は、この値を ELEMENT_TYPE_CLASS に設定します。`ICorDebugClass2`複合型を表します。  
  
 `nTypeArgs`  
 [in]型がジェネリックの場合、型パラメーターの数。 型パラメーター (ある場合) の数は、クラスに必要な数と一致する必要があります。  
  
 `ppTypeArgs`  
 [in]型パラメーターを表す ICorDebugType オブジェクトを指し示すそれぞれが、ポインターの配列。 クラスが非ジェネリックの場合は、この値が null です。  
  
 `ppType`  
 [out]アドレスへのポインター、`ICorDebugType`型宣言を表すオブジェクト。 このオブジェクトは、<xref:System.Type>マネージ コード内のオブジェクト。  
  
## <a name="remarks"></a>コメント  
 場合は、クラスは、非ジェネリックでは、型パラメーターが存在しない場合`GetParameterizedType`クラスに対応するランタイム型のオブジェクトを取得するだけです。 `elementType`クラスの正しい要素の型にパラメーターを設定する必要があります: ELEMENT_TYPE_VALUETYPE クラスが値型である場合はそれ以外の場合、ELEMENT_TYPE_CLASS です。  
  
 クラスが型パラメーターを受け入れる場合 (たとえば、 `ArrayList<T>`)、使用することができます`GetParameterizedType`など型のインスタンスの型のオブジェクトを構築するために`ArrayList<int>`です。  
  
## <a name="background-information"></a>背景情報  
 .NET Framework バージョン 1.0 および 1.1 では、メタデータ内のすべての型を直接実行中のプロセス内の型にマップすることもできます。 したがって、メタデータの種類と、ランタイム型は、実行中のプロセスで 1 つの表現必要があります。 ただし、メタデータ内の 1 つのジェネリック型は、実行中のプロセスでの型の複数の異なるインスタンスにマップできます。 たとえば、メタデータ型`SortedList<K,V>`にマップできます`SortedList<String, EmployeeRecord>`、 `SortedList<Int32, String>`、`SortedList<String,Array<Int32>>`のようにします。 したがって、型のインスタンス化を処理する必要があります。  
  
 .NET Framework version 2.0 では、`ICorDebugType`インターフェイスです。 ジェネリック型の場合、`ICorDebugClass`または`ICorDebugClass2`オブジェクトがインスタンス化されていない型を表します (`SortedList<K,V>`)、および`ICorDebugType`オブジェクトは、さまざまなインスタンス化された型を表します。 指定された、`ICorDebugClass`または`ICorDebugClass2`オブジェクトを作成することができます、`ICorDebugType`オブジェクトを呼び出すことによって、インスタンス化、`ICorDebugClass2::GetParameterizedType`メソッドです。 作成することも、 `ICorDebugType` Int32 などの単純型または非ジェネリック型のオブジェクト。  
  
 導入、`ICorDebugType`型の実行時の概念を表現するオブジェクトが、API 全体に影響します。 かかっていた関数、`ICorDebugClass`または`ICorDebugClass2`オブジェクトまたはであっても、`CorElementType`値を汎用化されて、`ICorDebugType`オブジェクト。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
