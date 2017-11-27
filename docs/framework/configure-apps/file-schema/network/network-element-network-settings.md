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
ms.openlocfilehash: 679351fd2d6f0727d40bd57c9ef2016738462eb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltnetworkgt-element-network-settings"></a><span data-ttu-id="2c21c-102">&lt;ネットワーク&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="2c21c-102">&lt;network&gt; Element (Network Settings)</span></span>
<span data-ttu-id="2c21c-103">外部の簡易メール転送プロトコル (SMTP) サーバーのネットワーク オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="2c21c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2c21c-104">\<configuration></span></span>  
<span data-ttu-id="2c21c-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="2c21c-105">\<system.net></span></span>  
<span data-ttu-id="2c21c-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="2c21c-106">\<mailSettings></span></span>  
<span data-ttu-id="2c21c-107">\<smtp ></span><span class="sxs-lookup"><span data-stu-id="2c21c-107">\<smtp></span></span>  
<span data-ttu-id="2c21c-108">\<ネットワーク ></span><span class="sxs-lookup"><span data-stu-id="2c21c-108">\<network></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c21c-109">構文</span><span class="sxs-lookup"><span data-stu-id="2c21c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c21c-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2c21c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2c21c-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c21c-112">属性</span><span class="sxs-lookup"><span data-stu-id="2c21c-112">Attributes</span></span>  
  
|<span data-ttu-id="2c21c-113">属性</span><span class="sxs-lookup"><span data-stu-id="2c21c-113">Attribute</span></span>|<span data-ttu-id="2c21c-114">説明</span><span class="sxs-lookup"><span data-stu-id="2c21c-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="2c21c-115">SMTP メール サーバーに接続する最初の SMTP プロトコルの要求で使用するクライアントのドメイン名を指定します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="2c21c-116">既定値は、要求を送信するローカル コンピューターのローカル ホスト名です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="2c21c-117">既定のユーザー資格情報を使用するときに、SMTP メール サーバー SMTP トランザクションでのアクセスを使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="2c21c-118">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="2c21c-119">SMTP メール サーバーへのアクセスに SSL が使用されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="2c21c-120">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="2c21c-121">SMTP トランザクションで使用する SMTP メール サーバーのホスト名を指定します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="2c21c-122">この属性には、既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="2c21c-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="2c21c-123">SMTP メール サーバーへの認証に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="2c21c-124">この属性には、既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="2c21c-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="2c21c-125">SMTP メール サーバーへの接続に使用するポート番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="2c21c-126">既定値は 25 です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="2c21c-127">SMTP トランザクションで拡張保護を使用する場合は、認証に使用するサービス プロバイダー名 (SPN) を指定します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="2c21c-128">この属性には、既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="2c21c-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="2c21c-129">SMTP メール サーバーへの認証に使用するユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="2c21c-130">この属性には、既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="2c21c-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c21c-131">子要素</span><span class="sxs-lookup"><span data-stu-id="2c21c-131">Child Elements</span></span>  
 <span data-ttu-id="2c21c-132">なし。</span><span class="sxs-lookup"><span data-stu-id="2c21c-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c21c-133">親要素</span><span class="sxs-lookup"><span data-stu-id="2c21c-133">Parent Elements</span></span>  
  
