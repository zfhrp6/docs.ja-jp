---
title: "GetMethodQualifierSet 関数 (アンマネージ API リファレンス)"
description: "GetMethodQualifierSet 関数は、メソッドの修飾子のセットを取得します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethodQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethodQualifierSet
helpviewer_keywords: GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2999bef31576cf2bc025868260c2b1782a9b69f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getmethodqualifierset-function"></a>GetMethodQualifierSet 関数
特定のメソッドの設定、修飾子を取得します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`wszMethod`  
[in]メソッドの名前。 `wszMethod`有効なをポイントする必要があります`LPCWSTR`です。 

`ppQualSet`  
[out]メソッドの修飾子にアクセスできるようにするインターフェイス ポインターを受け取ります。 `ppQualSet` として `null` を使用することはできません。 かどうかは、エラーが発生し、新しいオブジェクトが返されない、ポインターが指すように設定`null`です。 

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定されたメソッドが存在しません。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが`null`です。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx)メソッドです。 

この関数に対する呼び出しがサポートされるは、現在のオブジェクトが、CIM クラスの定義である場合にのみです。 メソッドの操作では使用できません[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) CIM インスタンスを指す ponters です。

各メソッドには、独自の修飾子があるため、 [IWbemQualifierSet ポインター](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)により、呼び出し元を追加、編集、またはこれらの修飾子を削除します。

## <a name="requirements"></a>必要条件  
**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
