---
title: "&lt;schemaImporterExtensions&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b3cc5e75cded5d468323a2b953bc61271f89e3e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltschemaimporterextensionsgt-element"></a><span data-ttu-id="2de3a-102">&lt;schemaImporterExtensions&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="2de3a-102">&lt;schemaImporterExtensions&gt; Element</span></span>
<span data-ttu-id="2de3a-103">XSD の型を .NET Framework の型にマッピングするために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を含みます。</span><span class="sxs-lookup"><span data-stu-id="2de3a-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="2de3a-104">構成ファイルの詳細については、「[構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2de3a-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2de3a-105">構文</span><span class="sxs-lookup"><span data-stu-id="2de3a-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="2de3a-106">子要素</span><span class="sxs-lookup"><span data-stu-id="2de3a-106">Child Elements</span></span>  
  
|<span data-ttu-id="2de3a-107">要素</span><span class="sxs-lookup"><span data-stu-id="2de3a-107">Element</span></span>|<span data-ttu-id="2de3a-108">説明</span><span class="sxs-lookup"><span data-stu-id="2de3a-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2de3a-109">\<追加 > 要素を\<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="2de3a-109">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)|<span data-ttu-id="2de3a-110">マッピングを作成するために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加します。</span><span class="sxs-lookup"><span data-stu-id="2de3a-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="2de3a-111">親要素</span><span class="sxs-lookup"><span data-stu-id="2de3a-111">Parent Elements</span></span>  
  
|<span data-ttu-id="2de3a-112">要素</span><span class="sxs-lookup"><span data-stu-id="2de3a-112">Element</span></span>|<span data-ttu-id="2de3a-113">説明</span><span class="sxs-lookup"><span data-stu-id="2de3a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2de3a-114">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="2de3a-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="2de3a-115">XML シリアル化を制御する最上位の要素です。</span><span class="sxs-lookup"><span data-stu-id="2de3a-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2de3a-116">例</span><span class="sxs-lookup"><span data-stu-id="2de3a-116">Example</span></span>  
 <span data-ttu-id="2de3a-117">XSD の型を .NET Framework の型にマッピングする際に <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="2de3a-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =   
        "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
/system.sxml.serializaiton>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2de3a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="2de3a-118">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="2de3a-119">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="2de3a-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="2de3a-120">\<dateTimeSerialization> 要素</span><span class="sxs-lookup"><span data-stu-id="2de3a-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [<span data-ttu-id="2de3a-121">\<追加 > 要素を\<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="2de3a-121">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [<span data-ttu-id="2de3a-122">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="2de3a-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
