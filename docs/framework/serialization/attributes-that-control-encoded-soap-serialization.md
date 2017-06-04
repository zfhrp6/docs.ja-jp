---
title: "エンコード済み SOAP シリアル化を制御する属性 | Microsoft Docs"
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
  - "シリアル化, 属性"
  - "SOAP, XML シリアル化"
  - "XML シリアル化, 属性"
  - "XML シリアル化, SOAP"
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# エンコード済み SOAP シリアル化を制御する属性
W3C \(World Wide Web Consortium\) \(www.w3.org\) のドキュメント『Simple Object Access Protocol \(SOAP\) 1.1』には、SOAP パラメーターのエンコード方法について説明したオプションのセクション \(セクション 5\) が含まれています。このセクション 5 の仕様に準拠するには、[System.Xml.Serialization](frlrfSystemXmlSerialization) 名前空間で指定されている特殊な属性のセットを使用する必要があります。これらの属性をクラスやクラスのメンバーに適宜適用し、[XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx) を使用して、クラスのインスタンスをシリアル化します。  
  
 これらの属性、およびその適用対象と機能を次の表に示します。これらの属性を使用して XML シリアル化を制御する方法の詳細については、「[方法 : オブジェクトを SOAP エンコード済み XML ストリームとしてシリアル化する](../../../docs/framework/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)」および「[方法 : SOAP エンコード済み XML シリアル化をオーバーライドする](../../../docs/framework/serialization/how-to-override-encoded-soap-xml-serialization.md)」を参照してください。  
  
 属性の詳細については、「[属性](../../../docs/standard/attributes/index.md)」を参照してください。  
  
|属性|対象|機能|  
|--------|--------|--------|  
|[SoapAttributeAttribute](frlrfSystemXmlSerializationSoapAttributeAttributeClassTopic)|パブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|クラス メンバーを XML 属性としてシリアル化します。|  
|[SoapElementAttribute](frlrfSystemXmlSerializationSoapElementAttributeClassTopic)|パブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|クラスを XML 要素としてシリアル化します。|  
|[SoapEnumAttribute](frlrfSystemXmlSerializationSoapEnumAttributeClassTopic)|列挙体識別子であるパブリック フィールド|列挙体のメンバーの要素名を指定します。|  
|[SoapIgnoreAttribute](frlrfSystemXmlSerializationSoapIgnoreAttributeClassTopic)|パブリック プロパティとパブリック フィールド|クラスのシリアル化時に、そのクラスに含まれているプロパティまたはフィールドを無視します。|  
|[SoapIncludeAttribute](frlrfSystemXmlSerializationSoapIncludeAttributeClassTopic)|パブリック派生クラス宣言、およびパブリック メソッド \(Web サービス記述言語 \(WSDL: Web Service Description Language\) ドキュメント用\)|シリアル化時に認識されるように、スキーマの生成時にその型を対象に含めます。|  
|[SoapTypeAttribute](frlrfSystemXmlSerializationSoapTypeAttributeClassTopic)|パブリック クラス宣言|クラスを XML 型としてシリアル化します。|  
  
## 参照  
 [XML シリアル化および SOAP シリアル化](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [方法 : オブジェクトを SOAP エンコード済み XML ストリームとしてシリアル化する](../../../docs/framework/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)   
 [方法 : SOAP エンコード済み XML シリアル化をオーバーライドする](../../../docs/framework/serialization/how-to-override-encoded-soap-xml-serialization.md)   
 [属性](../../../docs/standard/attributes/index.md)   
 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)   
 [方法 : オブジェクトをシリアル化する](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [方法 : オブジェクトを逆シリアル化する](../../../docs/framework/serialization/how-to-deserialize-an-object.md)