---
title: CompareTo 関数 (アンマネージ API リファレンス)
description: CompareTo 関数では、別の WMI オブジェクトにオブジェクトを比較します。
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db4431da90842f4f96a0f09a2f28dc473d956ee3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="compareto-function"></a>CompareTo 関数
別の Windows 管理オブジェクトにオブジェクトを比較します。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`flags`  
[in]比較検討するオブジェクトの特性を指定するフラグのビットごとの組み合わせ。 参照してください、[解説](#remarks)詳細についてはします。

`pCompareTo`  

[in]比較のオブジェクトです。 `pcompareTo` 有効な[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス; ことはできません`null`です。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 不明なエラーが発生しました。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
| `WBEM_E_UNEXPECTED` | 0x8004101d | 2 番目の呼び出しに`BeginEnumeration`せずに中間の呼び出しが行われた[ `EndEnumeration`](endenumeration.md)です。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
| `WBEM_S_DIFFERENT` | 0x40003 | オブジェクトが異なるです。 |
| `WBEM_S_SAME` | 0 | オブジェクトは、比較フラグに基づいたものと同じです。 |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx)メソッドです。

フラグとして渡すことができる、`lEnumFlags`で引数が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。 次のフラグのビットごとの組み合わせを指定することによって、比較に関係する個々 の特性を指定できます。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | ソース (サーバーと、元の名前空間) を無視します。 |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | すべての修飾子を無視する (含む**キー**と**動的**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | プロパティの既定値を無視します。 このフラグは、クラスの比較にのみ適用されます。 |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | 修飾子のフレーバーを無視します。 このフラグはまだ修飾子を考慮に入れたが伝達規則などのフレーバーの区別を無視、制限を上書きします。 |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | 文字列値の比較で大文字小文字を区別します。 これには、文字列と修飾子の値の両方が適用されます。 プロパティと修飾子の名前の比較は、このフラグが設定されているかに関係なく大文字小文字を区別は常にします。 |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | 比較対象となるオブジェクトが同じクラスのインスタンスであると仮定します。 そのため、このフラグは、インスタンスに関連する情報のみを比較します。 このフラグを使用して、パフォーマンスを最適化します。 同じクラスのオブジェクトは場合、結果は定義されていません。 |

または、次のように 1 つの複合フラグを指定できます。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | 比較のすべての機能を検討してください。 |

## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
