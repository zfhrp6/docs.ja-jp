---
title: "WritePropertyValue 関数 (アンマネージ API リファレンス)"
description: "WritePropertyValue 関数は、プロパティにバイトを書き込みます。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: WritePropertyValue
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: WritePropertyValue
helpviewer_keywords: WritePropertyValue function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26337a13ab9840b79c253d4af2d84a10e70877c5
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue 関数
プロパティのハンドルによって識別されたプロパティに指定したバイト数を書き込みます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx)インスタンス。

`lHandle`  
[in]このプロパティを識別するハンドルを格納する整数。 呼び出すことによって、ハンドルを取得できる、 [GetPropertyHandle](getpropertyhandle.md)関数。   

`lNumBytes`  
[in]プロパティに書き込まれるバイト数。 参照してください、[解説](#remarks)詳細についてはします。

`pHandle`   
[out]データを格納するバイト配列へのポインター。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |値  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | 型の不一致が発生しました。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::WritePropertyValue](https://msdn.microsoft.com/library/aa391783(v=vs.85).aspx)メソッドです。

使用してこの関数の文字列とすべて他の非`DWORD`または非-`QWORD`データ。

プロパティ値は文字列ではない、`lNumBytes`指定されたプロパティの型の適切なデータ サイズにする必要があります。 文字列プロパティの値の`lNumBytes`長さにする必要があります (バイト単位) で指定した文字列および文字列の偶数の長さ (バイト単位) の必要があり、null 終端文字の後にします。

## <a name="requirements"></a>要件  
**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
