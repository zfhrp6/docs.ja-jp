---
title: "QualifierSet_Next 関数 (アンマネージ API リファレンス)"
description: "QualifierSet_Next 関数では、列挙体の次の修飾子を取得します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Next
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Next
helpviewer_keywords: QualifierSet_Next function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01a9c9d162039547849597aaa9c8a6fa38a31455
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetnext-function"></a>QualifierSet_Next 関数
呼び出しの使用を開始する列挙体の次の修飾子を取得、 [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)関数。   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`   
[in]このパラメーターは使用されません。

`ptr`   
[in]ポインター、 [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)インスタンス。

`lFlags`   
[in]予約されています。 このパラメーターは、0 を指定する必要があります。

`pstrName`   
[out]修飾子の名前。 場合`null`、このパラメーターは無視されます。 それ以外の場合、`pstrName`指す必要がありますいない有効な`BSTR`またはメモリ リークが発生します。 かどうかは null でない関数を常に割り当てる新しい`BSTR`を返す場合`WBEM_S_NO_ERROR`です。

`pVal`   
[out]成功した場合、修飾子の値。 関数が失敗した場合、`VARIANT`によって示される`pVal`は変更されません。 このパラメーターが場合`null`パラメーターは無視されます。

`plFlavor`   
[out]修飾子の種類を受け取る long 整数へのポインター。 このパラメーターを指定できますフレーバー情報が必要ない場合`null`です。 

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 呼び出し元を呼び出さなかった[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)です。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 十分なメモリが新しい列挙体を開始します。 |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 複数修飾子は、列挙体に残されます。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx)メソッドです。

呼び出す、`QualifierSet_Next`関数の戻り値まで、すべての修飾子を列挙するには、繰り返し関数`WBEM_S_NO_MORE_DATA`です。 列挙体を早い段階を終了するには、呼び出し、 [QualifierSet_EndEnumeration](qualifierset-endenumeration.md)関数。

列挙体の中に返された修飾子の順序は定義されません。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
