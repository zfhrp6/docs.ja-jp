---
title: GetMethod 関数 (アンマネージ API リファレンス)
description: GetMethod 関数では、メソッドに関する情報を取得します。
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65b8cb74a028892a3494e818f2b523f75e8766a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="getmethod-function"></a>GetMethod 関数
指定したメソッドに関する情報を取得します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`wszName`  
[in]メソッドの名前。 このパラメーターを指定できません`null`し、有効なをポイントする必要があります`LPCWSTR`です。

`lFlags`  
[in]予約されています。 このパラメーターは、0 を指定する必要があります。

`ppInSignature`   
[out]アドレスへのポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)メソッドへの paramteers を説明するインスタンス。 設定されている場合、このパラメーターは無視されます`null`です。 

`ppOutSignature`  
[out]アドレスへのポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)メソッドに out パラメーターを説明するインスタンス。 設定されている場合、このパラメーターは無視されます`null`です。 

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定したプロパティは見つかりませんでした。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx)メソッドです。

Windows の管理を設定できる、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)へのポインター`null`メソッドに in パラメーターがあるない場合。

`ppInSignature`と`ppOutSignature`in および out パラメーターをそれぞれのプロパティとして、説明、`IWbemClassObject`システム クラスのインスタンス[_Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx)です。 指定したプロパティ`ppInsignature`は名前付き **Param * * * n*ここで、 *n*メソッド シグネチャのパラメーターの位置は、(など`Param1`、 `Param2`, などです。)。 指定したプロパティ`ppOutSignature`とも呼ば **Param * * * n*、および戻り値が名前付き**ReturnValue**です。 例および詳細については、次を参照してください。 [IWbemClassObject::GetMethod メソッド](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx)です。

## <a name="requirements"></a>要件  
**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
