---
title: XML シリアル化および SOAP シリアル化
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8895a3ca460034cd963bc43e1f27535a51cf9356
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="c67f6-102">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="c67f6-102">XML and SOAP Serialization</span></span>
<span data-ttu-id="c67f6-103">XML シリアル化とは、オブジェクトのパブリック フィールドやパブリック プロパティ、またはメソッドのパラメーターや戻り値を、特定の XML スキーマ定義言語 (XSD: XML Schema Definition Language) ドキュメントに準拠する XML ストリームに変換 (シリアル化) する処理です。</span><span class="sxs-lookup"><span data-stu-id="c67f6-103">XML serialization converts (serializes) the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="c67f6-104">XML シリアル化によって、パブリック プロパティおよびパブリック フィールドを含むクラスの型が厳密に指定され、それらのパブリック メンバーは格納または転送できるようにシリアル形式 (この場合は XML) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="c67f6-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>  
  
 <span data-ttu-id="c67f6-105">XML はオープン標準であるため、XML ストリームは、プラットフォームに関係なく、必要に応じて任意のアプリケーションで処理できます。</span><span class="sxs-lookup"><span data-stu-id="c67f6-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="c67f6-106">たとえば、ASP.NET を使用して作成された XML Web サービスは、<xref:System.Xml.Serialization.XmlSerializer> クラスを使用して、インターネット全体またはイントラネット上の XML Web サービス アプリケーション間でデータを受け渡しする XML ストリームを作成します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="c67f6-107">一方、逆シリアル化は、このような XML ストリームからデータを取得して、元のオブジェクトを再構築します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>  
  
 <span data-ttu-id="c67f6-108">XML シリアル化を使用して、SOAP 仕様に準拠する XML ストリームにオブジェクトをシリアル化することもできます。</span><span class="sxs-lookup"><span data-stu-id="c67f6-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="c67f6-109">SOAP は、XML を使用してプロシージャ呼び出しを転送するために特別にデザインされた、XML に基づくプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="c67f6-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>  
  
 <span data-ttu-id="c67f6-110">オブジェクトをシリアル化または逆シリアル化するには、<xref:System.Xml.Serialization.XmlSerializer> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="c67f6-111">また、シリアル化する対象のクラスを作成するには、XML スキーマ定義ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c67f6-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c67f6-112">In This Section</span></span>  
 [<span data-ttu-id="c67f6-113">XML シリアル化の概要</span><span class="sxs-lookup"><span data-stu-id="c67f6-113">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 <span data-ttu-id="c67f6-114">シリアル化、特に XML シリアル化の一般的な定義を示します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-114">Provides a general definition of serialization, particularly XML serialization.</span></span>  
  
 [<span data-ttu-id="c67f6-115">方法 : オブジェクトをシリアル化する</span><span class="sxs-lookup"><span data-stu-id="c67f6-115">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 <span data-ttu-id="c67f6-116">オブジェクトをシリアル化するための詳細な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-116">Provides step-by-step instructions for serializing an object.</span></span>  
  
 [<span data-ttu-id="c67f6-117">方法 : オブジェクトを逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="c67f6-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 <span data-ttu-id="c67f6-118">オブジェクトを逆シリアル化するための詳細な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-118">Provides step-by-step instructions for deserializing an object.</span></span>  
  
 [<span data-ttu-id="c67f6-119">XML シリアル化の例</span><span class="sxs-lookup"><span data-stu-id="c67f6-119">Examples of XML Serialization</span></span>](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 <span data-ttu-id="c67f6-120">XML シリアル化の基本事項を示す例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-120">Provides examples that demonstrate the basics of XML serialization.</span></span>  
  
 [<span data-ttu-id="c67f6-121">XML スキーマ定義ツールと XML シリアル化</span><span class="sxs-lookup"><span data-stu-id="c67f6-121">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 <span data-ttu-id="c67f6-122">XML スキーマ定義ツールを使用して、特定の XML スキーマ定義言語 (XSD) スキーマに準拠するクラスを作成したり、.dll ファイルから XML スキーマを生成したりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-122">Describes how to use the XML Schema Definition tool to create classes that adhere to a particular XML Schema definition language (XSD) schema, or to generate an XML Schema from a .dll file.</span></span>  
  
 [<span data-ttu-id="c67f6-123">属性を使用した XML シリアル化の制御</span><span class="sxs-lookup"><span data-stu-id="c67f6-123">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 <span data-ttu-id="c67f6-124">属性を使用してシリアル化を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-124">Describes how to control serialization by using attributes.</span></span>  
  
 [<span data-ttu-id="c67f6-125">XML シリアル化を制御する属性</span><span class="sxs-lookup"><span data-stu-id="c67f6-125">Attributes That Control XML Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 <span data-ttu-id="c67f6-126">XML シリアル化の制御に使用する属性を示します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-126">Lists the attributes that are used to control XML serialization.</span></span>  
  
 [<span data-ttu-id="c67f6-127">方法 : XML ストリームの代替要素名を指定する</span><span class="sxs-lookup"><span data-stu-id="c67f6-127">How to: Specify an Alternate Element Name for an XML Stream</span></span>](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 <span data-ttu-id="c67f6-128">シリアル化のオーバーライドにより、複数の XML ストリームを生成する方法を示す高度なシナリオを紹介します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-128">Presents an advanced scenario showing how to generate multiple XML streams by overriding the serialization.</span></span>  
  
 [<span data-ttu-id="c67f6-129">方法 : 派生クラスのシリアル化を制御する</span><span class="sxs-lookup"><span data-stu-id="c67f6-129">How to: Control Serialization of Derived Classes</span></span>](../../../docs/standard/serialization/how-to-control-serialization-of-derived-classes.md)  
 <span data-ttu-id="c67f6-130">派生クラスのシリアル化の制御方法を示す例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-130">Provides an example of how to control the serialization of derived classes.</span></span>  
  
 [<span data-ttu-id="c67f6-131">方法 : XML 要素および XML 属性名を修飾する</span><span class="sxs-lookup"><span data-stu-id="c67f6-131">How to: Qualify XML Element and XML Attribute Names</span></span>](../../../docs/standard/serialization/how-to-qualify-xml-element-and-xml-attribute-names.md)  
 <span data-ttu-id="c67f6-132">XML ストリームでの XML 名前空間の使用方法を定義および制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-132">Describes how to define and control the way in which XML namespaces are used in the XML stream.</span></span>  
  
 [<span data-ttu-id="c67f6-133">XML Web サービスを使用した XML シリアル化</span><span class="sxs-lookup"><span data-stu-id="c67f6-133">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 <span data-ttu-id="c67f6-134">XML Web サービスでの XML シリアル化の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-134">Explains how XML serialization is used in XML Web services.</span></span>  
  
 [<span data-ttu-id="c67f6-135">方法 : オブジェクトを SOAP エンコード済み XML ストリームとしてシリアル化する</span><span class="sxs-lookup"><span data-stu-id="c67f6-135">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 <span data-ttu-id="c67f6-136"><xref:System.Xml.Serialization.XmlSerializer> クラスを使用して、W3C (World Wide Web Consortium) (www.w3.org) のドキュメント『Simple Object Access Protocol (SOAP) 1.1』のセクション 5 に準拠する、エンコード済みの SOAP XML ストリームを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-136">Describes how to use the <xref:System.Xml.Serialization.XmlSerializer> class to create encoded SOAP XML streams that conform to section 5 of the World Wide Web Consortium (www.w3.org) document titled "Simple Object Access Protocol (SOAP) 1.1."</span></span>  
  
 [<span data-ttu-id="c67f6-137">方法 : SOAP エンコード済み XML シリアル化をオーバーライドする</span><span class="sxs-lookup"><span data-stu-id="c67f6-137">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 <span data-ttu-id="c67f6-138">SOAP メッセージとしてのオブジェクトの XML シリアル化をオーバーライドするプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-138">Describes the process for overriding XML serialization of objects as SOAP messages.</span></span>  
  
 [<span data-ttu-id="c67f6-139">エンコード済み SOAP シリアル化を制御する属性</span><span class="sxs-lookup"><span data-stu-id="c67f6-139">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 <span data-ttu-id="c67f6-140">SOAP エンコード済みのシリアル化の制御に使用する属性を示します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-140">Lists the attributes that are used to control SOAP-encoded serialization.</span></span>  
  
 [<span data-ttu-id="c67f6-141">\<system.xml.serialization> 要素</span><span class="sxs-lookup"><span data-stu-id="c67f6-141">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 <span data-ttu-id="c67f6-142">XML シリアル化を制御する最上位の構成要素です。</span><span class="sxs-lookup"><span data-stu-id="c67f6-142">The top-level configuration element for controlling XML serialization.</span></span>  
  
 [<span data-ttu-id="c67f6-143">\<dateTimeSerialization> 要素</span><span class="sxs-lookup"><span data-stu-id="c67f6-143">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 <span data-ttu-id="c67f6-144"><xref:System.DateTime> オブジェクトのシリアル化モードを制御します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-144">Controls the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 [<span data-ttu-id="c67f6-145">\<schemaImporterExtensions> 要素</span><span class="sxs-lookup"><span data-stu-id="c67f6-145">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 <span data-ttu-id="c67f6-146"><xref:System.Xml.Serialization.XmlSchemaImporter> クラスによって使用される型を含みます。</span><span class="sxs-lookup"><span data-stu-id="c67f6-146">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>  
  
 [<span data-ttu-id="c67f6-147">\<xmlSchemaImporterExtensions> の \<add> 要素</span><span class="sxs-lookup"><span data-stu-id="c67f6-147">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 <span data-ttu-id="c67f6-148"><xref:System.Xml.Serialization.XmlSchemaImporter> クラスによって使用される型を追加します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-148">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c67f6-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="c67f6-149">Related Sections</span></span>  
 [<span data-ttu-id="c67f6-150">高度な開発テクノロジ</span><span class="sxs-lookup"><span data-stu-id="c67f6-150">Advanced Development Technologies</span></span>](https://msdn.microsoft.com/library/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 <span data-ttu-id="c67f6-151">.NET Framework での高度な開発タスクと技法に関する詳細情報へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-151">Provides links to more information on sophisticated development tasks and techniques in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="c67f6-152">ASP.NET と XML Web サービス クライアントを使用して作成した XML Web サービス</span><span class="sxs-lookup"><span data-stu-id="c67f6-152">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)  
 <span data-ttu-id="c67f6-153">ASP.NET を使用した XML Web サービスのプログラミング方法について説明するトピックを示します。</span><span class="sxs-lookup"><span data-stu-id="c67f6-153">Provides topics that describe and explain how to program XML Web services using ASP.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c67f6-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="c67f6-154">See Also</span></span>  
 [<span data-ttu-id="c67f6-155">バイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="c67f6-155">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
