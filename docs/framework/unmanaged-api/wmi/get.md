---
title: "Get 関数 (アンマネージ API リファレンス)"
description: "Get 関数は、指定されたプロパティ値を取得します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69312030689ab1b87e3aadd040395f06e1c94ac8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="get-function"></a>Get 関数
存在する場合は、指定されたプロパティ値を取得します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```  
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
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

`wszName`  
[in]プロパティの名前です。

`lFlags`[in]予約されています。 このパラメーターは、0 を指定する必要があります。

`pVal`[out]関数が正常に返された場合の値が含まれています、`wszName`プロパティです。 `pval`引数には、正しい型および修飾子の値が割り当てられています。

`pvtType`[out]関数が正常に返された場合は、 [CIM 型の定数](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx)プロパティの型を示すです。 その値にはあります`null`です。 

`plFlavor`[out]関数が正常に返された場合は、プロパティの原点に関する情報を受け取ります。 その値を指定できます`null`、またはいずれかで定義されている次の WBEM_FLAVOR_TYPE 定数の*WbemCli.h*ヘッダー ファイル。 

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | プロパティは、標準のシステム プロパティです。 |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | クラスの: このプロパティは、親クラスから継承します。 </br> インスタンス: プロパティは、親クラスから継承されたときに変更されていないインスタンスがします。  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | クラスの: プロパティが、派生クラスに所属します。 </br> インスタンス:; のインスタンスによって、プロパティが変更されました。値が指定された、または修飾子が追加または変更します。 |

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 1 つまたは複数のパラメーターが有効ではありません。 |
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定したプロパティは見つかりませんでした。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx)メソッドです。

`Get`関数では、システムのプロパティを返すこともできます。

`pVal`引数には、正しい型および修飾子と COM の値が割り当てられている[VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx)関数

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
