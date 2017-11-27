---
title: "方法 : オブジェクトを逆シリアル化する"
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
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b28d80951cb2d71f8f8fb532710f738fecdf8508
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-deserialize-an-object"></a>方法 : オブジェクトを逆シリアル化する
オブジェクトを逆シリアル化する場合、転送形式によって、ストリーム オブジェクトとファイル オブジェクトのどちらを作成するかが決定されます。 転送形式を決定したら、必要に応じて <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> メソッドまたは <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> メソッドを呼び出すことができます。  
  
### <a name="to-deserialize-an-object"></a>オブジェクトを逆シリアル化するには  
  
1.  逆シリアル化するオブジェクトの型を使用して、<xref:System.Xml.Serialization.XmlSerializer> を構築します。  
  
2.  <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> メソッドを呼び出して、オブジェクトのレプリカを生成します。 逆シリアル化を行う際には、次の例に示すように、返されたオブジェクトを元の型にキャストする必要があります。この例では、オブジェクトをファイルに逆シリアル化しています (ストリームに逆シリアル化することもできます)。  
  
    ```vb  
    Dim myObject As MySerializableClass  
    ' Construct an instance of the XmlSerializer with the type  
    ' of object that is being deserialized.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To read the file, create a FileStream.  
    Dim myFileStream As FileStream = _  
    New FileStream("myFileName.xml", FileMode.Open)  
    ' Call the Deserialize method and cast to the object type.  
    myObject = CType( _  
    mySerializer.Deserialize(myFileStream), MySerializableClass)  
    ```  
  
    ```csharp  
    MySerializableClass myObject;  
    // Construct an instance of the XmlSerializer with the type  
    // of object that is being deserialized.  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(MySerializableClass));  
    // To read the file, create a FileStream.  
    FileStream myFileStream =   
    new FileStream("myFileName.xml", FileMode.Open);  
    // Call the Deserialize method and cast to the object type.  
    myObject = (MySerializableClass)   
    mySerializer.Deserialize(myFileStream)  
    ```  
  
## <a name="see-also"></a>関連項目  
 [XML シリアル化の概要](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [方法 : オブジェクトをシリアル化する](../../../docs/standard/serialization/how-to-serialize-an-object.md)
