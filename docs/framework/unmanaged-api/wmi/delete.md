---
title: "Delete 関数 (アンマネージ API リファレンス)"
description: "Delete 関数は、CIM クラス定義から、指定されたプロパティとその修飾子のすべてを削除します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 30f5bf651990cafe06811019cf2b3d92f866f646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="delete-function"></a>関数を削除します。
CIM クラス定義から、指定したプロパティとその修飾子のすべてを削除します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`wszName`  
[in]削除するプロパティの名前。 `wszName`有効なポインターである必要があります`LPCWSTR`です。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 不明なエラーが発生しました。 |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | プロパティを削除することはできません。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszzName` が無効です。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | 指定したプロパティが存在しません。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがありません。 |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | プロパティは、基本クラスから継承されます。 |
| `WBEM_E_SYSTEM_PROPERTY` | | プロパティは、システム プロパティです。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | 関数は、現在のクラスの上書きの既定値を削除します。 親クラスでこのプロパティの既定値は、reactiviated されました。 | 

## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::Delete](https://msdn.microsoft.com/library/aa391438(v=vs.85).aspx)メソッドです。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
