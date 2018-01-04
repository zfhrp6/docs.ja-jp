---
title: "GetMethodOrigin 関数 (アンマネージ API リファレンス)"
description: "GetMethodOrigin 関数では、メソッドが宣言されるクラスを決定します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethodOrigin
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethodOrigin
helpviewer_keywords: GetMethodOrigin function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a97376b459a5d9cce9b18ff692ac4c7535a24a56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getmethodorigin-function"></a>GetMethodOrigin 関数
メソッドが宣言されるクラスを決定します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`wszMethodName`  
[in]所有するクラスが要求されているオブジェクトのメソッドの名前。 

`pstrClassName`  
[out]メソッドを所有するクラスの名前を受け取ります。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定されたメソッドが見つかりませんでした。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 1 つまたは複数のパラメーターが有効ではありません。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::GetMethodOrigin](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx)メソッドです。

クラスは、1 つまたは複数の基底クラスからメソッドを継承することができます、ために、開発者は多くの場合に特定のメソッドが定義されているクラスを確認します。

`pstrClassName`パラメーターは、有効なを指していない必要があります`BSTR`ため、これは、関数が呼び出される前に、`out`パラメーターです。 この関数が返された後に、ポインターが割り当て解除されません。

## <a name="requirements"></a>必要条件  
**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
