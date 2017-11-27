---
title: "&lt;cryptoClasses&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7ed25fa1a2bdedc410fccf48802742766287c438
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcryptoclassesgt-element"></a><span data-ttu-id="7d3e5-102">&lt;cryptoClasses&gt;要素</span><span class="sxs-lookup"><span data-stu-id="7d3e5-102">&lt;cryptoClasses&gt; Element</span></span>
<span data-ttu-id="7d3e5-103">[\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) 要素内の表示名へのマッピングを持つ暗号化クラスのリストを含みます。</span><span class="sxs-lookup"><span data-stu-id="7d3e5-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="7d3e5-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="7d3e5-104">\<configuration></span></span>  
<span data-ttu-id="7d3e5-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="7d3e5-105">\<mscorlib></span></span>  
<span data-ttu-id="7d3e5-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="7d3e5-106">\<cryptographySettings></span></span>  
<span data-ttu-id="7d3e5-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="7d3e5-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="7d3e5-108">\<cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="7d3e5-108">\<cryptoClasses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d3e5-109">構文</span><span class="sxs-lookup"><span data-stu-id="7d3e5-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d3e5-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7d3e5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7d3e5-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d3e5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d3e5-112">属性</span><span class="sxs-lookup"><span data-stu-id="7d3e5-112">Attributes</span></span>  
 <span data-ttu-id="7d3e5-113">なし。</span><span class="sxs-lookup"><span data-stu-id="7d3e5-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7d3e5-114">子要素</span><span class="sxs-lookup"><span data-stu-id="7d3e5-114">Child Elements</span></span>  
  
|<span data-ttu-id="7d3e5-115">要素</span><span class="sxs-lookup"><span data-stu-id="7d3e5-115">Element</span></span>|<span data-ttu-id="7d3e5-116">説明</span><span class="sxs-lookup"><span data-stu-id="7d3e5-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d3e5-117">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="7d3e5-117">\<cryptoClass></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="7d3e5-118">**\<nameEntry>** 要素内の表示名へのマッピングを持つ暗号化クラスを含みます。</span><span class="sxs-lookup"><span data-stu-id="7d3e5-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d3e5-119">親要素</span><span class="sxs-lookup"><span data-stu-id="7d3e5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7d3e5-120">要素</span><span class="sxs-lookup"><span data-stu-id="7d3e5-120">Element</span></span>|<span data-ttu-id="7d3e5-121">説明</span><span class="sxs-lookup"><span data-stu-id="7d3e5-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7d3e5-122">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="7d3e5-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="7d3e5-123">暗号設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="7d3e5-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="7d3e5-124">表示名へのクラスのマッピングを含みます。</span><span class="sxs-lookup"><span data-stu-id="7d3e5-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="7d3e5-125">含まれています、`cryptographySettings`要素。</span><span class="sxs-lookup"><span data-stu-id="7d3e5-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7d3e5-126">例</span><span class="sxs-lookup"><span data-stu-id="7d3e5-126">Example</span></span>  
 <span data-ttu-id="7d3e5-127">次の例では、  **\<cryptoClass >**暗号化クラスを参照し、ランタイムを構成する要素。</span><span class="sxs-lookup"><span data-stu-id="7d3e5-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="7d3e5-128">文字列"RSA"を渡すことができますし、<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>メソッドを使用して、<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>を返すメソッドを`MyCryptoRSAClass`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7d3e5-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d3e5-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d3e5-129">See Also</span></span>  
 <xref:System.Security.Cryptography>  
 [<span data-ttu-id="7d3e5-130">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="7d3e5-130">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="7d3e5-131">暗号化設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="7d3e5-131">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="7d3e5-132">暗号サービス</span><span class="sxs-lookup"><span data-stu-id="7d3e5-132">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="7d3e5-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="7d3e5-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)  
 [<span data-ttu-id="7d3e5-134">暗号化クラスの設定</span><span class="sxs-lookup"><span data-stu-id="7d3e5-134">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
