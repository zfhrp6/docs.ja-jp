---
title: '&lt;削除&gt;authenticationModules (ネットワーク設定) の要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a22ddbada0162ba38589b244cab9123f33d7cf45
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742391"
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="a0d41-102">&lt;削除&gt;authenticationModules (ネットワーク設定) の要素</span><span class="sxs-lookup"><span data-stu-id="a0d41-102">&lt;remove&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="a0d41-103">アプリケーションからの認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="a0d41-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="a0d41-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a0d41-104">\<configuration></span></span>  
<span data-ttu-id="a0d41-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="a0d41-105">\<system.net></span></span>  
<span data-ttu-id="a0d41-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="a0d41-106">\<authenticationModules></span></span>  
<span data-ttu-id="a0d41-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="a0d41-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0d41-108">構文</span><span class="sxs-lookup"><span data-stu-id="a0d41-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0d41-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a0d41-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a0d41-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a0d41-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0d41-111">属性</span><span class="sxs-lookup"><span data-stu-id="a0d41-111">Attributes</span></span>  
  
|<span data-ttu-id="a0d41-112">**属性**</span><span class="sxs-lookup"><span data-stu-id="a0d41-112">**Attribute**</span></span>|<span data-ttu-id="a0d41-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="a0d41-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="a0d41-114">**type**</span><span class="sxs-lookup"><span data-stu-id="a0d41-114">**type**</span></span>|<span data-ttu-id="a0d41-115">削除する認証モジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="a0d41-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0d41-116">子要素</span><span class="sxs-lookup"><span data-stu-id="a0d41-116">Child Elements</span></span>  
 <span data-ttu-id="a0d41-117">なし。</span><span class="sxs-lookup"><span data-stu-id="a0d41-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0d41-118">親要素</span><span class="sxs-lookup"><span data-stu-id="a0d41-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a0d41-119">**要素**</span><span class="sxs-lookup"><span data-stu-id="a0d41-119">**Element**</span></span>|<span data-ttu-id="a0d41-120">**説明**</span><span class="sxs-lookup"><span data-stu-id="a0d41-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a0d41-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="a0d41-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="a0d41-122">ネットワーク要求を認証するために使用するモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="a0d41-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0d41-123">コメント</span><span class="sxs-lookup"><span data-stu-id="a0d41-123">Remarks</span></span>  
 <span data-ttu-id="a0d41-124">`remove`要素は、構成ファイルで、または、構成階層でより高いレベルで既に定義されている認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="a0d41-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="a0d41-125">値、`type`属性がクラス名として有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0d41-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a0d41-126">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="a0d41-126">Configuration Files</span></span>  
 <span data-ttu-id="a0d41-127">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a0d41-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0d41-128">例</span><span class="sxs-lookup"><span data-stu-id="a0d41-128">Example</span></span>  
 <span data-ttu-id="a0d41-129">次の例では、認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="a0d41-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0d41-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0d41-130">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="a0d41-131">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="a0d41-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
