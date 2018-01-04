---
title: "InheritsFrom 関数 (アンマネージ API リファレンス)"
description: "InheritsFrom 関数は、クラスまたはインスタンスが特定の親クラスから派生しているかどうかを決定します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: InheritsFrom
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: InheritsFrom
helpviewer_keywords: InheritsFrom function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0dce964829399e6761152a8ff424671b47cc6eb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="inheritsfrom-function"></a>InheritsFrom 関数
現在のクラスまたはインスタンスが指定された親クラスから派生するかどうかを判断します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`wszAncestor`  
[in]クラスの名前です。 `wszAncestor`有効なをポイントする必要があります`LPCWSTR`です。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | 0 | 現在のオブジェクトから継承`wszAncestor`です。  |
| `WBEM_S_FALSE` | 1 | 現在のオブジェクトを継承しない`wszAncestor`です。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszAncestor` は `null` です。 |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx)メソッドです。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
