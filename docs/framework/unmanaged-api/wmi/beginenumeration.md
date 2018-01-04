---
title: "BeginEnumeration 関数 (アンマネージ API リファレンス)"
description: "BeginEnumeration 関数が列挙体の先頭に、列挙子をリセットします。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BeginEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BeginEnumeration
helpviewer_keywords: BeginEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90c3e8448a61145290ea4a75b1d38f7ae010cb9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="beginenumeration-function"></a>BeginEnumeration 関数
列挙体の先頭に戻るには、列挙子をリセットします。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`lEnumFlags`  
[in]フラグまたはで説明されている値のビットごとの組み合わせ、[解説](#remarks)列挙体に含まれるプロパティを制御するセクション。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | フラグの組み合わせ`lEnumFlags`が無効か、無効な引数が指定されました。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 2 番目の呼び出しに`BeginEnumeration`せずに中間の呼び出しが行われた[ `EndEnumeration`](endenumeration.md)です。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 十分なメモリが新しい列挙体を開始します。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::BeginEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)メソッドです。

フラグとして渡すことができる、`lEnumFlags`で引数が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。  その他のグループから任意のフラグを使って各グループから 1 つのフラグを組み合わせることができます。 ただし、同じグループにフラグは相互に排他的です。 

**グループ 1**

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | キーのみを構成するプロパティが含まれます。 |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | オブジェクト参照のみであるプロパティが含まれます。 |

**グループ 2**

定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | システムのプロパティのみを列挙型を制限します。 |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | ローカルおよび伝達されたプロパティが含まれますが、列挙体からシステムのプロパティを除外します。 |

クラス。

定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | クラスの定義でオーバーライドされたプロパティ、列挙型を制限します。 |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | 現在のクラス定義でオーバーライドされたプロパティ、およびクラスで定義されている新しいプロパティに列挙型を制限します。 |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | A がに対して適用するマスク (フラグ) ではなく、`lEnumFlags`いずれかを確認する値`WBEM_FLAG_CLASS_OVERRIDES_ONLY`または`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES`設定されています。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 定義またはクラス自身で変更されるプロパティ、列挙型を制限します。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 基本クラスから継承されたプロパティ、列挙型を制限します。 |

インスタンス。

定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 定義またはクラス自身で変更されるプロパティ、列挙型を制限します。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 基本クラスから継承されたプロパティ、列挙型を制限します。 |


## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
