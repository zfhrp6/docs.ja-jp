---
title: "方法 : オブジェクトを SOAP エンコード済み XML ストリームとしてシリアル化する | Microsoft Docs"
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
  - "シリアル化, SOAP"
  - "SOAP, XML シリアル化"
  - "XML シリアル化, SOAP"
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 方法 : オブジェクトを SOAP エンコード済み XML ストリームとしてシリアル化する
[コード例](#cpconxmlserializationusingsoapprotocolanchor1)  
  
 SOAP メッセージは XML を使用して作成されるため、[XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx) を使用してクラスをシリアル化し、エンコード済みの SOAP メッセージを生成できます。生成される XML は、W3C \(World Wide Web Consortium\) \(www.w3.org\) のドキュメント『Simple Object Access Protocol \(SOAP\) 1.1』のセクション 5 に準拠します。SOAP メッセージを使用して通信を行う XML Web サービスを作成する場合、特殊な SOAP 属性のセットをクラスやクラスのメンバーに適用することで、生成される XML ストリームをカスタマイズできます。属性の一覧については、「[エンコード済み SOAP シリアル化を制御する属性](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md)」を参照してください。  
  
### オブジェクトを SOAP エンコード済み XML ストリームとしてシリアル化するには  
  
1.  [XML スキーマ定義ツール \(Xsd.exe\)](../../../docs/framework/serialization/xml-schema-definition-tool-xsd-exe.md) を使用して、クラスを作成します。  
  
2.  **System.Xml.Serialization** の特別な属性を 1 つ以上適用します。「エンコード済み SOAP シリアル化を制御する属性」の一覧を参照してください。  
  
3.  新しい **SoapReflectionImporter** を作成し、シリアル化されるクラスの型を使用して **ImportTypeMapping** メソッドを呼び出して、**XmlTypeMapping** を作成します。  
  
     **SoapReflectionImporter** クラスの **ImportTypeMapping** メソッドを呼び出して **XmlTypeMapping** を作成するコード例を次に示します。  
  
    ```vb  
    ' Serializes a class named Group as a SOAP message.  
    Dim myTypeMapping As XmlTypeMapping = (New SoapReflectionImporter(). _  
    ImportTypeMapping(GetType(Group))  
  
    ```  
  
    ```csharp  
    // Serializes a class named Group as a SOAP message.  
    XmlTypeMapping myTypeMapping = (new SoapReflectionImporter().  
    ImportTypeMapping(typeof(Group));  
    ```  
  
4.  **XmlTypeMapping** を <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> コンストラクターに渡して、**XmlSerializer** クラスのインスタンスを作成します。  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5.  **Serialize** メソッドまたは **Deserialize** メソッドを呼び出します。  
  
## 使用例  
  
```vb  
' Serializes a class named Group as a SOAP message.  
Dim myTypeMapping As XmlTypeMapping = (New SoapReflectionImporter(). _  
ImportTypeMapping(GetType(Group))  
Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
  
```  
  
```csharp  
// Serializes a class named Group as a SOAP message.  
XmlTypeMapping myTypeMapping = (new SoapReflectionImporter().ImportTypeMapping(typeof(Group));  
XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
```  
  
## 参照  
 [XML シリアル化および SOAP シリアル化](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [エンコード済み SOAP シリアル化を制御する属性](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md)   
 [XML Web サービスを使用した XML シリアル化](../../../docs/framework/serialization/xml-serialization-with-xml-web-services.md)   
 [方法 : オブジェクトをシリアル化する](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [方法 : オブジェクトを逆シリアル化する](../../../docs/framework/serialization/how-to-deserialize-an-object.md)   
 [方法 : SOAP エンコード済み XML シリアル化をオーバーライドする](../../../docs/framework/serialization/how-to-override-encoded-soap-xml-serialization.md)