---
title: '&lt;cryptographySettings&gt;要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 14b510df192dcff1f005eec4f029aa0f26b967a4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltcryptographysettingsgt-element"></a><span data-ttu-id="d39f4-102">&lt;cryptographySettings&gt;要素</span><span class="sxs-lookup"><span data-stu-id="d39f4-102">&lt;cryptographySettings&gt; Element</span></span>
<span data-ttu-id="d39f4-103">暗号設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="d39f4-103">Contains cryptography settings.</span></span>  
  
 <span data-ttu-id="d39f4-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d39f4-104">\<configuration></span></span>  
<span data-ttu-id="d39f4-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="d39f4-105">\<mscorlib></span></span>  
<span data-ttu-id="d39f4-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="d39f4-106">\<cryptographySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d39f4-107">構文</span><span class="sxs-lookup"><span data-stu-id="d39f4-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d39f4-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d39f4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d39f4-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d39f4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d39f4-110">属性</span><span class="sxs-lookup"><span data-stu-id="d39f4-110">Attributes</span></span>  
 <span data-ttu-id="d39f4-111">なし。</span><span class="sxs-lookup"><span data-stu-id="d39f4-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d39f4-112">子要素</span><span class="sxs-lookup"><span data-stu-id="d39f4-112">Child Elements</span></span>  
  
|<span data-ttu-id="d39f4-113">要素</span><span class="sxs-lookup"><span data-stu-id="d39f4-113">Element</span></span>|<span data-ttu-id="d39f4-114">説明</span><span class="sxs-lookup"><span data-stu-id="d39f4-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d39f4-115">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="d39f4-115">\<cryptoNameMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="d39f4-116">表示名へのクラスのマッピングを含みます。</span><span class="sxs-lookup"><span data-stu-id="d39f4-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="d39f4-117">\<oidMap ></span><span class="sxs-lookup"><span data-stu-id="d39f4-117">\<oidMap></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="d39f4-118">クラスに ASN.1 オブジェクト識別子 (OID) のマッピングが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d39f4-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d39f4-119">親要素</span><span class="sxs-lookup"><span data-stu-id="d39f4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d39f4-120">要素</span><span class="sxs-lookup"><span data-stu-id="d39f4-120">Element</span></span>|<span data-ttu-id="d39f4-121">説明</span><span class="sxs-lookup"><span data-stu-id="d39f4-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d39f4-122">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="d39f4-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="d39f4-123">含まれています、`cryptographySettings`要素。</span><span class="sxs-lookup"><span data-stu-id="d39f4-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d39f4-124">例</span><span class="sxs-lookup"><span data-stu-id="d39f4-124">Example</span></span>  
 <span data-ttu-id="d39f4-125">次の例では、  **\<cryptographySettings >** cryptography 名マッピングおよび OID のマッピングを格納する要素。</span><span class="sxs-lookup"><span data-stu-id="d39f4-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="d39f4-126">この例は、ランタイムを構成できるように<xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType>を返します、`MyHashClass`オブジェクトおよび`MyCryptoClass`クラスのオブジェクト識別子 1.3.36.2.1 にマップします。</span><span class="sxs-lookup"><span data-stu-id="d39f4-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d39f4-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="d39f4-127">See Also</span></span>  
 [<span data-ttu-id="d39f4-128">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="d39f4-128">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="d39f4-129">暗号化設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="d39f4-129">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="d39f4-130">暗号サービス</span><span class="sxs-lookup"><span data-stu-id="d39f4-130">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
