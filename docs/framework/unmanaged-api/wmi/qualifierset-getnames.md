---
title: "QualifierSet_GetNames 関数 (アンマネージ API リファレンス)"
description: "QualifierSet_GetNames 関数は、オブジェクトまたはプロパティから修飾子の名前を取得します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_GetNames
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_GetNames
helpviewer_keywords: QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6077b448c2644f68d12679cf208ee921c2af119a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetgetnames-function"></a>QualifierSet_GetNames 関数
すべての修飾子のまたは現在のオブジェクトまたはプロパティから使用できる特定の修飾子の名前を取得します。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`   
[in]このパラメーターは使用されません。

`ptr`   
[in]ポインター、 [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)インスタンス。

`lFlags`   
[in]次のフラグまたは列挙体に追加するには、どの名前を指定する値のいずれか。

|定数  |[値]  |説明  |
|---------|---------|---------|
|  | 0 | すべての修飾子の名前を返します。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 現在のプロパティまたはオブジェクトに特定の修飾子の名前のみを返します。 <br/> プロパティの: (オーバーライドを含む)、プロパティに特定の修飾子のみを返すし、クラス定義から伝達されたこれらの修飾子されません。 <br/> インスタンス: インスタンス固有の修飾子名のみが返されます。 <br/> クラスの: 派生クラス beiong に特定の修飾子のみを返します。
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | 別のオブジェクトから修飾子の名前のみが反映される戻り値。 <br/> プロパティ: から返される修飾子のみが反映されるこのプロパティに、クラス定義と、プロパティ自体からです。 <br/> インスタンス: クラス定義からこれらの修飾子のみが反映される戻り値。 <br/> クラスの: 戻り値の修飾子名前だけが、親クラスから継承します。 |

`pstrNames`[out]新しい`SAFEARRAY`要求された名前を格納しています。 配列には、0 の要素を持つことができます。 エラーが発生した場合、新しい`SAFEARRAY`は返されません。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 十分なメモリが新しい列挙体を開始します。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx)メソッドです。

修飾子の名前を取得すると、各修飾子名前でアクセスできますを呼び出して、 [QualifierSet_Get](qualifierset-get.md)関数。 

ゼロ修飾子があるためには、指定したオブジェクトのエラーではありませんで文字列の数`pstrNames`返された場合は 0 を指定する場合でも、この関数を返します`WBEM_S_NO_ERROR`です。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
