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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c7b1e335f03c5558d7680567fe19f3de2f3f8d78
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="ltschemaimporterextensionsgt-element"></a><span data-ttu-id="edecc-102">&lt;schemaImporterExtensions&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="edecc-102">&lt;schemaImporterExtensions&gt; Element</span></span>
<span data-ttu-id="edecc-103">XSD の型を .NET Framework の型にマッピングするために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を含みます。</span><span class="sxs-lookup"><span data-stu-id="edecc-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="edecc-104">構成ファイルの詳細については、「[構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="edecc-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edecc-105">構文</span><span class="sxs-lookup"><span data-stu-id="edecc-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="edecc-106">子要素</span><span class="sxs-lookup"><span data-stu-id="edecc-106">Child Elements</span></span>  
  
|<span data-ttu-id="edecc-107">要素</span><span class="sxs-lookup"><span data-stu-id="edecc-107">Element</span></span>|<span data-ttu-id="edecc-108">説明</span><span class="sxs-lookup"><span data-stu-id="edecc-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="edecc-109">\<xmlSchemaImporterExtensions> の \<add> 要素</span><span class="sxs-lookup"><span data-stu-id="edecc-109">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)|<span data-ttu-id="edecc-110">マッピングを作成するために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加します。</span><span class="sxs-lookup"><span data-stu-id="edecc-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="edecc-111">親要素</span><span class="sxs-lookup"><span data-stu-id="edecc-111">Parent Elements</span></span>  
  
|<span data-ttu-id="edecc-112">要素</span><span class="sxs-lookup"><span data-stu-id="edecc-112">Element</span></span>|<span data-ttu-id="edecc-113">説明</span><span class="sxs-lookup"><span data-stu-id="edecc-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="edecc-114">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="edecc-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="edecc-115">XML シリアル化を制御する最上位の要素です。</span><span class="sxs-lookup"><span data-stu-id="edecc-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="edecc-116">例</span><span class="sxs-lookup"><span data-stu-id="edecc-116">Example</span></span>  
 <span data-ttu-id="edecc-117">XSD の型を .NET Framework の型にマッピングする際に <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="edecc-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="edecc-118">参照</span><span class="sxs-lookup"><span data-stu-id="edecc-118">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="edecc-119">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="edecc-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="edecc-120">\<dateTimeSerialization> 要素</span><span class="sxs-lookup"><span data-stu-id="edecc-120">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 [<span data-ttu-id="edecc-121">\<xmlSchemaImporterExtensions> の \<add> 要素</span><span class="sxs-lookup"><span data-stu-id="edecc-121">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [<span data-ttu-id="edecc-122">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="edecc-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
