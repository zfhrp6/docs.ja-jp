---
title: "GetPropertyQualifierSet 関数 (アンマネージ API リファレンス)"
description: "GetPropertyQualifierSet 関数では、プロパティの設定、修飾子を取得します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyQualifierSet
helpviewer_keywords: GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ca2981c8833abaafd5d206b66d6e91f34e2c91d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getpropertyqualifierset-function"></a>GetPropertyQualifierSet 関数
特定のプロパティの設定、修飾子を取得します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```  
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`wszMethod`  
[in]プロパティ名。 `wszProperty`有効なをポイントする必要があります`LPCWSTR`です。 

`ppQualSet`  
[out]プロパティの修飾子にアクセスできるようにするインターフェイス ポインターを受け取ります。 `ppQualSet` として `null` を使用することはできません。 かどうかは、エラーが発生し、新しいオブジェクトが返されない、ポインターが指すように設定`null`です。 

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | 指定されたメソッドが存在しません。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが`null`です。 |
| `WBEM_E_SYSTEM_PROPERTY` | 0x80041030 | 関数は、システム プロパティの修飾子を取得しようとします。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx)メソッドです。 

この関数に対する呼び出しがサポートされるは、現在のオブジェクトが、CIM クラスの定義である場合にのみです。 メソッドの操作では使用できません[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) CIM インスタンスを指す ponters です。

各メソッドには、独自の修飾子があるため、 [IWbemQualifierSet ポインター](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)により、呼び出し元を追加、編集、またはこれらの修飾子を削除します。

システムのプロパティに修飾子があるないため、関数を返します`WBEM_E_SYSTEM_PROPERTY`を取得しようとすると、 [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)システム プロパティへのポインター。

## <a name="requirements"></a>必要条件  
**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
