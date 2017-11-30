---
title: "方法 : オブジェクトをシリアル化する"
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
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 76b6006c34b29e17ea725a5f7d104c1b085b5edc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="8c83e-102">方法 : オブジェクトをシリアル化する</span><span class="sxs-lookup"><span data-stu-id="8c83e-102">How to: Serialize an Object</span></span>
<span data-ttu-id="8c83e-103">オブジェクトをシリアル化するには、まず、シリアル化の対象となるオブジェクトを作成し、パブリック プロパティとパブリック フィールドを設定します。</span><span class="sxs-lookup"><span data-stu-id="8c83e-103">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="8c83e-104">この処理を行うには、転送形式、つまり XML ストリームをストリームとファイルのいずれとして格納するかを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c83e-104">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="8c83e-105">たとえば、XML ストリームを永続的な形式で保存する必要がある場合は、<xref:System.IO.FileStream> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8c83e-105">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c83e-106">XML シリアル化の例については、「[Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c83e-106">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="8c83e-107">オブジェクトをシリアル化するには</span><span class="sxs-lookup"><span data-stu-id="8c83e-107">To serialize an object</span></span>  
  
1.  <span data-ttu-id="8c83e-108">オブジェクトを作成し、パブリック フィールドとパブリック プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="8c83e-108">Create the object and set its public fields and properties.</span></span>  
  
2.  <span data-ttu-id="8c83e-109">そのオブジェクトの型を使用して、<xref:System.Xml.Serialization.XmlSerializer> を構築します。</span><span class="sxs-lookup"><span data-stu-id="8c83e-109">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="8c83e-110">詳細については、<xref:System.Xml.Serialization.XmlSerializer> クラスのコンストラクターを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c83e-110">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3.  <span data-ttu-id="8c83e-111"><xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> メソッドを呼び出して、オブジェクトのパブリック プロパティとパブリック フィールドを XML ストリーム形式またはファイル形式のいずれかで生成します。</span><span class="sxs-lookup"><span data-stu-id="8c83e-111">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="8c83e-112">ファイルを作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8c83e-112">The following example creates a file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8c83e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c83e-113">See Also</span></span>  
 [<span data-ttu-id="8c83e-114">XML シリアル化の概要</span><span class="sxs-lookup"><span data-stu-id="8c83e-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="8c83e-115">方法 : オブジェクトを逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="8c83e-115">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
