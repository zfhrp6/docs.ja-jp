---
title: "方法 : オブジェクトをシリアル化する | Microsoft Docs"
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
  - "オブジェクト, シリアル化の手順"
  - "オブジェクトのシリアル化"
ms.assetid: a1207d05-32b2-4953-8582-959607991227
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 方法 : オブジェクトをシリアル化する
オブジェクトをシリアル化するには、まず、シリアル化の対象となるオブジェクトを作成し、パブリック プロパティとパブリック フィールドを設定します。この処理を行うには、転送形式、つまり XML ストリームをストリームとファイルのいずれとして格納するかを決定する必要があります。たとえば、XML ストリームを永続的な形式で保存する必要がある場合は、[FileStream](frlrfSystemIOFileStreamClassTopic) オブジェクトを作成します。  
  
> [!NOTE]
>  XML シリアル化の例については、「[XML シリアル化の例](../../../docs/framework/serialization/examples-of-xml-serialization.md)」を参照してください。  
  
### オブジェクトをシリアル化するには  
  
1.  オブジェクトを作成し、パブリック フィールドとパブリック プロパティを設定します。  
  
2.  そのオブジェクトの型を使用して、<xref:System.Xml.Serialization.XmlSerializer> を構築します。詳細については、<xref:System.Xml.Serialization.XmlSerializer> クラスのコンストラクターを参照してください。  
  
3.  <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> メソッドを呼び出して、オブジェクトのパブリック プロパティとパブリック フィールドを XML ストリーム形式またはファイル形式のいずれかで生成します。ファイルを作成する例を次に示します。  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new   
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## 参照  
 [XML シリアル化の概要](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [方法 : オブジェクトを逆シリアル化する](../../../docs/framework/serialization/how-to-deserialize-an-object.md)