---
title: "SpawnDerivedClass 関数 (アンマネージ API リファレンス)"
description: "SpawnDerivedClass 関数は、オブジェクトから派生する新しいオブジェクトを作成します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 51a0dd0013b1bb3898bcc81ee2d64be20a5b6ecc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass 関数
指定したオブジェクトから新しく派生クラス オブジェクトを作成します。    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`lFlags`  
[in]予約されています。 このパラメーターは、0 を指定する必要があります。

`ppNewClass`  
[out]新しいクラス定義のオブジェクトへのポインターを受け取ります。 エラーが発生する場合、新しいオブジェクトが返される、および`ppNewClass`左は変更されていません。 その値にすることはできません`null`です。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | インスタンスからのクラスの生成などの無効な操作が要求されました。 |
| `WBEM_E_INCOMPLETE_CLASS` | ソース クラスが完全に定義されているか、新しい派生クラスは許可されていないために、Windows の管理に登録されています。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` は `null` です。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::SpawnDerivedClass](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx)メソッドです。

`ptr`子オブジェクトの親クラスとなるクラス定義でなければなりません。 返されたオブジェクトでは、現在のオブジェクトのサブクラスになります。

返される新しいオブジェクト`ppNewClass`現在のオブジェクトのサブクラスに自動的になります。 この動作はオーバーライドできません。 サブクラス (派生クラス) を作成できる他の方法はありません。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
