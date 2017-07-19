---
title: "&lt;network&gt; 要素 (ネットワーク設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#network"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<network> 要素"
  - "network 要素"
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;network&gt; 要素 (ネットワーク設定)
外部 SMTP \(Simple Mail Transport Protocol\) サーバー用のネットワーク オプションを設定します。  
  
## 構文  
  
```  
  
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
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`clientDomain`|SMTP メール サーバーに接続するために最初の SMTP プロトコル要求で使用するクライアント ドメイン名を指定します。  既定値は、要求を送信するローカル コンピューターの localhost 名です。|  
|`defaultCredentials`|SMTP トランザクションで SMTP メール サーバーにアクセスするために既定のユーザー資格情報を使用するかどうかを指定します。  既定値は `false` です。|  
|`enableSsl`|SMTP メール サーバーへのアクセスに SSL を使用するかどうかを指定します。  既定値は `false` です。|  
|`host`|SMTP トランザクションに使用する SMTP メール サーバーのホスト名を指定します。  この属性には既定値はありません。|  
|`password`|SMTP メール サーバーへの認証に使用するパスワードを指定します。  この属性には既定値はありません。|  
|`port`|SMTP メール サーバーへの接続に使用するポート番号を指定します。  既定値は 25 です。|  
|`targetName`|SMTP トランザクションで拡張保護を使用している場合に認証に使用するサービス プロバイダー名 \(SPN: Service Provider Name\) を指定します。  この属性には既定値はありません。|  
|`userName`|SMTP メール サーバーへの認証に使用するユーザー名を指定します。  この属性には既定値はありません。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<smtp\> 要素 \(ネットワーク設定\)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|SMTP \(Simple Mail Transport Protocol\) の電子メール送信オプションを設定します。|  
  
## 解説  
 一部の SMTP サーバーでは、使用する前にユーザー認証を受けることが要求されます。  ホストの既定のネットワーク資格情報を使用してユーザー認証を受けるには、`defaultCredentials` 属性を `true` に設定します。  <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=fullName> プロパティを使用して、適用可能な構成ファイルから `defaultCredentials` 属性の現在の値を取得できます。  
  
 基本認証 \(ユーザー名およびパスワード\) を使用して SMTP サーバーのユーザー認証を受けることもできます。  このオプションを使用するには、指定した SMTP サーバーで有効なユーザー名およびパスワードを指定する必要があります。  
  
> [!NOTE]
>  基本認証では、`userName` の値および `password` の値が暗号化されることなくサーバーに送信されます。  ネットワーク トラフィックを監視している者があれば、この資格情報を参照でき、これを使用してサーバーに接続できます。  Kerberos、NT LAN Manager \(NTLM.\) など、より安全な認証方式を使用することを検討してください。`defaultCredentials` が `true` の場合、サーバーでサポートされている場合は、Kerberos または NTLM が使用されます。  
  
 基本認証オプションと既定のネットワーク資格情報オプションは相互に排他的です。`defaultCredentials` を `true` に設定し、ユーザー名およびパスワードを指定すると、既定のネットワーク資格情報が使用され、基本認証データは無視されます。  
  
 基本認証で `userName` を指定する場合は、メール サーバーの認証を受けるために `password` も指定する必要があります。  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=fullName> プロパティを使用して、適用可能な構成ファイルから `userName` 属性の現在の値を取得できます。  <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=fullName> プロパティを使用して、適用可能な構成ファイルから `password` 属性の現在の値を取得できます。  セキュリティ上の理由から、通常、`password` 属性は構成ファイルに入力されません。  
  
 `clientDomain` 属性は、SMTP サーバーへの最初の SMTP プロトコル要求で使用されるクライアント ドメイン名を変更します。  `clientDomain` 属性は、既定で使用される localhost 名ではなく、ローカル コンピューターの完全修飾ドメイン名に設定できます。  これにより、SMTP プロトコル標準への準拠が向上します。  既定値は、要求を送信するローカル コンピューターの localhost 名です。  <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=fullName> プロパティを使用して、適用可能な構成ファイルから `clientDomain` 属性の現在の値を取得できます。  
  
 `targetName` 属性は、拡張保護を使用している場合に認証に使用します。  既定値はフォーム「SMTPSVC\/host\<\>」ホストが \<SMTP メール サーバー\> のホスト名である場所です。  <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=fullName> プロパティを使用して、適用可能な構成ファイルから `targetName` 属性の現在の値を取得できます。  
  
 `enableSsl`  属性は、SMTP メール サーバーへのアクセスに SSL を使用するかどうかを指定します。  <xref:System.Net.Mail.SmtpClient?displayProperty=fullName> クラスでサポートされているのは、RFC 3207 で定義されている SMTP Service Extension for Secure SMTP over Transport Layer Security のみです。  このモードでは、SMTP セッションが暗号化されていないチャネルで開始されます。その後、SSL によるセキュリティで保護された通信に切り替えるために、クライアントからサーバーに対して STARTTLS コマンドが実行されます。  詳細については、インターネット技術標準化委員会 \(IETF: Internet Engineering Task Force\) から発行された RFC 3207 を参照してください。  
  
 事前に SSL セッションが確立され、その後にプロトコル コマンドが送信されるという、代替接続方法もあります。  この接続方法は SMTPS とも呼ばれ、既定ではポート 465 を使用します。  SSL を使用するこの代替接続方法は、現在はサポートされていません。  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=fullName> プロパティを使用して、適用可能な構成ファイルから `enableSsl` 属性の現在の値を取得できます。  
  
## 使用例  
 既定のネットワーク資格情報を使用して電子メールを送信するために、適切な SMTP パラメーターを指定するコード例を次に示します。  
  
```  
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
  
## 参照  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=fullName>   
 <xref:System.Net.Configuration.SmtpSection?displayProperty=fullName>   
 <xref:System.Net.Mail.SmtpClient?displayProperty=fullName>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)