---
title: ConnectServerWmi 関数 (アンマネージ API リファレンス)
description: ConnectServerWmi 関数では、DCOM を使用して、WMI 名前空間への接続を作成します。
ms.date: 11/06/2017
api_name:
- ConnectServerWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ConnectServerWmi
helpviewer_keywords:
- ConnectServerWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de8447b9b090fc7f53df23346d61932bcb4dd6ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="connectserverwmi-function"></a>ConnectServerWmi 関数
指定したコンピューターで WMI 名前空間に使用する DCOM による接続を作成します。  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel, 
   [in] DWORD              authLevel
);
```  
## <a name="parameters"></a>パラメーター

`strNetworkResource` [in]有効なポインター`BSTR`正しい WMI 名前空間のオブジェクトのパスを格納しています。 参照してください、[解説](#remarks)詳細についてはします。

`strUser` [in]有効なポインター`BSTR`ユーザー名を格納しています。 A`null`値が現在のセキュリティ コンテキストを示します。 ユーザーが現在のものとは異なるドメインから場合`strUser`円記号で区切られたドメインとユーザー名を含めることもできます。 `strUser` できますもあるでユーザー プリンシパル名 (UPN) を書式設定、として suhc  *userName@domainName*です。 参照してください、[解説](#remarks)詳細についてはします。

`strPassword` [in]有効なポインター`BSTR`パスワードを格納しています。 A`null`現在のセキュリティ コンテキストを示します。 空の文字列 ("")、有効な長さ 0 のパスワードを示します。

`strLocale` [in]有効なポインター`BSTR`を示す、適切なロケール情報を取得します。 Microsoft ロケールの識別子、文字列の形式は"MS\_*xxx*"ここで、 *xxx*ロケール識別子 (LCID) を示す 16 進数形式で文字列です。 無効なロケールが指定されているかどうか、メソッドが返されます`WBEM_E_INVALID_PARAMETER`代わりに、サーバーの既定のロケールが使用されている Windows 7 を除きます。 場合 ' null 1、現在のロケールを使用します。 
 
`lSecurityFlags` [in]渡すフラグ、`ConnectServerWmi`メソッドです。 このパラメーターにゼロ (0) の値の結果への呼び出しで`ConnectServerWmi`サーバーへの接続が確立された後にのみを返すことです。 これは、結果、応答していない無制限にサーバーが切断されたかどうか、アプリケーションです。 その他の有効な値は次のとおりです。

| 定数  | [値]  | 説明  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | 内部使用のために予約されています。 使用しないでください。 |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi` 2 分以内を返します。 |

`strAuthority` [in]ユーザーのドメイン名。 次の値のいずれかを取ります。

| [値] | 説明 |
|---------|---------|
| 空白 | NTLM 認証を使用すると、し、現在のユーザー NTLM ドメインを使用します。 場合`strUser`ドメイン (推奨される場所) を指定します。 ここで指定してはなりませんがします。 この関数を返します`WBEM_E_INVALID_PARAMETER`両方のパラメーターでドメインを指定する場合。 |
| Kerberos:*プリンシパル名* | Kerberos 認証を使用して、このパラメーターには、Kerberos プリンシパル名が含まれています。 |
| NTLMDOMAIN:*ドメイン名* | NT LAN Manager 認証を使用して、このパラメーターには、NTLM ドメイン名が含まれています。 |

`pCtx`   
[in]このパラメーターは、通常、`null`です。 ポインターはそれ以外の場合、 [IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx)オブジェクトが 1 つ以上の動的クラス プロバイダーで必要です。 

`ppNamespace`  
[out]ポインターを受け取る関数が戻るとき、 [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)オブジェクトを指定した名前空間にバインドします。 指すように設定されている`null`ときにエラーが発生します。

`impLevel`  
[in]権限借用レベルです。

`authLevel`  
[in]承認レベル。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx)メソッドです。

 既定の名前空間へのローカル アクセスの`strNetworkResource`単純なオブジェクトのパスを指定できます:"root \default"または"\\.\root\default"です。 リモート コンピューター上の既定の名前空間にアクセスするため、COM または Microsoft と互換性のあるネットワークを使用して、コンピューター名を含める:"\\myserver\root\default"です。 コンピューター名は、DNS 名または IP アドレス使用することができますも。 `ConnectServerWmi`関数は、IPv6 を実行するコンピューターとも接続できます IPv6 アドレスを使用します。

`strUser` 空の文字列にすることはできません。 ドメインが指定されている場合`strAuthority`、その必要がありますいないに含めることも`strUser`、または、関数を返します`WBEM_E_INVALID_PARAMETER`です。


## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
