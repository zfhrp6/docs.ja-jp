---
title: "&lt;xmlSerializer&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 059fe3661878b51ef27facc2888286ecd1aaa97a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="ltxmlserializergt-element"></a><span data-ttu-id="3e895-102">&lt;xmlSerializer&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="3e895-102">&lt;xmlSerializer&gt; Element</span></span>
<span data-ttu-id="3e895-103"><xref:System.Xml.Serialization.XmlSerializer> の進行状況の追加チェックを行うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3e895-103">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="3e895-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3e895-104">\<configuration></span></span>  
<span data-ttu-id="3e895-105">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="3e895-105">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e895-106">構文</span><span class="sxs-lookup"><span data-stu-id="3e895-106">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e895-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3e895-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3e895-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e895-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e895-109">属性</span><span class="sxs-lookup"><span data-stu-id="3e895-109">Attributes</span></span>  
  
|<span data-ttu-id="3e895-110">属性</span><span class="sxs-lookup"><span data-stu-id="3e895-110">Attribute</span></span>|<span data-ttu-id="3e895-111">説明</span><span class="sxs-lookup"><span data-stu-id="3e895-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e895-112">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="3e895-112">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="3e895-113"><xref:System.Xml.Serialization.XmlSerializer> の進行状況をチェックするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3e895-113">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="3e895-114">属性は "true" または "false" に設定します。</span><span class="sxs-lookup"><span data-stu-id="3e895-114">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="3e895-115">既定値は "true" です。</span><span class="sxs-lookup"><span data-stu-id="3e895-115">The default is "true".</span></span>|  
|<span data-ttu-id="3e895-116">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="3e895-116">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="3e895-117">C# コードをファイルに記述し、それをアセンブリにコンパイルすることによってアセンブリを生成する従来のシリアル化の生成を、<xref:System.Xml.Serialization.XmlSerializer> で使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3e895-117">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="3e895-118">既定値は **false** です。</span><span class="sxs-lookup"><span data-stu-id="3e895-118">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e895-119">子要素</span><span class="sxs-lookup"><span data-stu-id="3e895-119">Child Elements</span></span>  
 <span data-ttu-id="3e895-120">なし。</span><span class="sxs-lookup"><span data-stu-id="3e895-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e895-121">親要素</span><span class="sxs-lookup"><span data-stu-id="3e895-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3e895-122">要素</span><span class="sxs-lookup"><span data-stu-id="3e895-122">Element</span></span>|<span data-ttu-id="3e895-123">説明</span><span class="sxs-lookup"><span data-stu-id="3e895-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e895-124">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="3e895-124">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="3e895-125"><xref:System.Xml.Serialization.XmlSerializer> クラスおよび <xref:System.Xml.Serialization.XmlSchemaImporter> クラスの構成設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="3e895-125">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e895-126">コメント</span><span class="sxs-lookup"><span data-stu-id="3e895-126">Remarks</span></span>  
 <span data-ttu-id="3e895-127">既定では、<xref:System.Xml.Serialization.XmlSerializer> は、信頼できないデータを逆シリアル化する際に、サービス拒否攻撃の可能性に対するセキュリティをさらに高めることができます。</span><span class="sxs-lookup"><span data-stu-id="3e895-127">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="3e895-128">これは、逆シリアル化中に無限ループを検出することにより行われます。</span><span class="sxs-lookup"><span data-stu-id="3e895-128">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="3e895-129">このような状態が検出されると例外がスローされ、"内部エラー: 逆シリアル化は基になるストリームのセキュリティの強化に失敗しました。" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3e895-129">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="3e895-130">このメッセージは、必ずしもサービス拒否攻撃を受けていることを示すわけではありません。</span><span class="sxs-lookup"><span data-stu-id="3e895-130">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="3e895-131">まれに、無限ループ検出機構で誤検出が発生し、適正な受信メッセージに対して例外がスローされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3e895-131">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="3e895-132">特定のアプリケーションにおいて、セキュリティの強化によって適正なメッセージが拒否される場合は、**checkDeserializeAdvances** 属性を "false" に設定します。</span><span class="sxs-lookup"><span data-stu-id="3e895-132">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e895-133">例</span><span class="sxs-lookup"><span data-stu-id="3e895-133">Example</span></span>  
 <span data-ttu-id="3e895-134">**checkDeserializeAdvances** 属性を "false" に設定するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3e895-134">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e895-135">参照</span><span class="sxs-lookup"><span data-stu-id="3e895-135">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="3e895-136">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="3e895-136">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [<span data-ttu-id="3e895-137">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="3e895-137">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
