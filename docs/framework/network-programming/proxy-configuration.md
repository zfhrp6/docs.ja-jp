---
title: "プロキシの構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 41f7cfe76acfb4b6bbf66207685935c190a51901
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="proxy-configuration"></a><span data-ttu-id="dab88-102">プロキシの構成</span><span class="sxs-lookup"><span data-stu-id="dab88-102">Proxy Configuration</span></span>
<span data-ttu-id="dab88-103">プロキシ サーバーは、リソースに対するクライアント要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="dab88-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="dab88-104">プロキシは、要求されたリソースをキャッシュから返したり、リソースが存在するサーバーに要求を転送したりできます。</span><span class="sxs-lookup"><span data-stu-id="dab88-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="dab88-105">プロキシは、リモート サーバーに送信された要求の数を減らすことで、ネットワークのパフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="dab88-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="dab88-106">プロキシを使用して、リソースへのアクセスを制限することもできます。</span><span class="sxs-lookup"><span data-stu-id="dab88-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="dab88-107">アダプティブ プロキシ</span><span class="sxs-lookup"><span data-stu-id="dab88-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="dab88-108">.NET Framework には、アダプティブと静的という 2 種類のプロキシがあります。</span><span class="sxs-lookup"><span data-stu-id="dab88-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="dab88-109">アダプティブ プロキシは、ネットワーク構成を変更するときに、その設定を調整します。</span><span class="sxs-lookup"><span data-stu-id="dab88-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="dab88-110">たとえば、ラップトップ ユーザーがダイヤルアップ ネットワーク接続を起動する場合、アダプティブ プロキシはこの変更を認識し、新しい構成スクリプトを検出して実行し、その設定を適切に調整します。</span><span class="sxs-lookup"><span data-stu-id="dab88-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="dab88-111">アダプティブ プロキシは、構成スクリプトによって構成されます (「[自動プロキシ検出](../../../docs/framework/network-programming/automatic-proxy-detection.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="dab88-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span></span> <span data-ttu-id="dab88-112">スクリプトは、一連のアプリケーション プロトコルと、各プロトコル用のプロキシを生成します。</span><span class="sxs-lookup"><span data-stu-id="dab88-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="dab88-113">いくつかのオプションは、構成スクリプトの実行方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="dab88-113">Several options control how the configuration script is run.</span></span> <span data-ttu-id="dab88-114">以下を指定できます。</span><span class="sxs-lookup"><span data-stu-id="dab88-114">You can specify the following:</span></span>  
  
-   <span data-ttu-id="dab88-115">構成スクリプトがダウンロードおよび実行される頻度。</span><span class="sxs-lookup"><span data-stu-id="dab88-115">How often the configuration script is downloaded and run.</span></span>  
  
-   <span data-ttu-id="dab88-116">スクリプトをダウンロードするまで待機する時間。</span><span class="sxs-lookup"><span data-stu-id="dab88-116">How long to wait for the script to download.</span></span>  
  
-   <span data-ttu-id="dab88-117">プロキシにアクセスするためにシステムで使用する資格情報。</span><span class="sxs-lookup"><span data-stu-id="dab88-117">Which credentials your system should use to access the proxy.</span></span>  
  
-   <span data-ttu-id="dab88-118">構成スクリプトをダウンロードするためにシステムで使用する資格情報。</span><span class="sxs-lookup"><span data-stu-id="dab88-118">Which credentials your system should use to download the configuration script.</span></span>  
  
 <span data-ttu-id="dab88-119">ネットワーク環境での変更により、システムで新しい一連のプロキシを使用することが必要となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="dab88-119">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="dab88-120">ネットワーク接続がダウンしたか、新しいネットワーク接続が開始された場合、システムは新しい環境で構成スクリプトの適切なソースを検出し、新しいスクリプトを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dab88-120">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="dab88-121">次の表に、アダプティブ プロキシの構成オプションを示します。</span><span class="sxs-lookup"><span data-stu-id="dab88-121">The following table shows configuration options for an adaptive proxy.</span></span>  
  
|<span data-ttu-id="dab88-122">属性、プロパティ、または構成ファイルの設定</span><span class="sxs-lookup"><span data-stu-id="dab88-122">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="dab88-123">説明</span><span class="sxs-lookup"><span data-stu-id="dab88-123">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|`scriptDownloadInterval`|<span data-ttu-id="dab88-124">スクリプトをダウンロードする間の経過時間 (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="dab88-124">Elapsed time in seconds between script downloads.</span></span>|  
|`scriptDownloadTimeout`|<span data-ttu-id="dab88-125">スクリプトをダウンロードするまでの待機時間 (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="dab88-125">Time to wait (in seconds) for the script to download.</span></span>|  
|<span data-ttu-id="dab88-126">`useDefaultCredentials` または <xref:System.Net.WebProxy.UseDefaultCredentials></span><span class="sxs-lookup"><span data-stu-id="dab88-126">`useDefaultCredentials` or <xref:System.Net.WebProxy.UseDefaultCredentials></span></span>|<span data-ttu-id="dab88-127">プロキシにアクセスするためにシステムで既定のネットワーク資格情報を使用するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="dab88-127">Controls whether the system uses the default network credentials to access a proxy.</span></span>|  
|`useDefaultCredentialForScriptDownload`|<span data-ttu-id="dab88-128">構成スクリプトをダウンロードするためにシステムで既定のネットワーク資格情報を使用するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="dab88-128">Controls whether the system uses the default network credentials to download the configuration script.</span></span>|  
|`usesystemdefaults`|<span data-ttu-id="dab88-129">静的プロキシ設定 (プロキシ アドレス、バイパス リスト、およびローカルでのバイパス) をユーザーの Internet Explorer プロキシ設定から読み取るかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="dab88-129">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="dab88-130">この値を"true"に設定した場合、Internet Explorer の静的プロキシ設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="dab88-130">If this value is set to "true", then the static proxy settings from Internet Explorer will be used.</span></span><br /><br /> <span data-ttu-id="dab88-131">この値が"false"であるか、または設定しない場合、静的プロキシ設定を構成で指定することができ、Internet Explorer のプロキシ設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="dab88-131">If this value is "false" or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="dab88-132">アダプティブ プロキシを有効にする場合も、この値を"false"に設定するか、または設定しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dab88-132">This value must also be set to "false" or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="dab88-133">一般的なアダプティブ プロキシの構成例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dab88-133">The following example shows a typical adaptive proxy configuration.</span></span>  
  
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
  
## <a name="static-proxies"></a><span data-ttu-id="dab88-134">静的プロキシ</span><span class="sxs-lookup"><span data-stu-id="dab88-134">Static Proxies</span></span>  
 <span data-ttu-id="dab88-135">静的プロキシは、通常、アプリケーションによって明示的に構成されるか、アプリケーションまたはシステムによって構成ファイルが呼び出されたときに構成されます。</span><span class="sxs-lookup"><span data-stu-id="dab88-135">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="dab88-136">静的プロキシは、企業ネットワークに接続されているデスクトップ コンピューターなど、トポロジがあまり変更されないネットワークで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="dab88-136">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="dab88-137">いくつかのオプションで静的プロキシの動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="dab88-137">Several options control how a static proxy operates.</span></span> <span data-ttu-id="dab88-138">以下を指定できます。</span><span class="sxs-lookup"><span data-stu-id="dab88-138">You can specify the following:</span></span>  
  
-   <span data-ttu-id="dab88-139">プロキシのアドレス。</span><span class="sxs-lookup"><span data-stu-id="dab88-139">The address of the proxy.</span></span>  
  
-   <span data-ttu-id="dab88-140">ローカル アドレスに対してプロキシをバイパスするかかどうか。</span><span class="sxs-lookup"><span data-stu-id="dab88-140">Whether the proxy should be bypassed for local addresses.</span></span>  
  
-   <span data-ttu-id="dab88-141">一連のアドレスに対してプロキシをバイパスするかかどうか。</span><span class="sxs-lookup"><span data-stu-id="dab88-141">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="dab88-142">次の表に、静的プロキシの構成オプションを示します。</span><span class="sxs-lookup"><span data-stu-id="dab88-142">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="dab88-143">属性、プロパティ、または構成ファイルの設定</span><span class="sxs-lookup"><span data-stu-id="dab88-143">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="dab88-144">説明</span><span class="sxs-lookup"><span data-stu-id="dab88-144">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="dab88-145">`proxyaddress` または <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="dab88-145">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="dab88-146">使用するプロキシのアドレス。</span><span class="sxs-lookup"><span data-stu-id="dab88-146">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="dab88-147">`bypassonlocal` または <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="dab88-147">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="dab88-148">ローカル アドレスに対してプロキシをバイパスするかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="dab88-148">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="dab88-149">`bypasslist` または <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="dab88-149">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="dab88-150">正規表現を使用して、プロキシをバイパスするアドレスのセットを記述します。</span><span class="sxs-lookup"><span data-stu-id="dab88-150">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefaults`|<span data-ttu-id="dab88-151">静的プロキシ設定 (プロキシ アドレス、バイパス リスト、およびローカルでのバイパス) をユーザーの Internet Explorer プロキシ設定から読み取るかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="dab88-151">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="dab88-152">この値を"true"に設定した場合、Internet Explorer の静的プロキシ設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="dab88-152">If this value is set to "true", then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="dab88-153">.NET Framework 2.0 でこの値を"true"に設定した場合、Internet Explorer のプロキシ設定は構成ファイル内の他のプロキシ設定でオーバーライドされません。</span><span class="sxs-lookup"><span data-stu-id="dab88-153">On .NET Framework 2.0 when this value is set to "true", the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="dab88-154">.NET Framework 1.1 では、構成ファイル内の他のプロキシ設定で Internet Explorer のプロキシ設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="dab88-154">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="dab88-155">この値が"false"であるか、または設定しない場合、静的プロキシ設定を構成で指定することができ、Internet Explorer のプロキシ設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="dab88-155">If this value is "false" or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="dab88-156">アダプティブ プロキシを有効にする場合も、この値を"false"に設定するか、または設定しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dab88-156">This value must also be set to "false" or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="dab88-157">一般的な静的プロキシの構成例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dab88-157">The following example shows a typical static proxy configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dab88-158">参照</span><span class="sxs-lookup"><span data-stu-id="dab88-158">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [<span data-ttu-id="dab88-159">自動プロキシ検出</span><span class="sxs-lookup"><span data-stu-id="dab88-159">Automatic Proxy Detection</span></span>](../../../docs/framework/network-programming/automatic-proxy-detection.md)
