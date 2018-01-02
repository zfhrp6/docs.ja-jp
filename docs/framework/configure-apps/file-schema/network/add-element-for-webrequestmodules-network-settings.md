---
title: "&lt;追加&gt;webRequestModules (ネットワーク設定) の要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9b7d2c0f52ea42fcb98be149ab005cd67c2db46a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="80d8b-102">&lt;追加&gt;webRequestModules (ネットワーク設定) の要素</span><span class="sxs-lookup"><span data-stu-id="80d8b-102">&lt;add&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="80d8b-103">アプリケーションにカスタム Web 要求のモジュールを追加します。</span><span class="sxs-lookup"><span data-stu-id="80d8b-103">Adds a custom Web request module to the application.</span></span>  
  
 <span data-ttu-id="80d8b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="80d8b-104">\<configuration></span></span>  
<span data-ttu-id="80d8b-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="80d8b-105">\<system.net></span></span>  
<span data-ttu-id="80d8b-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="80d8b-106">\<webRequestModules></span></span>  
<span data-ttu-id="80d8b-107">\<add></span><span class="sxs-lookup"><span data-stu-id="80d8b-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80d8b-108">構文</span><span class="sxs-lookup"><span data-stu-id="80d8b-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80d8b-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="80d8b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="80d8b-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="80d8b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80d8b-111">属性</span><span class="sxs-lookup"><span data-stu-id="80d8b-111">Attributes</span></span>  
  
|<span data-ttu-id="80d8b-112">**属性**</span><span class="sxs-lookup"><span data-stu-id="80d8b-112">**Attribute**</span></span>|<span data-ttu-id="80d8b-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="80d8b-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="80d8b-114">この Web 要求モジュールによって処理される要求の URI プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="80d8b-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="80d8b-115">完全修飾型名 (によって示される、<xref:System.Type.FullName%2A>プロパティ) とアセンブリ名 (によって示される、<xref:System.Reflection.Assembly.FullName%2A>プロパティ)、この Web 要求のモジュールを実装する、コンマで区切って指定します。</span><span class="sxs-lookup"><span data-stu-id="80d8b-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80d8b-116">子要素</span><span class="sxs-lookup"><span data-stu-id="80d8b-116">Child Elements</span></span>  
 <span data-ttu-id="80d8b-117">なし。</span><span class="sxs-lookup"><span data-stu-id="80d8b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80d8b-118">親要素</span><span class="sxs-lookup"><span data-stu-id="80d8b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="80d8b-119">**要素**</span><span class="sxs-lookup"><span data-stu-id="80d8b-119">**Element**</span></span>|<span data-ttu-id="80d8b-120">**説明**</span><span class="sxs-lookup"><span data-stu-id="80d8b-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="80d8b-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="80d8b-121">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="80d8b-122">使用してネットワークのホストから情報を要求するモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="80d8b-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80d8b-123">コメント</span><span class="sxs-lookup"><span data-stu-id="80d8b-123">Remarks</span></span>  
 <span data-ttu-id="80d8b-124">`prefix`属性は、指定された Web 要求モジュールを使用する URI プレフィックスを定義します。</span><span class="sxs-lookup"><span data-stu-id="80d8b-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="80d8b-125">Web 要求のモジュールは、通常、HTTP、FTP などの特定のプロトコルを処理する登録しますが、特定のサーバーまたはサーバー上のパスに要求を処理する登録されていることができます。</span><span class="sxs-lookup"><span data-stu-id="80d8b-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="80d8b-126">URI の一致のプレフィックスに渡される Web 要求のモジュールが作成された、<xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="80d8b-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="80d8b-127">値、`prefix`属性が有効な URI: たとえば、"http"または"http://www.contoso.com"の先頭の文字にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="80d8b-127">The value for the `prefix` attribute should be the leading characters of a valid URI --for example, "http", or "http://www.contoso.com".</span></span>  
  
 <span data-ttu-id="80d8b-128">値、`type`属性が有効な型名と対応するアセンブリ名、コンマで区切られたにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="80d8b-128">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma .</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="80d8b-129">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="80d8b-129">Configuration Files</span></span>  
 <span data-ttu-id="80d8b-130">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="80d8b-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80d8b-131">例</span><span class="sxs-lookup"><span data-stu-id="80d8b-131">Example</span></span>  
 <span data-ttu-id="80d8b-132">次の例では、HTTP のカスタム Web 要求のモジュールを登録します。</span><span class="sxs-lookup"><span data-stu-id="80d8b-132">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="80d8b-133">指定したモジュールの正しい値を持つバージョンおよび PublicKeyToken の値を置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="80d8b-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="80d8b-134">参照</span><span class="sxs-lookup"><span data-stu-id="80d8b-134">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="80d8b-135">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="80d8b-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
