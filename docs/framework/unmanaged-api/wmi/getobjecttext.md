---
title: GetObjectText 関数 (アンマネージ API リファレンス)
description: GetObjectText 関数は、MOF 構文では、オブジェクトのテキストのレンダリングを返します。
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2f0e766a3a310bdb58f7cbffd8d49404eb5e0b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="getobjecttext-function"></a>GetObjectText 関数
管理オブジェクト フォーマット (MOF) の構文では、オブジェクトのテキストのレンダリングを返します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`lFlags`  
[in]通常は 0 です。 場合`WBEM_FLAG_NO_FLAVORS`(0x1) を指定すると、修飾子は伝達またはフレーバーの情報がない場合に含まれています。

`pstrObjectText`   
[out]ポインター、`null`エントリです。 戻り時に、新しく割り当てられた`BSTR`を含むオブジェクトの MOF 構文レンダリングします。  

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx)メソッドです。

MOF テキストを返すには、オブジェクトに関するすべての情報が、元のオブジェクトを作成し直すことができる MOF コンパイラのための十分な情報のみがありません。 たとえば、伝達された修飾子または親クラスのプロパティは含まれません。

次のアルゴリズムは、メソッドのパラメーターのテキストを再構築に使用されます。

1. パラメーターは、その識別子の値の順序で resequenced されます。
1. パラメーターとして指定されている`[in]`と`[out]`パラメーターを 1 つに結合されます。
 
`pstrObjectText` ポインターにする必要があります、`null`有効では、メソッドを呼び出す前に、ポインターの割り当てを解除できませんが、文字列をポイントする必要がありますいない関数が呼び出されるとします。 します。

## <a name="requirements"></a>要件  
**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
