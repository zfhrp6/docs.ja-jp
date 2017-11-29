---
title: "次の関数 (アンマネージ API リファレンス)"
description: "次のように関数 retireves 列挙型で次のプロパティです。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Next
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Next
helpviewer_keywords: Next function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c198a9f9507af583f4718c636cd00c9d65a25695
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="next-function"></a>次の関数
呼び出しで始まる列挙型で次のプロパティを取得[BeginEnumeration](beginenumeration.md)です。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Next (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor     
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`lFlags`  
[in]予約されています。 このパラメーターは、0 を指定する必要があります。

`pstrName`  
[out]新しい`BSTR`プロパティ名を格納しています。 このパラメーターに設定することができます`null`名前が必要ない場合。

`pVal`  
[out]A`VARIANT`プロパティの値が入力されます。 このパラメーターに設定することができます`null`値が必要ない場合。 関数は、エラー コードを返した場合、`VARIANT`に渡される`pVal`左は変更されていません。 

`pvtType`  
[out]ポインター、`CIMTYPE`変数 (、`LONG`にプロパティの型が配置されます)。 このプロパティの値にすることができます、 `VT_NULL_VARIANT`、この場合は、プロパティの実際の型を決定するために必要です。 このパラメーターは指定できますも`null`します。 

`plFlavor`  
[out]`null`、またはプロパティの原点の情報を受信する値。 使用可能な値 [注釈] セクションを参照してください。 

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
| `WBEM_E_UNEXPECTED` | 0x8004101d | 呼び出しが入っていなかった、 [ `BeginEnumeration` ](beginenumeration.md)関数。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 十分なメモリが新しい列挙体を開始します。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | リモート プロシージャは、現在のプロセスと Windows 管理に失敗しました間を呼び出します。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列挙には、プロパティがあります。 |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::Next](https://msdn.microsoft.com/library/aa391453(v=vs.85).aspx)メソッドです。

このメソッドは、システムのプロパティも返します。

プロパティの基になる型がオブジェクトのパスにある、日付または時刻、または他の特別な種類の場合は、し、返された型は十分な情報です。 呼び出し元を確認する必要があります、`CIMTYPE`指定したプロパティのプロパティがオブジェクト参照を日付または時刻、または他の特別な種類を判断します。

場合`plFlavor`は`null`、`LONG`値が次のように、プロパティの原点に関する情報を受け取る。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | プロパティは、標準のシステム プロパティです。 |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | クラスの: このプロパティは、親クラスから継承します。 </br> インスタンス: プロパティは、親クラスから継承されたときに変更されていないインスタンスがします。  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | クラスの: プロパティが、派生クラスに所属します。 </br> インスタンス:; のインスタンスによって、プロパティが変更されました。値が指定された、または修飾子が追加または変更します。 |

## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
