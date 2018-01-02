---
title: "&lt;cryptoNameMapping&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b0ddd8368b84ec1b218f2c48fddd898f83fc71fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcryptonamemappinggt-element"></a><span data-ttu-id="9ad12-102">&lt;cryptoNameMapping&gt;要素</span><span class="sxs-lookup"><span data-stu-id="9ad12-102">&lt;cryptoNameMapping&gt; Element</span></span>
<span data-ttu-id="9ad12-103">表示名へのクラスのマッピングを含みます。</span><span class="sxs-lookup"><span data-stu-id="9ad12-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="9ad12-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9ad12-104">\<configuration></span></span>  
<span data-ttu-id="9ad12-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="9ad12-105">\<mscorlib></span></span>  
<span data-ttu-id="9ad12-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="9ad12-106">\<cryptographySettings></span></span>  
<span data-ttu-id="9ad12-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="9ad12-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ad12-108">構文</span><span class="sxs-lookup"><span data-stu-id="9ad12-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ad12-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9ad12-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9ad12-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ad12-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ad12-111">属性</span><span class="sxs-lookup"><span data-stu-id="9ad12-111">Attributes</span></span>  
 <span data-ttu-id="9ad12-112">なし。</span><span class="sxs-lookup"><span data-stu-id="9ad12-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9ad12-113">子要素</span><span class="sxs-lookup"><span data-stu-id="9ad12-113">Child Elements</span></span>  
  
|<span data-ttu-id="9ad12-114">要素</span><span class="sxs-lookup"><span data-stu-id="9ad12-114">Element</span></span>|<span data-ttu-id="9ad12-115">説明</span><span class="sxs-lookup"><span data-stu-id="9ad12-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="9ad12-116">**\<nameEntry>** 要素内の表示名へのマッピングを持つ暗号化クラスのリストを含みます。</span><span class="sxs-lookup"><span data-stu-id="9ad12-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="9ad12-117">アルゴリズムの表示名にクラス名をマップして、1 つのクラスが多くの表示名を持つことを許可します。</span><span class="sxs-lookup"><span data-stu-id="9ad12-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ad12-118">親要素</span><span class="sxs-lookup"><span data-stu-id="9ad12-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9ad12-119">要素</span><span class="sxs-lookup"><span data-stu-id="9ad12-119">Element</span></span>|<span data-ttu-id="9ad12-120">説明</span><span class="sxs-lookup"><span data-stu-id="9ad12-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9ad12-121">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="9ad12-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="9ad12-122">暗号設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="9ad12-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="9ad12-123">表示名へのクラスのマッピングを含みます。</span><span class="sxs-lookup"><span data-stu-id="9ad12-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="9ad12-124">含まれています、 \<cryptographySettings > 要素。</span><span class="sxs-lookup"><span data-stu-id="9ad12-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9ad12-125">例</span><span class="sxs-lookup"><span data-stu-id="9ad12-125">Example</span></span>  
 <span data-ttu-id="9ad12-126">次の例を使用する方法を示しています、  **\<cryptoNameMapping >**暗号化クラスを参照し、ランタイムを構成する要素。</span><span class="sxs-lookup"><span data-stu-id="9ad12-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="9ad12-127">文字列"RSA"を渡すことができますし、<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>メソッドを使用して、<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>を返すメソッドを`MyCryptoRSAClass`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9ad12-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ad12-128">参照</span><span class="sxs-lookup"><span data-stu-id="9ad12-128">See Also</span></span>  
 [<span data-ttu-id="9ad12-129">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="9ad12-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="9ad12-130">暗号化設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="9ad12-130">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="9ad12-131">暗号サービス</span><span class="sxs-lookup"><span data-stu-id="9ad12-131">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="9ad12-132">暗号化クラスの設定</span><span class="sxs-lookup"><span data-stu-id="9ad12-132">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
