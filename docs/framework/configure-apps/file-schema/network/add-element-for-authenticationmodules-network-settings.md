---
title: '&lt;追加&gt;authenticationModules (ネットワーク設定) の要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/add
helpviewer_keywords:
- authenticationModules, add element
- add element, authenticationModules
- <authenticationModules>, add element
- <add> element, authenticationModules
ms.assetid: 333c5fb0-a2ab-4db8-8531-a7fe37bb9b5b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 471e36bb584164b851e7a06c0e682ba9872f7910
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742901"
---
# <a name="ltaddgt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="3f1b2-102">&lt;追加&gt;authenticationModules (ネットワーク設定) の要素</span><span class="sxs-lookup"><span data-stu-id="3f1b2-102">&lt;add&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="3f1b2-103">アプリケーションに認証モジュールを追加します。</span><span class="sxs-lookup"><span data-stu-id="3f1b2-103">Adds an authentication module to the application.</span></span>  
  
 <span data-ttu-id="3f1b2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3f1b2-104">\<configuration></span></span>  
<span data-ttu-id="3f1b2-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="3f1b2-105">\<system.net></span></span>  
<span data-ttu-id="3f1b2-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="3f1b2-106">\<authenticationModules></span></span>  
<span data-ttu-id="3f1b2-107">\<add></span><span class="sxs-lookup"><span data-stu-id="3f1b2-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f1b2-108">構文</span><span class="sxs-lookup"><span data-stu-id="3f1b2-108">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f1b2-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3f1b2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3f1b2-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3f1b2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f1b2-111">属性</span><span class="sxs-lookup"><span data-stu-id="3f1b2-111">Attributes</span></span>  
  
|<span data-ttu-id="3f1b2-112">**属性**</span><span class="sxs-lookup"><span data-stu-id="3f1b2-112">**Attribute**</span></span>|<span data-ttu-id="3f1b2-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="3f1b2-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="3f1b2-114">完全修飾型名 (によって示される、<xref:System.Type.FullName%2A>プロパティ) とアセンブリ名 (によって示される、<xref:System.Reflection.Assembly.FullName%2A>プロパティ)、コンマで区切って指定します。</span><span class="sxs-lookup"><span data-stu-id="3f1b2-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f1b2-115">子要素</span><span class="sxs-lookup"><span data-stu-id="3f1b2-115">Child Elements</span></span>  
 <span data-ttu-id="3f1b2-116">なし。</span><span class="sxs-lookup"><span data-stu-id="3f1b2-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f1b2-117">親要素</span><span class="sxs-lookup"><span data-stu-id="3f1b2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3f1b2-118">**要素**</span><span class="sxs-lookup"><span data-stu-id="3f1b2-118">**Element**</span></span>|<span data-ttu-id="3f1b2-119">**説明**</span><span class="sxs-lookup"><span data-stu-id="3f1b2-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3f1b2-120">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="3f1b2-120">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="3f1b2-121">ネットワーク要求を認証するために使用するモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="3f1b2-121">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f1b2-122">コメント</span><span class="sxs-lookup"><span data-stu-id="3f1b2-122">Remarks</span></span>  
 <span data-ttu-id="3f1b2-123">`add`要素は、登録済みの認証モジュールの一覧の末尾に認証モジュールを追加します。</span><span class="sxs-lookup"><span data-stu-id="3f1b2-123">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="3f1b2-124">認証モジュールは、一覧に追加された順序で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3f1b2-124">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="3f1b2-125">値、`type`属性が有効な型名と対応するアセンブリ名、コンマで区切られたにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f1b2-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3f1b2-126">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="3f1b2-126">Configuration Files</span></span>  
 <span data-ttu-id="3f1b2-127">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="3f1b2-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f1b2-128">例</span><span class="sxs-lookup"><span data-stu-id="3f1b2-128">Example</span></span>  
 <span data-ttu-id="3f1b2-129">次の例では、既定の認証モジュールを有効します。</span><span class="sxs-lookup"><span data-stu-id="3f1b2-129">The following example enables the default authentication modules.</span></span> <span data-ttu-id="3f1b2-130">指定したモジュールの正しい値を持つバージョンおよび PublicKeyToken の値を置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f1b2-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
        <authenticationModules>  
            <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NegotiateClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.KerberosClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NtlmClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.BasicClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f1b2-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f1b2-131">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="3f1b2-132">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="3f1b2-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