|<span data-ttu-id="2c21c-134">要素</span><span class="sxs-lookup"><span data-stu-id="2c21c-134">Element</span></span>|<span data-ttu-id="2c21c-135">説明</span><span class="sxs-lookup"><span data-stu-id="2c21c-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c21c-136">\<smtp > 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="2c21c-136">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="2c21c-137">簡易メール転送プロトコル (SMTP) 電子メールの送信オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c21c-138">コメント</span><span class="sxs-lookup"><span data-stu-id="2c21c-138">Remarks</span></span>  
 <span data-ttu-id="2c21c-139">一部の SMTP サーバーでは、自分でを使用する前に、サーバーに対して認証することが必要です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="2c21c-140">ホストの既定のネットワーク資格情報を使用して独自の認証を設定する場合、`defaultCredentials`属性を`true`です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="2c21c-141"><xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`defaultCredentials`該当する構成ファイルからの属性です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="2c21c-142">基本認証 (ユーザー名とパスワード) 自分自身を認証する SMTP サーバーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="2c21c-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="2c21c-143">このオプションを使用するには、有効なユーザー名と指定された SMTP サーバーのパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c21c-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c21c-144">基本認証で送信、`userName`と`password`暗号化されていないサーバーへの値。</span><span class="sxs-lookup"><span data-stu-id="2c21c-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="2c21c-145">認証情報を表示でき、それらを使用して、サーバーに接続するネットワーク トラフィックを監視している人ことができます。</span><span class="sxs-lookup"><span data-stu-id="2c21c-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="2c21c-146">Kerberos または NT LAN Manager (NTLM) より安全な認証メカニズムを使用する必要があります。場合`defaultCredentials`は`true`サーバーは、これらのプロトコルをサポートしている場合、Kerberos または NTLM が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2c21c-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="2c21c-147">基本認証と既定ネットワーク資格情報オプションは相互に排他的です。設定した場合`defaultCredentials`に`true`とユーザー名とパスワードを指定、既定のネットワーク資格情報が使用され、基本認証データは無視されます。</span><span class="sxs-lookup"><span data-stu-id="2c21c-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="2c21c-148">基本認証を指定する場合、`userName`も指定する必要があります、`password`認証にメール サーバーに自分でします。</span><span class="sxs-lookup"><span data-stu-id="2c21c-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="2c21c-149"><xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`userName`該当する構成ファイルからの属性です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="2c21c-150"><xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`password`該当する構成ファイルからの属性です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="2c21c-151">A`password`は、通常セキュリティ上の理由の構成ファイルに入力していない属性です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="2c21c-152">`clientDomain`属性は、SMTP サーバーに初期の SMTP プロトコルの要求で使用されるクライアントのドメイン名を変更します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="2c21c-153">`clientDomain`属性は既定で使用されるローカル ホスト名ではなく、ローカル コンピューターの完全修飾ドメイン名に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="2c21c-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="2c21c-154">これは、大きい標準に準拠して、SMTP プロトコルを提供します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="2c21c-155">既定値は、要求を送信するローカル コンピューターのローカル ホスト名です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="2c21c-156"><xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`clientDomain`該当する構成ファイルからの属性です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="2c21c-157">`targetName`属性は、拡張保護を使用する場合、認証に使用します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="2c21c-158">形式で、既定値は"SMTPSVC/\<ホスト >"を\<ホスト > は、SMTP メール サーバーのホスト名です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="2c21c-159"><xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`targetName`該当する構成ファイルからの属性です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="2c21c-160">`enableSsl`属性は、SMTP メール サーバーへのアクセスに SSL が使用されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="2c21c-161"><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>クラスのみがサポート SMTP サービス拡張 SMTP のセキュリティで保護されたトランスポート層セキュリティ経由での RFC 3207 で定義されています。</span><span class="sxs-lookup"><span data-stu-id="2c21c-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="2c21c-162">このモードでは、SMTP セッションが暗号化されていないチャネルで開始し、STARTTLS コマンドがクライアントで SSL を使用してセキュリティで保護された通信に切り替えるには、サーバーに発行します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="2c21c-163">詳細についてはインターネット技術標準化委員会 (IETF) によって発行された RFC 3207 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c21c-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="2c21c-164">代替の接続方法は、任意のプロトコル コマンドを送信する前の SSL セッションの前払いの確立です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="2c21c-165">この接続方法は、SMTPS とも呼ばれますが、既定ではポート 465 を使用します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="2c21c-166">SSL を使用してこの代替の接続方法は現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2c21c-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="2c21c-167"><xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`enableSsl`該当する構成ファイルからの属性です。</span><span class="sxs-lookup"><span data-stu-id="2c21c-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c21c-168">例</span><span class="sxs-lookup"><span data-stu-id="2c21c-168">Example</span></span>  
 <span data-ttu-id="2c21c-169">次の例では、既定のネットワーク資格情報を使用して電子メールを送信する適切な SMTP パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="2c21c-169">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2c21c-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c21c-170">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 [<span data-ttu-id="2c21c-171">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="2c21c-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
