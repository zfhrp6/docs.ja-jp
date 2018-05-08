---
title: ExecNotificationQueryWmi 関数 (アンマネージ API リファレンス)
description: ExecNotificationQueryWmi 関数は、イベントを受信するクエリを実行します。
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b5c26ab9c273b134915eea39078a83f569bcd32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="execnotificationquerywmi-function"></a>ExecNotificationQueryWmi 関数
イベントを受信するクエリを実行します。 呼び出しが、すぐに返され、受信したときに、呼び出し元がイベントの返された列挙子をポーリングすることです。 返された列挙子を解放するには、クエリが取り消されます。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ExecNotificationQueryWmi (
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
[in]この関数の動作に影響する次の 2 つのフラグの組み合わせ。 これらの値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。 

| 定数 | [値]  | 説明  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | フラグは、半同期呼び出しがします。 このフラグが設定されていない場合、呼び出しが失敗します。 これは、イベントが継続的に、受信したため、ユーザーは、返された列挙子をポーリングする必要があります。 この呼び出しを無期限にブロックするようにするが不可能です。 |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | この関数は、順方向専用の列挙子を返します。 呼び出しを許可しませんが、通常、順方向専用の列挙子は、高速および従来の列挙子よりも少ないメモリを使用して[クローン](clone.md)です。 |

`pCtx`  
[in]この値は、通常、`null`です。 ポインターはそれ以外の場合、 [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)要求イベントを提供しているプロバイダーで使用できるインスタンスです。 

`ppEnum`  
[out]エラーが発生しなかった場合は、クエリの結果セット内のインスタンスを取得する呼び出し元を許可する列挙子へのポインターを受け取ります。 参照してください、[解説](#remarks)詳細についてはします。

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
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | ユーザーには、1 つ以上の関数が返すことができるクラスを表示するアクセス許可がありません。 |
| `WBEM_E_FAILED` | 0x80041001 | 不明なエラーが発生しました。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | クエリでは、存在しないクラスを指定します。 |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | 0x80042002 | イベントの配信にあまり有効桁数が要求されました。 大規模なポーリング許容範囲を指定する必要があります。 |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | 0x80042001 | クエリ requess Windows 管理より多くの情報を提供できます。 これは、`HRESULT`イベント クエリが名前空間のすべてのオブジェクトをポーリングする要求の結果が返されます。 |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | クエリでは、構文エラーがありました。 |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | 要求されたクエリ言語がサポートされていません。 |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | クエリが複雑すぎます。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI は、おそらく停止および再起動されました。 呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | リモート プロシージャ コール (RPC) リンクで、現在のプロセスと WMI との間に失敗しました。 |
| `WBEM_E_UNPARSABLE_QUERY` | 0x80041058 | クエリを解析できません。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemServices::ExecNotificationQuery](https://msdn.microsoft.com/library/aa392105(v=vs.85).aspx)メソッドです。

関数から返された後に呼び出し元は、定期的に渡されます、返された`ppEnum`オブジェクトを[次](next.md)かどうか、提供されているイベントを表示する関数。

数に制限は`AND`と`OR`WQL クエリで使用できるキーワード。 多数の複雑なクエリで使用される WQL キーワードには、WMI を返す可能性があります、 `WBEM_E_QUOTA_VIOLATION` (または 0x8004106c) としてのエラー コード、`HRESULT`値。 WQL のキーワードの制限は、どの程度複雑なクエリがによって異なります。

呼び出して追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。

## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
