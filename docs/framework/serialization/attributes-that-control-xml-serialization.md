---
title: "XML シリアル化を制御する属性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "属性 [.NET Framework], XML シリアル化"
  - "クラス, シリアル化"
  - "シリアル化, 属性"
  - "XML スキーマ, シリアル化"
  - "XML シリアル化, 属性"
  - "XmlSerializer クラス, シリアル化"
ms.assetid: 414b820f-a696-4206-b576-2711d85490c7
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# XML シリアル化を制御する属性
次の表に示す属性をクラスおよびクラス メンバーに適用すると、[XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx) がそのクラスのインスタンスをシリアル化または逆シリアル化する方法を制御できます。これらの属性で XML シリアル化を制御する方法については、「[属性を使用した XML シリアル化の制御](../../../docs/framework/serialization/controlling-xml-serialization-using-attributes.md)」を参照してください。  
  
 また、これらの属性を使用して、XML Web サービスによって生成されるリテラル スタイルの SOAP メッセージを制御することもできます。これらの属性を XML Web サービス メソッドに適用する方法の詳細については、「[XML Web サービスを使用した XML シリアル化](../../../docs/framework/serialization/xml-serialization-with-xml-web-services.md)」を参照してください。  
  
 属性の詳細については、「[属性](../../../docs/standard/attributes/index.md)」を参照してください。  
  
|属性|対象|機能|  
|--------|--------|--------|  
|[XmlAnyAttributeAttribute](frlrfSystemXmlSerializationXmlAnyAttributeAttributeClassTopic)|[XmlAttribute](frlrfSystemXmlXmlAttributeClassTopic) オブジェクトの配列を返すパブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|逆シリアル化時に、スキーマで未定義のすべての XML 属性を表す [XmlAttribute](frlrfSystemXmlXmlAttributeClassTopic) オブジェクトを配列に挿入します。|  
|[XmlAnyElementAttribute](frlrfSystemXmlSerializationXmlAnyElementAttributeClassTopic)|[XmlElement](frlrfSystemXmlXmlElementClassTopic) オブジェクトの配列を返すパブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|逆シリアル化時に、スキーマで未定義のすべての XML 要素を表す [XmlElement](frlrfSystemXmlXmlElementClassTopic) オブジェクトを配列に挿入します。|  
|[XmlArrayAttribute](frlrfSystemXmlSerializationXmlArrayAttributeClassTopic)|複合オブジェクトの配列を返すパブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|配列のメンバーを XML 配列のメンバーとして生成します。|  
|[XmlArrayItemAttribute](frlrfSystemXmlSerializationXmlArrayItemAttributeClassTopic)|複合オブジェクトの配列を返すパブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|配列に挿入できる派生型を指定します。通常、[XmlArrayAttribute](frlrfSystemXmlSerializationXmlArrayAttributeClassTopic) と共に適用されます。|  
|[XmlAttributeAttribute](frlrfSystemXmlSerializationXmlAttributeAttributeClassTopic)|パブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|メンバーを XML 属性としてシリアル化します。|  
|[XmlChoiceIdentifierAttribute](frlrfSystemXmlSerializationXmlChoiceIdentifierAttributeClassTopic)|パブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|列挙体を使用して、メンバーを明確に区別できるようにします。|  
|[XmlElementAttribute](frlrfSystemXmlSerializationXmlElementAttributeClassTopic)|パブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|フィールドまたはプロパティを XML 要素としてシリアル化します。|  
|[XmlEnumAttribute](frlrfSystemXmlSerializationXmlEnumAttributeClassTopic)|列挙体識別子であるパブリック フィールド|列挙体のメンバーの要素名を指定します。|  
|[XmlIgnoreAttribute](frlrfSystemXmlSerializationXmlIgnoreAttributeClassTopic)|パブリック プロパティとパブリック フィールド|クラスのシリアル化時に、そのクラスに含まれているプロパティまたはフィールドを無視します。|  
|[XmlIncludeAttribute](frlrfSystemXmlSerializationXmlIncludeAttributeClassTopic)|パブリック派生クラス宣言、およびパブリック メソッドの戻り値 \(Web サービス記述言語 \(WSDL: Web Service Description Language\) ドキュメント用\)|シリアル化されたときにクラスが認識されるように、スキーマの生成時にそのクラスを対象に含めます。|  
|[XmlRootAttribute](frlrfSystemXmlSerializationXmlRootAttributeClassTopic)|パブリック クラス宣言|属性ターゲットを XML ルート要素として XML シリアル化する方法を制御します。この属性を使用して、さらに名前空間と要素名を指定できます。|  
|[XmlTextAttribute](frlrfSystemXmlSerializationXmlTextAttributeClassTopic)|パブリック プロパティとパブリック フィールド|プロパティまたはフィールドを XML テキストとしてシリアル化します。|  
|[XmlTypeAttribute](frlrfSystemXmlSerializationXmlTypeAttributeClassTopic)|パブリック クラス宣言|XML 型の名前および名前空間を指定します。|  
  
 [System.Xml.Serialization](frlrfSystemxmlserialization) 名前空間にあるこれらの属性の他に、[System.ComponentModel.DefaultValueAttribute](frlrfSystemComponentModelDefaultValueAttributeClassTopic) 属性もフィールドに適用できます。**DefaultValueAttribute** は、メンバーの値が指定されていない場合に、メンバーに自動的に割り当てられる値を設定します。  
  
 エンコード済みの SOAP XML シリアル化を制御する方法については、「[エンコード済み SOAP シリアル化を制御する属性](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md)」を参照してください。  
  
## 参照  
 [XML シリアル化および SOAP シリアル化](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)   
 [属性を使用した XML シリアル化の制御](../../../docs/framework/serialization/controlling-xml-serialization-using-attributes.md)   
 [方法 : XML ストリームの代替要素名を指定する](../../../docs/framework/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)   
 [方法 : オブジェクトをシリアル化する](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [方法 : オブジェクトを逆シリアル化する](../../../docs/framework/serialization/how-to-deserialize-an-object.md)