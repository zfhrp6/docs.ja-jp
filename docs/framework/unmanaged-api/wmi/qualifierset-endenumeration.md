---
title: QualifierSet_EndEnumeration 関数 (アンマネージ API リファレンス)
description: QualifierSet_EndEnumeration 関数は、列挙を終了します。
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e24acdde486f377cc9187aac088ce7a611cd4eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="qualifiersetendenumeration-function"></a>QualifierSet_EndEnumeration 関数
呼び出しで開始された列挙の終了、 [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)関数。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`   
[in]ポインター、 [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)インスタンス。

## <a name="return-value"></a>戻り値

この関数によって返される次の値がで定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができます、定数としてコードで定義します。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemQualifierSet::EndEnumeration](https://msdn.microsoft.com/library/aa391865(v=vs.85).aspx)メソッドです。

この呼び出しは、推奨しますが、必要ありません。 すぐに、列挙体に関連付けられているリソースを解放します。

## <a name="requirements"></a>要件  

**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
**ヘッダー:** WMINet_Utils.idl  
  
**.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
