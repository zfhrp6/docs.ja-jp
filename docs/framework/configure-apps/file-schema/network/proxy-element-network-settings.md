---
title: '&lt;プロキシ&gt;要素 (ネットワーク設定)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b5ae716994f9b8222a633699367c94480179c97b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltproxygt-element-network-settings"></a><span data-ttu-id="419eb-102">&lt;プロキシ&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="419eb-102">&lt;proxy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="419eb-103">プロキシ サーバーを定義します。</span><span class="sxs-lookup"><span data-stu-id="419eb-103">Defines a proxy server.</span></span>  
  
 <span data-ttu-id="419eb-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="419eb-104">\<configuration></span></span>  
<span data-ttu-id="419eb-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="419eb-105">\<system.net></span></span>  
<span data-ttu-id="419eb-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="419eb-106">\<defaultProxy></span></span>  
<span data-ttu-id="419eb-107">\<プロキシ ></span><span class="sxs-lookup"><span data-stu-id="419eb-107">\<proxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="419eb-108">構文</span><span class="sxs-lookup"><span data-stu-id="419eb-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="419eb-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="419eb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="419eb-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="419eb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="419eb-111">属性</span><span class="sxs-lookup"><span data-stu-id="419eb-111">Attributes</span></span>  
  
|<span data-ttu-id="419eb-112">**属性**</span><span class="sxs-lookup"><span data-stu-id="419eb-112">**Attribute**</span></span>|<span data-ttu-id="419eb-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="419eb-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="419eb-114">プロキシが自動的に検出されたかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="419eb-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="419eb-115">既定値は `unspecified` です。</span><span class="sxs-lookup"><span data-stu-id="419eb-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="419eb-116">ローカル リソースに対してプロキシをバイパスするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="419eb-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="419eb-117">ローカル リソースには、ローカル サーバーが含まれます (http://localhost、 http://loopback、またはhttp://127.0.0.1)およびピリオドを付けない URI (http://webserver)です。</span><span class="sxs-lookup"><span data-stu-id="419eb-117">Local resources include the local server (http://localhost, http://loopback, or http://127.0.0.1) and a URI without a period (http://webserver).</span></span> <span data-ttu-id="419eb-118">既定値は `unspecified` です。</span><span class="sxs-lookup"><span data-stu-id="419eb-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="419eb-119">プロキシに使用する URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="419eb-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="419eb-120">構成スクリプトの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="419eb-120">Specifies the location of the configuration script.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="419eb-121">Internet Explorer のプロキシ設定を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="419eb-121">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="419eb-122">場合設定`true`、後続する属性には、Internet Explorer のプロキシ設定がよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="419eb-122">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="419eb-123">既定値は `unspecified` です。</span><span class="sxs-lookup"><span data-stu-id="419eb-123">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="419eb-124">子要素</span><span class="sxs-lookup"><span data-stu-id="419eb-124">Child Elements</span></span>  
 <span data-ttu-id="419eb-125">なし。</span><span class="sxs-lookup"><span data-stu-id="419eb-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="419eb-126">親要素</span><span class="sxs-lookup"><span data-stu-id="419eb-126">Parent Elements</span></span>  
  
|<span data-ttu-id="419eb-127">**要素**</span><span class="sxs-lookup"><span data-stu-id="419eb-127">**Element**</span></span>|<span data-ttu-id="419eb-128">**説明**</span><span class="sxs-lookup"><span data-stu-id="419eb-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="419eb-129">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="419eb-129">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="419eb-130">ハイパーテキスト転送プロトコル (HTTP: Hypertext Transfer Protocol) プロキシ サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="419eb-130">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="419eb-131">テキスト値</span><span class="sxs-lookup"><span data-stu-id="419eb-131">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="419eb-132">コメント</span><span class="sxs-lookup"><span data-stu-id="419eb-132">Remarks</span></span>  
 <span data-ttu-id="419eb-133">`proxy`要素は、アプリケーションのプロキシ サーバーを定義します。</span><span class="sxs-lookup"><span data-stu-id="419eb-133">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="419eb-134">この要素が見つからない場合、構成ファイルから、し、.NET Framework は Internet Explorer でプロキシ設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="419eb-134">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="419eb-135">値、`proxyaddress`属性が整形式 Uniform Resource Indicator (URI) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="419eb-135">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="419eb-136">`scriptLocation`属性はプロキシ構成スクリプトの自動検出を参照します。</span><span class="sxs-lookup"><span data-stu-id="419eb-136">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="419eb-137"><xref:System.Net.WebProxy>クラスは、構成スクリプト (通常の名前付き Wpad.dat) と検索を試みます、**自動構成スクリプトを使用して**Internet Explorer のオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="419eb-137">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span>  
  
 <span data-ttu-id="419eb-138">使用して、 `usesystemdefault` version 2.0 に移行する .NET Framework version 1.1 のアプリケーション用の属性です。</span><span class="sxs-lookup"><span data-stu-id="419eb-138">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="419eb-139">場合、例外がスローされます、`proxyaddress`属性は無効な既定のプロキシを指定します。</span><span class="sxs-lookup"><span data-stu-id="419eb-139">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="419eb-140">例外の <xref:System.Exception.InnerException%2A> プロパティに、このエラーの根本的な原因に関する詳細情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="419eb-140">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="419eb-141">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="419eb-141">Configuration Files</span></span>  
 <span data-ttu-id="419eb-142">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="419eb-142">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="419eb-143">例</span><span class="sxs-lookup"><span data-stu-id="419eb-143">Example</span></span>  
 <span data-ttu-id="419eb-144">次の例は、Internet Explorer のプロキシで既定値を使用して、プロキシ アドレスを指定し、ローカル アクセスでプロキシをバイパスします。</span><span class="sxs-lookup"><span data-stu-id="419eb-144">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="419eb-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="419eb-145">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="419eb-146">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="419eb-146">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
