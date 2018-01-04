---
title: "ExecQueryWmi 関数 (アンマネージ API リファレンス)"
description: "ExecQueryWmi 関数は、オブジェクトを取得するクエリを実行します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ExecQueryWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ExecQueryWmi
helpviewer_keywords: ExecQueryWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 872109cb0472a8404c492c2867429fe783f898eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="execquerywmi-function"></a>ExecQueryWmi 関数
オブジェクトを取得するクエリを実行します。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ExecQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
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

`strQueryLanguage`    
[in]Windows 管理でサポートされる有効なクエリ言語での文字列です。 WMI クエリ言語の頭字語である"WQL"でなければなりません。

`strQuery`  
[in]クエリのテキスト。 このパラメーターを指定できません`null`です。

`lFlags`   
[in]この関数の動作に影響するフラグの組み合わせ。 次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。 

| 定数 | [値]  | 説明  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 場合は、関数のセットは、現在の接続のロケールのローカライズされた名前空間に格納されている修正済みの修飾子を取得します。 <br/> 指定しない場合、セット、関数は、イミディ エイトの名前空間に格納されている修飾子のみを取得します。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | フラグは、半同期呼び出しがします。 |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | この関数は、順方向専用の列挙子を返します。 呼び出しを許可しませんが、通常、順方向専用の列挙子は、高速および従来の列挙子よりも少ないメモリを使用して[クローン](clone.md)です。 |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI は、リリースされるまで、enumration 内のオブジェクトへのポインターを保持します。 | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | 0x100 | 返されるオブジェクトがあるのに十分な情報にためことにより、そのシステムのプロパティなど**_ _path**、 **_relpath**、および**__SERVER**、されない`null`です。 |
| `WBEM_FLAG_PROTOTYPE` | 2 | このフラグは、プロトタイプの作成に使用されます。 クエリは実行されませんし、代わりに、よくある結果オブジェクトのようなオブジェクトを返します。 |
| `WBEM_FLAG_DIRECT_READ` | 0x200 | 原因は直接、親クラス、または任意のサブクラスに関係なく指定されたクラスのプロバイダーへのアクセスです。 |

推奨されるフラグは`WBEM_FLAG_RETURN_IMMEDIATELY`と`WBEM_FLAG_FORWARD_ONLY`最適なパフォーマンスをします。

`pCtx`  
[in]この値は、通常、`null`です。 ポインターはそれ以外の場合、 [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)要求されたクラスを提供しているプロバイダーで使用できるインスタンスです。 

`ppEnum`  
[out]エラーが発生しなかった場合は、クエリの結果セット内のインスタンスを取得する呼び出し元を許可する列挙子へのポインターを受け取ります。 クエリでは、0 個のインスタンスを含む結果セットを持つことができます。 参照してください、[解説](#remarks)詳細についてはします。

`authLevel`  
[in]承認レベル。

`impLevel`[in]権限借用レベルです。

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
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | ユーザーには、1 つ以上の関数が返すことができるクラスを表示するアクセス許可がありません。 |
| `WBEM_E_FAILED` | 0x80041001 | 不明なエラーが発生しました。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | クエリでは、構文エラーがありました。 |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | 要求されたクエリ言語がサポートされていません。 |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | クエリが複雑すぎます。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI は、おそらく停止および再起動されました。 呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | リモート プロシージャ コール (RPC) リンクで、現在のプロセスと WMI との間に失敗しました。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | クエリでは、存在しないクラスを指定します。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx)メソッドです。

この関数で指定されたクエリの処理、`strQuery`パラメーターと、呼び出し元が、クエリの結果をアクセス列挙子を作成します。 列挙子がへのポインター、 [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx)インターフェイス以外のクエリ結果で利用できるクラス オブジェクトのインスタンスである、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx)インターフェイスです。

数に制限は`AND`と`OR`WQL クエリで使用できるキーワード。 多数の複雑なクエリで使用される WQL キーワードには、WMI を返す可能性があります、 `WBEM_E_QUOTA_VIOLATION` (または 0x8004106c) としてのエラー コード、`HRESULT`値。 WQL のキーワードの制限は、どの程度複雑なクエリがによって異なります。

呼び出して追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
