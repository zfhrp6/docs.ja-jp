---
title: "QualifierSet_Put 関数 (アンマネージ API リファレンス)"
description: "QualifierSet_Put 関数は、名前付きの修飾子とその値を書き込みます。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1bf5c6dbf0f707942d58f4d7cf155636f0532724
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetput-function"></a>QualifierSet_Put 関数
名前付きの修飾子と値を書き込みます。 新しい修飾子には、同じ名前の前の値が上書きされます。 修飾子が存在しない場合は作成されます。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`   
[in]このパラメーターは使用されません。

`ptr`   
[in]ポインター、 [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)インスタンス。

`wszName`   
[in]書き込む修飾子の名前。

`pVal`[in]有効なポインター`VARIANT`書き込む修飾子を格納しています。 このパラメーターを指定できません`null`です。

`lFlavor`[in]この修飾子に必要な修飾子のフレーバーを定義する次の定数の 1 つ。 既定値は`WBEM_FLAVOR_OVERRIDABLE`(0) です。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | 修飾子は、派生クラスまたはインスタンスでオーバーライドできます。 **これは、既定値です。** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | この修飾子は、インスタンスに反映されます。 |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | 修飾子は、派生クラスに伝達されます。 |
| ' WBEM_FLAVOR_NOT_OVERRIDABLE | 0x10 | この修飾子は、派生クラスまたはインスタンスではオーバーライドできません。 |
| ' WBEM_FLAVOR_AMENDED | 0x80 | 修飾子はローカライズされます。 |

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | 指定する無効なが試行されました、**キー**することはできません、キー プロパティでの修飾子です。 キーが指定されて om c; オブジェクトの定義はアセンブリと、インスタンスごとに変更することはできません。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | `pVal`パラメーターが正しい型ではありません。 |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | 呼び出すことはできません、`QualifierSet_Put`修飾子のメソッド オーバーライドの所有するオブジェクトが許可されていません。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx)メソッドです。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
