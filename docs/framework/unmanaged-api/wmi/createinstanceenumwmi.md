---
title: CreateInstanceEnumWmi 関数 (アンマネージ API リファレンス)
description: CreateInstanceEnumWmi 関数では、選択条件を満たす、指定されたクラスのインスタンスを含む列挙子を返します。
ms.date: 11/06/2017
api_name:
- CreateInstanceEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstanceEnumWmi
helpviewer_keywords:
- CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f9297d34b01c03075db67bd904a81e589bfcc10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="createinstanceenumwmi-function"></a>CreateInstanceEnumWmi 関数
指定された選択条件を満たす指定したクラスのインスタンスを返す列挙子を返します。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateInstanceEnumWmi (
   [in] BSTR                    strFilter,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
); 
```  

## <a name="parameters"></a>パラメーター

`strFilter`    
[in]インスタンスが必要となるクラスの名前。 このパラメーターを指定できません`null`です。

`lFlags`   
[in]この関数の動作に影響するフラグの組み合わせ。 次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。 

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 場合は、関数のセットは、現在の接続のロケールのローカライズされた名前空間に格納されている修正済みの修飾子を取得します。 <br/> 指定しない場合、セット、関数は、イミディ エイトの名前空間に格納されている修飾子のみを取得します。 |
| `WBEM_FLAG_DEEP` | 0 | 列挙体には、階層内のすべてのサブクラスとこれが含まれています。 |
| `WBEM_FLAG_SHALLOW` | 1 | 列挙体は、このクラスの純粋なインスタンスのみを含むおよびのサブクラスが見つかりません。 このクラスでプロパティを提供するすべてのインスタンスを除外します。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | フラグは、半同期呼び出しがします。 |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | この関数は、順方向専用の列挙子を返します。 呼び出しを許可しませんが、通常、順方向専用の列挙子は、高速および従来の列挙子よりも少ないメモリを使用して[クローン](clone.md)です。 |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI は、リリースされるまで、enumration 内のオブジェクトへのポインターを保持します。 | 

推奨されるフラグは`WBEM_FLAG_RETURN_IMMEDIATELY`と`WBEM_FLAG_FORWARD_ONLY`最適なパフォーマンスをします。

`pCtx`  
[in]この値は、通常、`null`です。 ポインターはそれ以外の場合、 [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)インスタンスを使用して、要求されたインスタンスを提供しているプロバイダーによって可能性があります。

`ppEnum`  
[out]列挙子へのポインターを受け取ります。

`authLevel`  
[in]承認レベル。

`impLevel` [in]権限借用レベルです。

`pCurrentNamespace`   
[in]ポインター、 [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)を現在の名前空間を表すオブジェクト。

`strUser`   
[in]ユーザー名。 参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。

`strPassword`   
[in]パスワードです。 参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。

`strAuthority`   
[in]ユーザーのドメイン名。 参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | ユーザーには、指定したクラスのインスタンスを表示するアクセス許可がありません。 |
| `WBEM_E_FAILED` | 0x80041001 | 不明なエラーが発生しました。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strFilter` は存在しません。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI は、おそらく停止および再起動されました。 呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | リモート プロシージャ コール (RPC) リンクで、現在のプロセスと WMI との間に失敗しました。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、[で iwbemservices::createclassenum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx)メソッドです。

返された列挙子がゼロの要素を持つことに注意してください。

呼び出して追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。

## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
