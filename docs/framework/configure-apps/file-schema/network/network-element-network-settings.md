---
title: "&lt;ネットワーク&gt;要素 (ネットワーク設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d3e99a10403a735383ee5e1a78c1f85ac7fd8281
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetworkgt-element-network-settings"></a>&lt;ネットワーク&gt;要素 (ネットワーク設定)
外部の簡易メール転送プロトコル (SMTP) サーバーのネットワーク オプションを構成します。  
  
 \<configuration>  
\<system.net >  
\<mailSettings >  
\<smtp >  
\<ネットワーク >  
  
## <a name="syntax"></a>構文  
  
```xml  
<network  
  clientDomain="string"   
  defaultCredentials="true|false"  
  enableSsl="true|false"  
  host="string"   
  password="string"  
  port="integer"   
  targetName="string"  
  userName="string"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`clientDomain`|SMTP メール サーバーに接続する最初の SMTP プロトコルの要求で使用するクライアントのドメイン名を指定します。 既定値は、要求を送信するローカル コンピューターのローカル ホスト名です。|  
|`defaultCredentials`|既定のユーザー資格情報を使用するときに、SMTP メール サーバー SMTP トランザクションでのアクセスを使用するかどうかを指定します。 既定値は `false` です。|  
|`enableSsl`|SMTP メール サーバーへのアクセスに SSL が使用されるかどうかを指定します。 既定値は `false` です。|  
|`host`|SMTP トランザクションで使用する SMTP メール サーバーのホスト名を指定します。 この属性には、既定値はありません。|  
|`password`|SMTP メール サーバーへの認証に使用するパスワードを指定します。 この属性には、既定値はありません。|  
|`port`|SMTP メール サーバーへの接続に使用するポート番号を指定します。 既定値は 25 です。|  
|`targetName`|SMTP トランザクションで拡張保護を使用する場合は、認証に使用するサービス プロバイダー名 (SPN) を指定します。 この属性には、既定値はありません。|  
|`userName`|SMTP メール サーバーへの認証に使用するユーザー名を指定します。 この属性には、既定値はありません。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<smtp > 要素 (ネットワーク設定)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|簡易メール転送プロトコル (SMTP) 電子メールの送信オプションを構成します。|  
  
## <a name="remarks"></a>コメント  
 一部の SMTP サーバーでは、自分でを使用する前に、サーバーに対して認証することが必要です。 ホストの既定のネットワーク資格情報を使用して独自の認証を設定する場合、`defaultCredentials`属性を`true`です。 <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`defaultCredentials`該当する構成ファイルからの属性です。  
  
 基本認証 (ユーザー名とパスワード) 自分自身を認証する SMTP サーバーを使用することもできます。 このオプションを使用するには、有効なユーザー名と指定された SMTP サーバーのパスワードを指定する必要があります。  
  
> [!NOTE]
>  基本認証で送信、`userName`と`password`暗号化されていないサーバーへの値。 認証情報を表示でき、それらを使用して、サーバーに接続するネットワーク トラフィックを監視している人ことができます。 Kerberos または NT LAN Manager (NTLM) より安全な認証メカニズムを使用する必要があります。場合`defaultCredentials`は`true`サーバーは、これらのプロトコルをサポートしている場合、Kerberos または NTLM が使用されます。  
  
 基本認証と既定ネットワーク資格情報オプションは相互に排他的です。設定した場合`defaultCredentials`に`true`とユーザー名とパスワードを指定、既定のネットワーク資格情報が使用され、基本認証データは無視されます。  
  
 基本認証を指定する場合、`userName`も指定する必要があります、`password`認証にメール サーバーに自分でします。  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`userName`該当する構成ファイルからの属性です。 <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`password`該当する構成ファイルからの属性です。 A`password`は、通常セキュリティ上の理由の構成ファイルに入力していない属性です。  
  
 `clientDomain`属性は、SMTP サーバーに初期の SMTP プロトコルの要求で使用されるクライアントのドメイン名を変更します。 `clientDomain`属性は既定で使用されるローカル ホスト名ではなく、ローカル コンピューターの完全修飾ドメイン名に設定することができます。 これは、大きい標準に準拠して、SMTP プロトコルを提供します。 既定値は、要求を送信するローカル コンピューターのローカル ホスト名です。 <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`clientDomain`該当する構成ファイルからの属性です。  
  
 `targetName`属性は、拡張保護を使用する場合、認証に使用します。 形式で、既定値は"SMTPSVC/\<ホスト >"を\<ホスト > は、SMTP メール サーバーのホスト名です。 <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`targetName`該当する構成ファイルからの属性です。  
  
 `enableSsl`属性は、SMTP メール サーバーへのアクセスに SSL が使用されるかどうかを指定します。 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>クラスのみがサポート SMTP サービス拡張 SMTP のセキュリティで保護されたトランスポート層セキュリティ経由での RFC 3207 で定義されています。 このモードでは、SMTP セッションが暗号化されていないチャネルで開始し、STARTTLS コマンドがクライアントで SSL を使用してセキュリティで保護された通信に切り替えるには、サーバーに発行します。 詳細についてはインターネット技術標準化委員会 (IETF) によって発行された RFC 3207 を参照してください。  
  
 代替の接続方法は、任意のプロトコル コマンドを送信する前の SSL セッションの前払いの確立です。 この接続方法は、SMTPS とも呼ばれますが、既定ではポート 465 を使用します。 SSL を使用してこの代替の接続方法は現在サポートされていません。  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`enableSsl`該当する構成ファイルからの属性です。  
  
## <a name="example"></a>例  
 次の例では、既定のネットワーク資格情報を使用して電子メールを送信する適切な SMTP パラメーターを指定します。  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
        <network  
          clientDomain="www.contoso.com"  
          defaultCredentials="true"  
          enableSsl="false"  
          host="mail.contoso.com"  
          port="25"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
