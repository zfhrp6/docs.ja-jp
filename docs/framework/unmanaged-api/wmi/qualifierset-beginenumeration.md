---
title: "QualifierSet_BeginEnumeration 関数 (アンマネージ API リファレンス)"
description: "QualifierSet_BeginEnumeration 関数では、オブジェクトの修飾子の列挙子をリセットします。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_BeginEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_BeginEnumeration
helpviewer_keywords: QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 440dde03f4ed138a33eb6f817723d7c5c74f6d46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetbeginenumeration-function"></a>QualifierSet_BeginEnumeration 関数
列挙体の先頭にオブジェクトの修飾子の列挙子をリセットします。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`   
[in]このパラメーターは使用されません。

`ptr`   
[in]ポインター、 [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)インスタンス。

`lFlags`   
[in]フラグまたはで説明されている値のビットごとの組み合わせ、[解説](#remarks)セクションに含める列挙体の修飾子を指定します。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lFlags`パラメーターが無効です。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 2 番目の呼び出しに`QualifierSet_BeginEnumeration`せずに中間の呼び出しが行われた[ `QualifierSet_EndEnumeration`](qualifierset-endenumeration.md)です。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 十分なメモリが新しい列挙体を開始します。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemQualifierSet::BeginEnumeration](https://msdn.microsoft.com/library/aa391861(v=vs.85).aspx)メソッドです。

すべてのオブジェクトに対する修飾子を列挙するには、最初の呼び出しの前にこのメソッドを呼び出す[QualifierSet_Next](qualifierset-next.md)です。 修飾子が列挙される順序が指定した列挙体のバリアントを解除します。

フラグとして渡すことができる、`lEnumFlags`で引数が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。   

|定数  |[値]  |説明  |
|---------|---------|---------|
|  | 0 | すべての修飾子の名前を返します。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 現在のプロパティまたはオブジェクトに特定の修飾子の名前のみを返します。 <br/> プロパティの: (オーバーライドを含む)、プロパティに特定の修飾子のみを返すし、クラス定義から伝達されたこれらの修飾子されません。 <br/> インスタンス: インスタンス固有の修飾子名のみが返されます。 <br/> クラスの: 派生クラス beiong に特定の修飾子のみを返します。
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | 別のオブジェクトから修飾子の名前のみが反映される戻り値。 <br/> プロパティ: から返される修飾子のみが反映されるこのプロパティに、クラス定義と、プロパティ自体からです。 <br/> インスタンス: クラス定義からこれらの修飾子のみが反映される戻り値。 <br/> クラスの: 戻り値の修飾子名前だけが、親クラスから継承します。 |

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
