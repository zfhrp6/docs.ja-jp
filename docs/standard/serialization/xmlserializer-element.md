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
ms.openlocfilehash: 17e4fcd1b471a5197f2e6a30bad10cbdbe22f216
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltxmlserializergt-element"></a><span data-ttu-id="bca2e-102">&lt;xmlSerializer&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="bca2e-102">&lt;xmlSerializer&gt; Element</span></span>
<span data-ttu-id="bca2e-103"><xref:System.Xml.Serialization.XmlSerializer> の進行状況の追加チェックを行うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="bca2e-103">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="bca2e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="bca2e-104">\<configuration></span></span>  
<span data-ttu-id="bca2e-105">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="bca2e-105">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca2e-106">構文</span><span class="sxs-lookup"><span data-stu-id="bca2e-106">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bca2e-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="bca2e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="bca2e-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="bca2e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bca2e-109">属性</span><span class="sxs-lookup"><span data-stu-id="bca2e-109">Attributes</span></span>  
  
|<span data-ttu-id="bca2e-110">属性</span><span class="sxs-lookup"><span data-stu-id="bca2e-110">Attribute</span></span>|<span data-ttu-id="bca2e-111">説明</span><span class="sxs-lookup"><span data-stu-id="bca2e-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bca2e-112">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="bca2e-112">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="bca2e-113"><xref:System.Xml.Serialization.XmlSerializer> の進行状況をチェックするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="bca2e-113">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="bca2e-114">属性は "true" または "false" に設定します。</span><span class="sxs-lookup"><span data-stu-id="bca2e-114">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="bca2e-115">既定値は "true" です。</span><span class="sxs-lookup"><span data-stu-id="bca2e-115">The default is "true".</span></span>|  
|<span data-ttu-id="bca2e-116">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="bca2e-116">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="bca2e-117">C# コードをファイルに記述し、それをアセンブリにコンパイルすることによってアセンブリを生成する従来のシリアル化の生成を、<xref:System.Xml.Serialization.XmlSerializer> で使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="bca2e-117">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="bca2e-118">既定値は **false** です。</span><span class="sxs-lookup"><span data-stu-id="bca2e-118">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bca2e-119">子要素</span><span class="sxs-lookup"><span data-stu-id="bca2e-119">Child Elements</span></span>  
 <span data-ttu-id="bca2e-120">なし。</span><span class="sxs-lookup"><span data-stu-id="bca2e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bca2e-121">親要素</span><span class="sxs-lookup"><span data-stu-id="bca2e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="bca2e-122">要素</span><span class="sxs-lookup"><span data-stu-id="bca2e-122">Element</span></span>|<span data-ttu-id="bca2e-123">説明</span><span class="sxs-lookup"><span data-stu-id="bca2e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bca2e-124">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="bca2e-124">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="bca2e-125"><xref:System.Xml.Serialization.XmlSerializer> クラスおよび <xref:System.Xml.Serialization.XmlSchemaImporter> クラスの構成設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="bca2e-125">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bca2e-126">コメント</span><span class="sxs-lookup"><span data-stu-id="bca2e-126">Remarks</span></span>  
 <span data-ttu-id="bca2e-127">既定では、<xref:System.Xml.Serialization.XmlSerializer> は、信頼できないデータを逆シリアル化する際に、サービス拒否攻撃の可能性に対するセキュリティをさらに高めることができます。</span><span class="sxs-lookup"><span data-stu-id="bca2e-127">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="bca2e-128">これは、逆シリアル化中に無限ループを検出することにより行われます。</span><span class="sxs-lookup"><span data-stu-id="bca2e-128">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="bca2e-129">このような状態が検出されると例外がスローされ、"内部エラー: 逆シリアル化は基になるストリームのセキュリティの強化に失敗しました。" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bca2e-129">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="bca2e-130">このメッセージは、必ずしもサービス拒否攻撃を受けていることを示すわけではありません。</span><span class="sxs-lookup"><span data-stu-id="bca2e-130">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="bca2e-131">まれに、無限ループ検出機構で誤検出が発生し、適正な受信メッセージに対して例外がスローされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bca2e-131">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="bca2e-132">特定のアプリケーションにおいて、セキュリティの強化によって適正なメッセージが拒否される場合は、**checkDeserializeAdvances** 属性を "false" に設定します。</span><span class="sxs-lookup"><span data-stu-id="bca2e-132">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="bca2e-133">例</span><span class="sxs-lookup"><span data-stu-id="bca2e-133">Example</span></span>  
 <span data-ttu-id="bca2e-134">**checkDeserializeAdvances** 属性を "false" に設定するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bca2e-134">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bca2e-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="bca2e-135">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="bca2e-136">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="bca2e-136">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [<span data-ttu-id="bca2e-137">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="bca2e-137">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
