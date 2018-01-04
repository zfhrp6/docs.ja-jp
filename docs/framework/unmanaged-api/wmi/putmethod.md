---
title: "PutMethod 関数 (アンマネージ API リファレンス)"
description: "PutMethod 関数では、メソッドを作成します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutMethod
helpviewer_keywords: PutMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7e97ffcf44a738234f67d9736382c46c42e5b61e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="putmethod-function"></a>PutMethod 関数
メソッドを作成します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`wszName`  
[in]作成する方法の名前。 

`lFlags`  
[in]予約されています。 このパラメーターは、0 を指定する必要があります。

`pSignatureIn`  
[in]コピーへのポインター、 [_parameters システム クラス](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx)を格納している、`in`メソッドのパラメーターです。 場合、このパラメーターは無視されます 'éý'`null`です。  

`pSignatureOut`  
[in] コピーへのポインター、 [_parameters システム クラス](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx)を格納している、`out`メソッドのパラメーターです。 場合、このパラメーターは無視されます 'éý'`null`です。
 

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 1 つまたは複数のパラメーターが有効ではありません。 |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | `[in, out]`メソッド パラメーターの両方で指定された、 *pInSignature*と*pOutSignature*オブジェクトが別の修飾子を持ちます。
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | メソッド パラメーターには、指定が不足して、 **ID**修飾子です。 |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | メソッドのパラメーターに割り当てられている ID の系列が連続するか、0 から始まっていません。 |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | メソッドの戻り値は、 **ID**修飾子です。 |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | 親クラスからの既存のメソッド名を再利用しようとしましたが、シグネチャが一致しませんでした。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。 |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx)メソッドです。

場合にのみ、このメソッドの呼び出しがサポート`ptr`CIM クラス定義です。 メソッドの操作からは使用できない[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) CIM インスタンスを指すポインターです。

ユーザーは、名前にアンダー スコアで開始または終了をメソッドを作成することはできません。 これはシステム クラスとプロパティの予約されています。

メソッドで、`in`と`out`パラメーターがプロパティとして記載されている[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396)オブジェクト。

`[in/out]`によって示される両方のオブジェクトに同じプロパティを追加することでパラメーターを定義することができます、`pInSignature`と`pOutSignature`パラメーター。 この場合、プロパティが同じ**ID**修飾子の値。

内の各プロパティ、 [_parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx)以外のオブジェクトをクラス`ReturnValue`必要があります、 **ID**修飾子、パラメーターの順序を識別する 0 から始まる数値です。 ない 2 つのパラメーターと同じであることができます**ID**値、およびなし**ID**値をスキップすることができます。 いずれかの条件が発生した場合、`PutMethod`関数が返される`WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`です。

## <a name="example"></a>例

例については、次を参照してください。、 [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx)メソッドです。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
