---
title: QualifierSet_Get 関数 (アンマネージ API リファレンス)
description: QualifierSet_Get 関数では、名前付きの修飾子を取得します。
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1bc57ab45a0452d9e3a50f0ab2de786ad73204a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458648"
---
# <a name="qualifiersetget-function"></a>QualifierSet_Get 関数
指定した名前付き修飾子を取得します。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT QualifierSet_Get (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`   
[in]このパラメーターは使用されません。

`ptr`   
[in]ポインター、 [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)インスタンス。

`wszName`   
[in]値が要求された修飾子の名前。

`lFlags`   
[in]予約されています。 このパラメーターは、0 を指定する必要があります。

`pVal`   
[out]成功した場合、正しい型および修飾子の値。 関数が失敗した場合、`VARIANT`によって示される`pVal`は変更されません。 このパラメーターが場合`null`パラメーターは無視されます。

`plFlavor`   
[out]修飾子フレーバーのビットを要求された修飾子を受け取る long 整数へのポインター。 このパラメーターを指定できますフレーバー情報が必要ない場合`null`です。 

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定した修飾子が存在しません。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemQualifierSet::Get](https://msdn.microsoft.com/library/aa391867(v=vs.85).aspx)メソッドです。

## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
