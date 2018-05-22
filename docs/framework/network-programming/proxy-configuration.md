---
title: プロキシの構成
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 41e1dcee90531de605b6bddc1eedc1c44235d8eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="proxy-configuration"></a><span data-ttu-id="46311-102">プロキシの構成</span><span class="sxs-lookup"><span data-stu-id="46311-102">Proxy Configuration</span></span>
<span data-ttu-id="46311-103">プロキシ サーバーは、リソースに対するクライアント要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="46311-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="46311-104">プロキシは、要求されたリソースをキャッシュから返したり、リソースが存在するサーバーに要求を転送したりできます。</span><span class="sxs-lookup"><span data-stu-id="46311-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="46311-105">プロキシは、リモート サーバーに送信された要求の数を減らすことで、ネットワークのパフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="46311-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="46311-106">プロキシを使用して、リソースへのアクセスを制限することもできます。</span><span class="sxs-lookup"><span data-stu-id="46311-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="46311-107">アダプティブ プロキシ</span><span class="sxs-lookup"><span data-stu-id="46311-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="46311-108">.NET Framework には、アダプティブと静的という 2 種類のプロキシがあります。</span><span class="sxs-lookup"><span data-stu-id="46311-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="46311-109">アダプティブ プロキシは、ネットワーク構成を変更するときに、その設定を調整します。</span><span class="sxs-lookup"><span data-stu-id="46311-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="46311-110">たとえば、ラップトップ ユーザーがダイヤルアップ ネットワーク接続を起動する場合、アダプティブ プロキシはこの変更を認識し、新しい構成スクリプトを検出して実行し、その設定を適切に調整します。</span><span class="sxs-lookup"><span data-stu-id="46311-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="46311-111">アダプティブ プロキシは、構成スクリプトによって構成されます (「[自動プロキシ検出](../../../docs/framework/network-programming/automatic-proxy-detection.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="46311-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span></span> <span data-ttu-id="46311-112">スクリプトは、一連のアプリケーション プロトコルと、各プロトコル用のプロキシを生成します。</span><span class="sxs-lookup"><span data-stu-id="46311-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="46311-113">いくつかのオプションは、構成スクリプトの実行方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="46311-113">Several options control how the configuration script is run.</span></span> <span data-ttu-id="46311-114">以下を指定できます。</span><span class="sxs-lookup"><span data-stu-id="46311-114">You can specify the following:</span></span>  
  
-   <span data-ttu-id="46311-115">構成スクリプトがダウンロードおよび実行される頻度。</span><span class="sxs-lookup"><span data-stu-id="46311-115">How often the configuration script is downloaded and run.</span></span>  
  
-   <span data-ttu-id="46311-116">スクリプトをダウンロードするまで待機する時間。</span><span class="sxs-lookup"><span data-stu-id="46311-116">How long to wait for the script to download.</span></span>  
  
-   <span data-ttu-id="46311-117">プロキシにアクセスするためにシステムで使用する資格情報。</span><span class="sxs-lookup"><span data-stu-id="46311-117">Which credentials your system should use to access the proxy.</span></span>  
  
-   <span data-ttu-id="46311-118">構成スクリプトをダウンロードするためにシステムで使用する資格情報。</span><span class="sxs-lookup"><span data-stu-id="46311-118">Which credentials your system should use to download the configuration script.</span></span>  
  
 <span data-ttu-id="46311-119">ネットワーク環境での変更により、システムで新しい一連のプロキシを使用することが必要となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="46311-119">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="46311-120">ネットワーク接続がダウンしたか、新しいネットワーク接続が開始された場合、システムは新しい環境で構成スクリプトの適切なソースを検出し、新しいスクリプトを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46311-120">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="46311-121">次の表に、アダプティブ プロキシの構成オプションを示します。</span><span class="sxs-lookup"><span data-stu-id="46311-121">The following table shows configuration options for an adaptive proxy.</span></span>  
  
|<span data-ttu-id="46311-122">属性、プロパティ、または構成ファイルの設定</span><span class="sxs-lookup"><span data-stu-id="46311-122">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="46311-123">説明</span><span class="sxs-lookup"><span data-stu-id="46311-123">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|`scriptDownloadInterval`|<span data-ttu-id="46311-124">スクリプトをダウンロードする間の経過時間 (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="46311-124">Elapsed time in seconds between script downloads.</span></span>|  
|`scriptDownloadTimeout`|<span data-ttu-id="46311-125">スクリプトをダウンロードするまでの待機時間 (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="46311-125">Time to wait (in seconds) for the script to download.</span></span>|  
|<span data-ttu-id="46311-126">`useDefaultCredentials` または <xref:System.Net.WebProxy.UseDefaultCredentials></span><span class="sxs-lookup"><span data-stu-id="46311-126">`useDefaultCredentials` or <xref:System.Net.WebProxy.UseDefaultCredentials></span></span>|<span data-ttu-id="46311-127">プロキシにアクセスするためにシステムで既定のネットワーク資格情報を使用するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="46311-127">Controls whether the system uses the default network credentials to access a proxy.</span></span>|  
|`useDefaultCredentialForScriptDownload`|<span data-ttu-id="46311-128">構成スクリプトをダウンロードするためにシステムで既定のネットワーク資格情報を使用するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="46311-128">Controls whether the system uses the default network credentials to download the configuration script.</span></span>|  
|`usesystemdefaults`|<span data-ttu-id="46311-129">静的プロキシ設定 (プロキシ アドレス、バイパス リスト、およびローカルでのバイパス) をユーザーの Internet Explorer プロキシ設定から読み取るかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="46311-129">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="46311-130">この値を"true"に設定した場合、Internet Explorer の静的プロキシ設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="46311-130">If this value is set to "true", then the static proxy settings from Internet Explorer will be used.</span></span><br /><br /> <span data-ttu-id="46311-131">この値が"false"であるか、または設定しない場合、静的プロキシ設定を構成で指定することができ、Internet Explorer のプロキシ設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="46311-131">If this value is "false" or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="46311-132">アダプティブ プロキシを有効にする場合も、この値を"false"に設定するか、または設定しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="46311-132">This value must also be set to "false" or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="46311-133">一般的なアダプティブ プロキシの構成例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="46311-133">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy  scriptDownloadInterval="600"  
              scriptDownloadTimeout="30"  
              useDefaultCredentials="true"  
              usesystemdefaults="true"  
      />  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="46311-134">静的プロキシ</span><span class="sxs-lookup"><span data-stu-id="46311-134">Static Proxies</span></span>  
 <span data-ttu-id="46311-135">静的プロキシは、通常、アプリケーションによって明示的に構成されるか、アプリケーションまたはシステムによって構成ファイルが呼び出されたときに構成されます。</span><span class="sxs-lookup"><span data-stu-id="46311-135">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="46311-136">静的プロキシは、企業ネットワークに接続されているデスクトップ コンピューターなど、トポロジがあまり変更されないネットワークで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="46311-136">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="46311-137">いくつかのオプションで静的プロキシの動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="46311-137">Several options control how a static proxy operates.</span></span> <span data-ttu-id="46311-138">以下を指定できます。</span><span class="sxs-lookup"><span data-stu-id="46311-138">You can specify the following:</span></span>  
  
-   <span data-ttu-id="46311-139">プロキシのアドレス。</span><span class="sxs-lookup"><span data-stu-id="46311-139">The address of the proxy.</span></span>  
  
-   <span data-ttu-id="46311-140">ローカル アドレスに対してプロキシをバイパスするかかどうか。</span><span class="sxs-lookup"><span data-stu-id="46311-140">Whether the proxy should be bypassed for local addresses.</span></span>  
  
-   <span data-ttu-id="46311-141">一連のアドレスに対してプロキシをバイパスするかかどうか。</span><span class="sxs-lookup"><span data-stu-id="46311-141">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="46311-142">次の表に、静的プロキシの構成オプションを示します。</span><span class="sxs-lookup"><span data-stu-id="46311-142">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="46311-143">属性、プロパティ、または構成ファイルの設定</span><span class="sxs-lookup"><span data-stu-id="46311-143">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="46311-144">説明</span><span class="sxs-lookup"><span data-stu-id="46311-144">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="46311-145">`proxyaddress` または <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="46311-145">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="46311-146">使用するプロキシのアドレス。</span><span class="sxs-lookup"><span data-stu-id="46311-146">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="46311-147">`bypassonlocal` または <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="46311-147">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="46311-148">ローカル アドレスに対してプロキシをバイパスするかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="46311-148">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="46311-149">`bypasslist` または <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="46311-149">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="46311-150">正規表現を使用して、プロキシをバイパスするアドレスのセットを記述します。</span><span class="sxs-lookup"><span data-stu-id="46311-150">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefaults`|<span data-ttu-id="46311-151">静的プロキシ設定 (プロキシ アドレス、バイパス リスト、およびローカルでのバイパス) をユーザーの Internet Explorer プロキシ設定から読み取るかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="46311-151">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="46311-152">この値を"true"に設定した場合、Internet Explorer の静的プロキシ設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="46311-152">If this value is set to "true", then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="46311-153">.NET Framework 2.0 でこの値を"true"に設定した場合、Internet Explorer のプロキシ設定は構成ファイル内の他のプロキシ設定でオーバーライドされません。</span><span class="sxs-lookup"><span data-stu-id="46311-153">On .NET Framework 2.0 when this value is set to "true", the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="46311-154">.NET Framework 1.1 では、構成ファイル内の他のプロキシ設定で Internet Explorer のプロキシ設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="46311-154">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="46311-155">この値が"false"であるか、または設定しない場合、静的プロキシ設定を構成で指定することができ、Internet Explorer のプロキシ設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="46311-155">If this value is "false" or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="46311-156">アダプティブ プロキシを有効にする場合も、この値を"false"に設定するか、または設定しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="46311-156">This value must also be set to "false" or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="46311-157">一般的な静的プロキシの構成例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="46311-157">The following example shows a typical static proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="true"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="46311-158">参照</span><span class="sxs-lookup"><span data-stu-id="46311-158">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [<span data-ttu-id="46311-159">自動プロキシ検出</span><span class="sxs-lookup"><span data-stu-id="46311-159">Automatic Proxy Detection</span></span>](../../../docs/framework/network-programming/automatic-proxy-detection.md)
