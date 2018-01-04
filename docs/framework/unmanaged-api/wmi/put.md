---
title: "Put 関数 (アンマネージ API リファレンス)"
description: "Put 関数では、名前付きプロパティに新しい値を割り当てます。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Put
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Put
helpviewer_keywords: Put function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09d3edc74b34688d5cc36e688f634850cfb60910
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="put-function"></a>Put 関数
新しい値を名前付きプロパティを設定します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`wszName`  
[in]プロパティの名前です。 このパラメーターを指定できません`null`です。

`lFlags`  
[in]予約されています。 このパラメーターは、0 を指定する必要があります。

`pVal`   
[in]有効なポインター`VARIANT`新しいプロパティ値になります。 場合`pVal`は`null`を指すか、`VARIANT`型の`VT_NULL`、プロパティに設定`null`です。 

`vtType`  
[in]型`VARIANT`によって示される`pVal`です。 参照してください、[解説](#remarks)詳細についてはします。
 

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 1 つまたは複数のパラメーターが有効ではありません。 |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | プロパティの型は認識されません。 クラスが既に存在する場合は、クラスのインスタンスを作成するときに、この値が返されます。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | インスタンス: ことを示します`pVal`を指す、`VARIANT`プロパティの型が正しくないのです。 <br/> クラス定義: プロパティは、親クラスに既に存在し、新しい COM 型が古い COM 型を異なる。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。 |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx)メソッドです。

この関数は常に、新しい現在のプロパティ値を上書きします。 場合、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)はクラス定義、指す`Put`作成するか、プロパティ値を更新します。 ときに[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) CIM のインスタンスを指す`Put`更新プログラムのプロパティの値だけです。`Put`プロパティ値を作成できません。

`__CLASS`システム プロパティは書き込み可能なクラスの作成時に場合にのみは空白にできません。 その他のすべてのシステム プロパティとは、読み取り専用です。

ユーザーは、アンダー スコア (「_ _」) で開始または終了する名前を持つプロパティを作成することはできません。 これはシステム クラスとプロパティの予約されています。

プロパティ設定されている場合、`Put`親クラスで関数が存在する場合、プロパティの型が、親クラスの型と一致しませんしない限り、プロパティの既定値を変更します。 プロパティが存在しないため、型の不一致は、プロパティが ceated を使用します。

使用して、`vtType`パラメーター CIM クラス定義に新しいプロパティを作成する場合にのみと`pVal`は`null`を指すか、`VARIANT`型の`VT_NULL`します。 ここで、`vType`パラメーター プロパティの CIM 型を指定します。 その他のすべてのケースで`vtType`0 にする必要があります。 `vtType`基になるオブジェクトがインスタンスの場合も、0 をする必要があります (場合でも`Val`は`null`) ため、プロパティの型は固定され変更できません。   

## <a name="example"></a>例

例については、次を参照してください。、 [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx)メソッドです。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
