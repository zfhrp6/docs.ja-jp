---
title: "BeginMethodEnumeration 関数 (アンマネージ API リファレンス)"
description: "オブジェクトのメソッドの列挙を開始する BeginMethodEnumeration 関数"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7d843c40a8ab0dd1c48a08126b8c7472505a1732
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="beginenumeration-function"></a>BeginEnumeration 関数
オブジェクトの使用可能なメソッドの列挙を開始します。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
``` 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`lEnumFlags`  
[in]ゼロ (0) のすべてのメソッド、または列挙体のスコープを指定するフラグ。 次のフラグが定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 列挙型クラス自体で定義されているメソッドを制限します。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 基本クラスから継承されたプロパティ、列挙型を制限します。 |

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lEnnumFlags`ゼロ以外は、指定したフラグのいずれか。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx)メソッドです。

このメソッドの呼び出しは、現在のオブジェクトがクラス定義である場合にのみサポートされます。 メソッドの操作からは使用できない[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンスを指すポインターです。 メソッドが列挙される順序は、特定のインスタンスのバリアントすることは保証[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)です。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
