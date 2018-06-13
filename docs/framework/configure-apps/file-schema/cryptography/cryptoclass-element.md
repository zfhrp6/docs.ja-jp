---
title: '&lt;cryptoClass&gt;要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 728fff7b8626e227e692c713f4cb05049c14a9f1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742758"
---
# <a name="ltcryptoclassgt-element"></a><span data-ttu-id="ca0f0-102">&lt;cryptoClass&gt;要素</span><span class="sxs-lookup"><span data-stu-id="ca0f0-102">&lt;cryptoClass&gt; Element</span></span>
<span data-ttu-id="ca0f0-103">[\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) 要素内の表示名へのマッピングを持つ暗号化クラスを含みます。</span><span class="sxs-lookup"><span data-stu-id="ca0f0-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="ca0f0-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ca0f0-104">\<configuration></span></span>  
<span data-ttu-id="ca0f0-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="ca0f0-105">\<mscorlib></span></span>  
<span data-ttu-id="ca0f0-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="ca0f0-106">\<cryptographySettings></span></span>  
<span data-ttu-id="ca0f0-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="ca0f0-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="ca0f0-108">\<cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="ca0f0-108">\<cryptoClasses></span></span>  
<span data-ttu-id="ca0f0-109">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="ca0f0-109">\<cryptoClass></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca0f0-110">構文</span><span class="sxs-lookup"><span data-stu-id="ca0f0-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca0f0-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ca0f0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ca0f0-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ca0f0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca0f0-113">属性</span><span class="sxs-lookup"><span data-stu-id="ca0f0-113">Attributes</span></span>  
  
|<span data-ttu-id="ca0f0-114">属性</span><span class="sxs-lookup"><span data-stu-id="ca0f0-114">Attribute</span></span>|<span data-ttu-id="ca0f0-115">説明</span><span class="sxs-lookup"><span data-stu-id="ca0f0-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="ca0f0-116">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="ca0f0-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="ca0f0-117">暗号化クラスの情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ca0f0-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="ca0f0-118">この属性を使用して、クラスの短い名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="ca0f0-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="ca0f0-119">指定された要件を満たしている文字列を指定する必要があります[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca0f0-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca0f0-120">子要素</span><span class="sxs-lookup"><span data-stu-id="ca0f0-120">Child Elements</span></span>  
 <span data-ttu-id="ca0f0-121">なし。</span><span class="sxs-lookup"><span data-stu-id="ca0f0-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ca0f0-122">親要素</span><span class="sxs-lookup"><span data-stu-id="ca0f0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ca0f0-123">要素</span><span class="sxs-lookup"><span data-stu-id="ca0f0-123">Element</span></span>|<span data-ttu-id="ca0f0-124">説明</span><span class="sxs-lookup"><span data-stu-id="ca0f0-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ca0f0-125">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="ca0f0-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="ca0f0-126">[\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) 要素内の表示名へのマッピングを持つ暗号化クラスのリストを含みます。</span><span class="sxs-lookup"><span data-stu-id="ca0f0-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="ca0f0-127">暗号設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="ca0f0-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="ca0f0-128">表示名へのクラスのマッピングを含みます。</span><span class="sxs-lookup"><span data-stu-id="ca0f0-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="ca0f0-129">[ \<cryptographySettings >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)要素を含みます。</span><span class="sxs-lookup"><span data-stu-id="ca0f0-129">Contains the [\<cryptographySettings>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ca0f0-130">例</span><span class="sxs-lookup"><span data-stu-id="ca0f0-130">Example</span></span>  
 <span data-ttu-id="ca0f0-131">次の例では、  **\<cryptoClass >** 暗号化クラスを参照し、ランタイムを構成する要素。</span><span class="sxs-lookup"><span data-stu-id="ca0f0-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="ca0f0-132">文字列"RSA"を渡すことができますし、<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>メソッドを使用して、<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>を返すメソッドを`MyCryptoRSAClass`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ca0f0-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca0f0-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca0f0-133">See Also</span></span>  
 [<span data-ttu-id="ca0f0-134">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="ca0f0-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="ca0f0-135">暗号化設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="ca0f0-135">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="ca0f0-136">暗号サービス</span><span class="sxs-lookup"><span data-stu-id="ca0f0-136">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="ca0f0-137">暗号化クラスの設定</span><span class="sxs-lookup"><span data-stu-id="ca0f0-137">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
