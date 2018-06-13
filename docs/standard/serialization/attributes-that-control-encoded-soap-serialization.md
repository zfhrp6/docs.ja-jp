---
title: エンコード済み SOAP シリアル化を制御する属性
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: b7f0d8bf7c7c1013937f7ce0a87c326b707fbc6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582423"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a><span data-ttu-id="859fa-102">エンコード済み SOAP シリアル化を制御する属性</span><span class="sxs-lookup"><span data-stu-id="859fa-102">Attributes That Control Encoded SOAP Serialization</span></span> 
<span data-ttu-id="859fa-103">World Wide Web コンソーシアム (www.w3.org) のドキュメント『Simple Object Access Protocol (SOAP) 1.1』には、SOAP パラメーターのエンコード方法について説明したオプションのセクション (セクション 5) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="859fa-103">The World Wide Web Consortium (www.w3.org) document named "Simple Object Access Protocol (SOAP) 1.1" contains an optional section (section 5) that describes how SOAP parameters can be encoded.</span></span> <span data-ttu-id="859fa-104">このセクション 5 の仕様に準拠するには、<xref:System.Xml.Serialization> 名前空間で指定されている特殊な属性セットを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="859fa-104">To conform to section 5 of the specification, you must use a special set of attributes found in the <xref:System.Xml.Serialization> namespace.</span></span> <span data-ttu-id="859fa-105">これらの属性をクラスやクラスのメンバーに適宜適用し、<xref:System.Xml.Serialization.XmlSerializer> を使用して、クラスのインスタンスをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="859fa-105">Apply those attributes as appropriate to classes and members of classes, and then use the <xref:System.Xml.Serialization.XmlSerializer> to serialize instances of the class or classes.</span></span>  
  
 <span data-ttu-id="859fa-106">これらの属性、およびその適用対象と機能を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="859fa-106">The following table shows the attributes, where they can be applied, and what they do.</span></span> <span data-ttu-id="859fa-107">これらの属性を使用する XML シリアル化の制御の詳細については、「[How to: Serialize an Object as a SOAP-Encoded XML Stream](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)」(方法 : オブジェクトを SOAP エンコード済み XML ストリームとしてシリアル化する) および「[How to: Override Encoded SOAP XML Serialization](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)」(方法 : SOAP エンコード済み XML シリアル化をオーバーライドする) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="859fa-107">For more information about using these attributes to control XML serialization, see [How to: Serialize an Object as a SOAP-Encoded XML Stream](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) and [How to: Override Encoded SOAP XML Serialization](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md).</span></span>  
  
 <span data-ttu-id="859fa-108">属性の詳細については、「[属性](../../../docs/standard/attributes/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="859fa-108">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span>  
  
|<span data-ttu-id="859fa-109">属性</span><span class="sxs-lookup"><span data-stu-id="859fa-109">Attribute</span></span>|<span data-ttu-id="859fa-110">対象</span><span class="sxs-lookup"><span data-stu-id="859fa-110">Applies to</span></span>|<span data-ttu-id="859fa-111">指定内容</span><span class="sxs-lookup"><span data-stu-id="859fa-111">Specifies</span></span>|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|<span data-ttu-id="859fa-112">パブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値</span><span class="sxs-lookup"><span data-stu-id="859fa-112">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="859fa-113">クラス メンバーを XML 属性としてシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="859fa-113">The class member will be serialized as an XML attribute.</span></span>|  
|<xref:System.Xml.Serialization.SoapElementAttribute>|<span data-ttu-id="859fa-114">パブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値</span><span class="sxs-lookup"><span data-stu-id="859fa-114">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="859fa-115">クラスを XML 要素としてシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="859fa-115">The class will be serialized as an XML element.</span></span>|  
|<xref:System.Xml.Serialization.SoapEnumAttribute>|<span data-ttu-id="859fa-116">列挙体識別子であるパブリック フィールド</span><span class="sxs-lookup"><span data-stu-id="859fa-116">Public field that is an enumeration identifier.</span></span>|<span data-ttu-id="859fa-117">列挙体のメンバーの要素名を指定します。</span><span class="sxs-lookup"><span data-stu-id="859fa-117">The element name of an enumeration member.</span></span>|  
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|<span data-ttu-id="859fa-118">パブリック プロパティとパブリック フィールド</span><span class="sxs-lookup"><span data-stu-id="859fa-118">Public properties and fields.</span></span>|<span data-ttu-id="859fa-119">クラスのシリアル化時に、そのクラスに含まれているプロパティまたはフィールドを無視します。</span><span class="sxs-lookup"><span data-stu-id="859fa-119">The property or field should be ignored when the containing class is serialized.</span></span>|  
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|<span data-ttu-id="859fa-120">パブリック派生クラス宣言、およびパブリック メソッド (Web サービス記述言語 (WSDL: Web Service Description Language) ドキュメント用)</span><span class="sxs-lookup"><span data-stu-id="859fa-120">Public-derived class declarations and public methods for Web Services Description Language (WSDL) documents.</span></span>|<span data-ttu-id="859fa-121">シリアル化時に認識されるように、スキーマの生成時にその型を対象に含めます。</span><span class="sxs-lookup"><span data-stu-id="859fa-121">The type should be included when generating schemas (to be recognized when serialized).</span></span>|  
|<xref:System.Xml.Serialization.SoapTypeAttribute>|<span data-ttu-id="859fa-122">パブリック クラス宣言</span><span class="sxs-lookup"><span data-stu-id="859fa-122">Public class declarations.</span></span>|<span data-ttu-id="859fa-123">クラスを XML 型としてシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="859fa-123">The class should be serialized as an XML type.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="859fa-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="859fa-124">See Also</span></span>  
 [<span data-ttu-id="859fa-125">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="859fa-125">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [<span data-ttu-id="859fa-126">方法 : オブジェクトを SOAP エンコード済み XML ストリームとしてシリアル化する</span><span class="sxs-lookup"><span data-stu-id="859fa-126">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 [<span data-ttu-id="859fa-127">方法 : SOAP エンコード済み XML シリアル化をオーバーライドする</span><span class="sxs-lookup"><span data-stu-id="859fa-127">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 [<span data-ttu-id="859fa-128">属性</span><span class="sxs-lookup"><span data-stu-id="859fa-128">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="859fa-129">方法 : オブジェクトをシリアル化する</span><span class="sxs-lookup"><span data-stu-id="859fa-129">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="859fa-130">方法 : オブジェクトを逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="859fa-130">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
