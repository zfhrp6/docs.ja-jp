---
title: "NextMethod 関数 (アンマネージ API リファレンス)"
description: "NextMethod 関数では、列挙体の次のメソッドを取得します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: NextMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: NextMethod
helpviewer_keywords: NextMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b886b3ecbd1d5b5b8d212846b2bd8291fa43909
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="nextmethod-function"></a>NextMethod 関数
呼び出しで始まる列挙体の次のメソッドを取得[BeginMethodEnumeration](beginmethodenumeration.md)です。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`lFlags`  
[in]予約されています。 このパラメーターは、0 を指定する必要があります。

`pName`  
[out]指すポインター`null`呼び出しの前にします。 ときに、関数からの新しいアドレス`BSTR`メソッド名を格納しています。 

`ppSignatureIn`  
[out]ポインターを受け取るポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)を格納している、`in`メソッドのパラメーターです。 

`ppSignatureOut`  
[out]ポインターを受け取るポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)を格納している、`out`メソッドのパラメーターです。 

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | 呼び出しが入っていなかった、 [ `BeginEnumeration` ](beginenumeration.md)関数。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列挙には、プロパティがあります。 |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx)メソッドです。

呼び出し元が呼び出しによって列挙のシーケンスを開始、 [BeginMethodEnumeration](beginmethodenumeration.md)関数、および関数が戻るまで [NextMethod] 関数を呼び出す`WBEM_S_NO_MORE_DATA`です。 必要に応じて、呼び出し元が完了すると、シーケンスを呼び出して[EndMethodEnumeration](endmethodenumeration.md)です。 呼び出し元が呼び出すことで列挙体を早期終了可能性があります[EndMethodEnumeration](endmethodenumeration.md)いつでもできます。

## <a name="example"></a>例

C++ の例では、次を参照してください。、 [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx)メソッドです。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
