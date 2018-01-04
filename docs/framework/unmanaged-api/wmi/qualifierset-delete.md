---
title: "QualifierSet_Delete 関数 (アンマネージ API リファレンス)"
description: "QualifierSet_Delete 関数は、名前で、修飾子を削除します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Delete
helpviewer_keywords: QualifierSet_Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e7b5650a0b47fd8d9b64bb9d0fff3511afe2d43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetdelete-function"></a>QualifierSet_Delete 関数
名前で指定された修飾子を削除します。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`   
[in]ポインター、 [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)インスタンス。

`wszName`   
[in]削除する修飾子の名前。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName`パラメーターが無効です。 |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | この修飾子を削除することはできません。 |
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定した修飾子が見つかりませんでした。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | ローカルの上書きは削除され、親オブジェクトから元の修飾子がスコープを再開します。 |

## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx)メソッドです。

修飾子の伝達の規則により、特定の修飾子可能性があります別のオブジェクトから継承されだけでは、現在のクラスまたはインスタンスでオーバーライドされます。 ここで、`QualifierSet_Delete`メソッドは、継承された値は元に、修飾子をリセットします。 関数は、この場合、ステータス コードを返します`WBEM_S_RESET_TO_DEFAULT`です。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
