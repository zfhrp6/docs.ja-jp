---
title: "方法 : オブジェクトを SOAP エンコード済み XML ストリームとしてシリアル化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 34d0529c302f08287f2714e056eb6a536f3b28ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="b35d1-102">方法 : オブジェクトを SOAP エンコード済み XML ストリームとしてシリアル化する</span><span class="sxs-lookup"><span data-stu-id="b35d1-102">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="b35d1-103">SOAP メッセージは XML を使用して作成されるため、<xref:System.Xml.Serialization.XmlSerializer> クラスを使用してクラスをシリアル化し、エンコード済みの SOAP メッセージを生成できます。</span><span class="sxs-lookup"><span data-stu-id="b35d1-103">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="b35d1-104">生成される XML は、[W3C (World Wide Web Consortium) のドキュメント『Simple Object Access Protocol (SOAP) 1.1』のセクション 5](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512) に準拠します。</span><span class="sxs-lookup"><span data-stu-id="b35d1-104">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="b35d1-105">SOAP メッセージを使用して通信を行う XML Web サービスを作成する場合、特殊な SOAP 属性のセットをクラスやクラスのメンバーに適用することで、生成される XML ストリームをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="b35d1-105">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="b35d1-106">属性の一覧については、「[Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b35d1-106">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="b35d1-107">オブジェクトを SOAP エンコード済み XML ストリームとしてシリアル化するには</span><span class="sxs-lookup"><span data-stu-id="b35d1-107">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1.  <span data-ttu-id="b35d1-108">[XML スキーマ定義ツール (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md) を使用して、クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b35d1-108">Create the class using the [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2.  <span data-ttu-id="b35d1-109">`System.Xml.Serialization` の特別な属性を 1 つ以上適用します。</span><span class="sxs-lookup"><span data-stu-id="b35d1-109">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="b35d1-110">「エンコード済み SOAP シリアル化を制御する属性」の一覧を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b35d1-110">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3.  <span data-ttu-id="b35d1-111">新しい `XmlTypeMapping` を作成し、シリアル化されるクラスの型を使用して `SoapReflectionImporter` メソッドを呼び出して、`ImportTypeMapping` を作成します。</span><span class="sxs-lookup"><span data-stu-id="b35d1-111">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="b35d1-112">`ImportTypeMapping` クラスの `SoapReflectionImporter` メソッドを呼び出して `XmlTypeMapping` を作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b35d1-112">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
    ```vb  
    ' Serializes a class named Group as a SOAP message.  
    Dim myTypeMapping As XmlTypeMapping =
        New SoapReflectionImporter().ImportTypeMapping(GetType(Group))  
    ```  
  
    ```csharp  
    // Serializes a class named Group as a SOAP message.  
    XmlTypeMapping myTypeMapping =
        new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
    ```  
  
4.  <span data-ttu-id="b35d1-113">`XmlSerializer` を `XmlTypeMapping` コンストラクターに渡して、<xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b35d1-113">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5.  <span data-ttu-id="b35d1-114">`Serialize` メソッドまたは `Deserialize` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b35d1-114">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b35d1-115">例</span><span class="sxs-lookup"><span data-stu-id="b35d1-115">Example</span></span>  
  
```vb  
' Serializes a class named Group as a SOAP message.  
Dim myTypeMapping As XmlTypeMapping =
    New SoapReflectionImporter().ImportTypeMapping(GetType(Group))
Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
```  
  
```csharp  
// Serializes a class named Group as a SOAP message.  
XmlTypeMapping myTypeMapping =
    new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
```  
  
## <a name="see-also"></a><span data-ttu-id="b35d1-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b35d1-116">See Also</span></span>  
 [<span data-ttu-id="b35d1-117">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="b35d1-117">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [<span data-ttu-id="b35d1-118">エンコード済み SOAP シリアル化を制御する属性</span><span class="sxs-lookup"><span data-stu-id="b35d1-118">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 [<span data-ttu-id="b35d1-119">XML Web サービスを使用した XML シリアル化</span><span class="sxs-lookup"><span data-stu-id="b35d1-119">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 [<span data-ttu-id="b35d1-120">方法 : オブジェクトをシリアル化する</span><span class="sxs-lookup"><span data-stu-id="b35d1-120">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="b35d1-121">方法 : オブジェクトを逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="b35d1-121">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [<span data-ttu-id="b35d1-122">方法 : SOAP エンコード済み XML シリアル化をオーバーライドする</span><span class="sxs-lookup"><span data-stu-id="b35d1-122">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)
