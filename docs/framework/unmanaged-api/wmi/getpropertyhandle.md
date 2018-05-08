---
title: GetPropertyHandle 関数 (アンマネージ API リファレンス)
description: GetPropertyHandle 関数では、プロパティの識別子を管理する一意のハンドルを返します。
ms.date: 11/06/2017
api_name:
- GetPropertyHandle
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyHandle
helpviewer_keywords:
- GetPropertyHandle function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 103e81dfa0e455157cfce5914b711347b15b578d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="getpropertyhandle-function"></a>GetPropertyHandle 関数
プロパティを識別する一意のハンドルを返します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```  
HRESULT GetPropertyHandle (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx)インスタンス。

`wszPropertyName`  
[in]プロパティ名を含む UTF16 エンコード characaters の null で終わる文字列。   

`pType`  
[out]ポインター、 [ `CIMTYPE` ](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx)プロパティの CIM 型を表す列挙体メンバーです。

`pHandle`   
[out]プロパティのハンドルを格納する整数へのポインター。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定したプロパティ名が見つかりませんでした。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
|`WBEM_E_NOT_SUPPORTED` | 0x8004100c | 要求されたプロパティの型は、`CIM_OBJECT`または`CIM_ARRAY`です。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx)メソッドです。

このハンドルを使用するにを使用する場合は、プロパティを識別する[IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx)プロパティの値を読み取ったり書き込んだりする方法です。

ハンドルを以外のすべてのデータ型のプロパティを取得できる`CIM_OBJECT`と`CIM_ARRAY`です。 クラスのすべてのインスタンス ハンドルの作業が返されます。

## <a name="requirements"></a>要件  
**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
