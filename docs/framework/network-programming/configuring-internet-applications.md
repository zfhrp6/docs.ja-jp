---
title: 構成 (インターネット アプリケーションを)
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, default proxy
- sending data, default proxy
- receiving data, default proxy
- downloading Internet resources, configuring Internet applications
- protocol-specific modules
- custom authentication modules
- receiving data, configuring Internet applications
- configuration settings [.NET Framework], Internet applications
- requesting data from Internet, configuring Internet applications
- requesting data from Internet, default proxy
- response to Internet request, default proxy
- Internet, configuring Internet applications
- response to Internet request, configuring Internet applications
- default proxy
- network resources, default proxy
- sending data, configuring Internet applications
- network resources, configuring Internet applications
- Internet, default proxy
ms.assetid: bb707c72-eed2-4a82-8800-c9e68df2fd4f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7c4755e13202f60df5704f6faefb3b279a30ce58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395061"
---
# <a name="configuring-internet-applications"></a><span data-ttu-id="c37f8-102">構成 (インターネット アプリケーションを)</span><span class="sxs-lookup"><span data-stu-id="c37f8-102">Configuring Internet Applications</span></span>
<span data-ttu-id="c37f8-103">[\<system.Net> 要素 (ネットワーク設定)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) 構成要素には、アプリケーションのネットワーク構成情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c37f8-103">The [\<system.Net> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="c37f8-104">[\<system.Net> 要素 (ネットワーク設定)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) 要素を使用すると、プロキシ サーバーを設定し、接続管理パラメーターを設定し、カスタム認証および要求モジュールをアプリケーションに組み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="c37f8-104">Using the [\<system.Net> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="c37f8-105">[\<defaultProxy> 要素 (ネットワーク設定)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) 要素は、`GlobalProxySelection` クラスによって返されるプロキシ サーバーを定義します。</span><span class="sxs-lookup"><span data-stu-id="c37f8-105">The [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="c37f8-106">独自の <xref:System.Net.HttpWebRequest.Proxy%2A> プロパティが特定の値に設定されていない <xref:System.Net.HttpWebRequest> はすべて、既定のプロキシを使用します。</span><span class="sxs-lookup"><span data-stu-id="c37f8-106">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="c37f8-107">プロキシ アドレスを設定するだけでなく、プロキシを使用しないサーバー アドレスの一覧を作成し、ローカル アドレスにプロキシを使用しないように指定できます。</span><span class="sxs-lookup"><span data-stu-id="c37f8-107">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="c37f8-108">Microsoft Internet Explorer の設定は構成の設定と組み合わせて使用され、構成の設定が優先されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c37f8-108">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="c37f8-109">次の例では、既定のプロキシ サーバー アドレスを http://proxyserver に設定し、ローカル アドレスにプロキシを使用しないようにし、contoso.com ドメインにあるサーバーへのすべての要求でプロキシをバイパスするように指定しています。</span><span class="sxs-lookup"><span data-stu-id="c37f8-109">The following example sets the default proxy server address to http://proxyserver, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <defaultProxy>  
            <proxy  
                usesystemdefault = "false"  
                proxyaddress = "http://proxyserver:80"  
                bypassonlocal = "true"  
            />  
            <bypasslist>  
                <add address="http://[a-z]+\.contoso\.com/" />  
            </bypasslist>  
        </defaultProxy>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="c37f8-110">特定のサーバーまたは他のすべてのサーバーに対して行うことができる持続接続の数を構成する場合は、[\<connectionManagement> 要素 (ネットワーク設定)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="c37f8-110">Use the [\<connectionManagement> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="c37f8-111">次の例では、サーバー www.contoso.com への 2 つの持続接続、IP アドレス 192.168.1.2 を持つサーバーへの 4 つの持続接続、および他のすべてのサーバーへの 1 つの持続接続を使用するようにアプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="c37f8-111">The following example configures the application to use two persistent connections to the server www.contoso.com, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <connectionManagement>  
            <add address="http://www.contoso.com" maxconnection="2" />  
            <add address="192.168.1.2" maxconnection="4" />  
            <add address="*" maxconnection="1" />  
        </connectionManagement>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="c37f8-112">カスタム認証モジュールは、[\<authenticationModules> 要素 (ネットワーク設定)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) 要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="c37f8-112">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="c37f8-113">カスタム認証モジュールは <xref:System.Net.IAuthenticationModule> インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c37f8-113">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="c37f8-114">次の例では、カスタム認証モジュールを構成します。</span><span class="sxs-lookup"><span data-stu-id="c37f8-114">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="c37f8-115">[\<webRequestModules> 要素 (ネットワーク設定)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) 要素を使用し、カスタム プロトコル固有のモジュールを使用してインターネット リソースから情報を要求するようにアプリケーションを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="c37f8-115">You can use the [\<webRequestModules> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="c37f8-116">指定されたモジュールは <xref:System.Net.IWebRequestCreate> インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c37f8-116">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="c37f8-117">既定の HTTP、HTTPS、およびファイル要求モジュールは、次の例のように、構成ファイルでカスタム モジュールを指定してオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="c37f8-117">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <webRequestModules>  
            <add  
                prefix="HTTP"  
                type = "MyHttpRequest.dll, MyHttpRequestCreator"  
            />  
        </webRequestModules>  
    </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c37f8-118">参照</span><span class="sxs-lookup"><span data-stu-id="c37f8-118">See Also</span></span>  
 [<span data-ttu-id="c37f8-119">.NET Framework のネットワーク プログラミング</span><span class="sxs-lookup"><span data-stu-id="c37f8-119">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="c37f8-120">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="c37f8-120">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="c37f8-121">\<system.Net> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="c37f8-121">\<system.Net> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
