---
title: GetNames 関数 (アンマネージ API リファレンス)
description: GetNames 関数では、オブジェクトのプロパティの名前を取得します。
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 108946428cdfadcfb9c653b7e444bf278dfa2782
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="getnames-function"></a>GetNames 関数
一部またはすべてのオブジェクトのプロパティの名前を取得します。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。

`wszQualifierName`  
[in]有効なポインター`LPCWSTR`フィルターの一部として動作する修飾子の名前を指定します。 詳細については、次を参照してください。、[解説](#remarks)セクションです。 このパラメーターは、`null` に設定できます。 

`lFlags`  
[in]ビット フィールドの組み合わせ。 詳細については、次を参照してください。、[解説](#remarks)セクションです。

`pQualifierValue`   
[in]有効なポインター`VARIANT`フィルター値に初期化された構造体。 このパラメーターは、`null` に設定できます。 

`pstrNames`  
[out]A`SAFEARRAY`プロパティ名を格納する構造体。 項目で、このパラメーターは常にへのポインター`null`です。 参照してください、[解説](#remarks)詳細についてはします。 

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 1 つまたは複数のパラメーターが有効でないか、フラグとパラメーターの組み合わせが正しくないが指定されました。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx)メソッドです。

返される名前付きのフラグとパラメーターの組み合わせによって制御されます。 たとえば、関数では、すべてのプロパティの名前またはキーのプロパティの名前のみを返すことができます。  プライマリ フィルターがで指定された、`lFlags`パラメーター、およびその他のパラメーターは、これによって異なります。

フラグの値が`lFlags`ビット フィールドは、


フラグとして渡すことができる、`lEnumFlags`引数は、ビット フィールドで定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。  その他のグループから任意のフラグを使って各グループから 1 つのフラグを組み合わせることができます。 ただし、同じグループにフラグは相互に排他的です。 

| グループ 1 フラグ |[値]  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | すべてのプロパティ名を返します。 `strQualifierName` `pQualifierVal`使用されていません。 |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | 指定した名前の修飾子を持つプロパティのみを返す、`strQualifierName`パラメーター。 このフラグを使用する必要がありますを指定する`strQualifierName`です。 |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  によって指定された名前の修飾子を持たない唯一のプロパティを返す、`strQualifierName`パラメーター。 このフラグを使用する必要がありますを指定する`strQualifierName`です。 |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | によって指定された名前の修飾子を持つプロパティのみを返す、`wszQualifierName`パラメーターで指定されているのと同じ値が設定されても、`pQualifierVal`構造体。 このフラグを使用する場合、両方を指定する必要があります、`wszQualifierName`と`pQualifierValue`です。 |

| グループ 2 フラグ |[値]  |説明  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | キーを定義するプロパティの名前のみを返します。 |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | 戻り値のみプロパティ名オブジェクト参照であります。 |

| フラグのグループ 3 |[値]  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 最派生クラスに属しているプロパティ名のみが返されます。 親クラスからプロパティを除外します。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 親クラスに属しているプロパティ名のみが返されます。 |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | システムのプロパティの名前のみを返します。 |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | 非システムのプロパティの名前のみを返します。 |

関数を常に割り当てる新しい`SAFEARRAY`を返す場合`WBEM_S_NO_ERROR`、および`pstrNames`は常に設定します。 指定したフィルターに一致するプロパティがない場合、返される配列要素がゼロことができます。 以外の場合、値が返されます場合`WBM_S_NO_ERROR`、新しい`SAFEARRAY`構造は返されません。
 
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
