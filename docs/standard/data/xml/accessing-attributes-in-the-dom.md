---
title: "DOM の属性へのアクセス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a433ec5f83a50aa4fe4b2017a0dac3d2a5e5710c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-attributes-in-the-dom"></a>DOM の属性へのアクセス
属性は要素のプロパティであり、要素の子ではありません。 この区別は、XML ドキュメント オブジェクト モデル (DOM) の兄弟ノード、親ノード、および子ノードの間の移動に使用するメソッドで重要な意味を持ちます。 たとえば、 **PreviousSibling**と**NextSibling**属性または属性の間の要素から移動する方法は使用されません。 代わりに、属性、要素のプロパティと要素が所有するが、 **OwnerElement**プロパティおよび not、 **parentNode**プロパティ、およびナビゲーションの個別の方法があります。  
  
 現在のノードが要素を使用して、 **HasAttribute**メソッドを要素に関連付けられた任意の属性があるかどうかを参照してください。 要素に属性がある場合は、各種のメソッドで属性にアクセスできます。 要素の 1 つの属性を取得する際、 **GetAttribute**と**GetAttributeNode**のメソッド、 **XmlElement**またはすべての属性を取得します。コレクション。 コレクションに対して反復処理を行う必要がある場合は、コレクションを取得すると便利です。 要素からすべての属性にする場合は、使用、**属性**コレクション内のすべての属性を取得する要素のプロパティです。  
  
## <a name="retrieving-all-attributes-into-a-collection"></a>コレクションへのすべての属性の取得  
 コレクションにすべての属性、要素ノードの場合、 **XmlElement.Attributes**プロパティです。 これを取得、 **XmlAttributeCollection**要素のすべての属性を格納しています。 **XmlAttributeCollection**クラスから継承、 **XmlNamedNode**マップします。 したがって、メソッドとプロパティ コレクションで使用できるでも含まれます、名前付きノード マップで使用できるメソッドとプロパティを特定する、 **XmlAttributeCollection**クラスなど、 **ItemOf**プロパティまたは**Append**メソッドです。 属性のコレクション内の各項目を表す、 **XmlAttribute**ノード。 要素に属性の数を検索、取得、 **XmlAttributeCollection**、使用して、**カウント**プロパティを確認して数**XmlAttribute**コレクション内のノードには。  
  
 次のコード例は、属性を取得する方法を示しています。 コレクションと、を使用して、**カウント**上に反復処理するメソッドをループのインデックス。 このコードは、その後、コレクションから属性を 1 つ取得して、その値を表示します。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.   
        Dim myElement As XmlElement = doc.DocumentElement  
  
        ' Create an attribute collection from the element.  
        Dim attrColl As XmlAttributeCollection = myElement.Attributes  
  
        ' Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...")  
        Dim i As Integer  
        For i = 0 To attrColl.Count - 1  
            Console.Write("{0} = ", attrColl.ItemOf(i).Name)  
            Console.Write("{0}", attrColl.ItemOf(i).Value)  
            Console.WriteLine()  
        Next  
  
        ' Retrieve a single attribute from the collection; specifically, the  
        ' attribute with the name "misc".  
        Dim attr As XmlAttribute = attrColl("misc")  
  
        ' Retrieve the value from that attribute.  
        Dim miscValue As String = attr.InnerXml  
  
        Console.WriteLine("Display the attribute information.")  
        Console.WriteLine(miscValue)  
  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  
    public static void Main()  
    {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" +  
                      "<title>The Handmaid's Tale</title>" +  
                      "<price>14.95</price>" +  
                      "</book>");  
  
        // Move to an element.  
        XmlElement myElement = doc.DocumentElement;  
  
        // Create an attribute collection from the element.  
        XmlAttributeCollection attrColl = myElement.Attributes;  
  
        // Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...");  
        for (int i = 0; i < attrColl.Count; i++)  
        {  
            Console.Write("{0} = ", attrColl[i].Name);  
            Console.Write("{0}", attrColl[i].Value);  
            Console.WriteLine();  
        }  
  
        // Retrieve a single attribute from the collection; specifically, the  
        // attribute with the name "misc".  
        XmlAttribute attr = attrColl["misc"];  
  
        // Retrieve the value from that attribute.  
        String miscValue = attr.InnerXml;  
  
        Console.WriteLine("Display the attribute information.");  
        Console.WriteLine(miscValue);  
  
    }  
}  
```  
  
 この例を実行すると、次の出力が表示されます。  
  
 **出力**  
  
 コレクション内のすべての属性を表示します。  
  
```  
genre = novel  
ISBN = 1-861001-57-5  
misc = sale item  
Display the attribute information.  
sale item  
```  
  
 属性コレクションの情報は、名前またはインデックス番号によって取得できます。 上の例では、名前を指定してデータを取得しています。 次の例では、インデックス番号を指定してデータを取得します。  
  
 **XmlAttributeCollection**反復処理できるし、は、コレクションの名前またはインデックスを使ってこの例では 0 から始まるインデックスを使用して、次のファイルを使用してコレクションの最初の属性を選択して**baseuri.xml**の入力として、します。  
  
### <a name="input"></a>入力  
  
```xml  
<!-- XML fragment -->  
<book genre="novel">  
  <title>Pride And Prejudice</title>  
</book>  
```  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.Load("http://localhost/baseuri.xml")  
  
        ' Display information on the attribute node. The value  
        ' returned for BaseURI is 'http://localhost/baseuri.xml'.  
        Dim attr As XmlAttribute = doc.DocumentElement.Attributes(0)  
        Console.WriteLine("Name of the attribute:  {0}", attr.Name)  
        Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI)  
        Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText)  
    End Sub 'Main   
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  public static void Main()  
  {  
    // Create the XmlDocument.  
    XmlDocument doc = new XmlDocument();  
  
    doc.Load("http://localhost/baseuri.xml");  
  
    // Display information on the attribute node. The value  
    // returned for BaseURI is 'http://localhost/baseuri.xml'.  
    XmlAttribute attr = doc.DocumentElement.Attributes[0];  
    Console.WriteLine("Name of the attribute:  {0}", attr.Name);  
    Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI);  
    Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText);  
  }  
}  
```  
  
## <a name="retrieving-an-individual-attribute-node"></a>個別の属性ノードの取得  
 要素から属性ノードを 1 つ取得するには、<xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> メソッドを使用します。 型のオブジェクトを返します**XmlAttribute**です。 作成したら、 **XmlAttribute**、すべてのメソッドとプロパティで使用できる、<xref:System.Xml.XmlAttribute?displayProperty=nameWithType>クラスを検索するなど、そのオブジェクトで使用可能な**OwnerElement**です。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.  
        Dim root As XmlElement  
        root = doc.DocumentElement  
  
        ' Get an attribute.  
        Dim attr As XmlAttribute  
        attr = root.GetAttributeNode("ISBN")  
  
        ' Display the value of the attribute.  
        Dim attrValue As String  
        attrValue = attr.InnerXml  
        Console.WriteLine(attrValue)  
  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
 public class Sample  
 {  
      public static void Main()  
      {  
    XmlDocument doc = new XmlDocument();  
     doc.LoadXml("<book genre='novel' ISBN='1-861003-78' misc='sale item'>" +  
                   "<title>The Handmaid's Tale</title>" +  
                   "<price>14.95</price>" +  
                   "</book>");   
  
    // Move to an element.  
     XmlElement root = doc.DocumentElement;  
  
    // Get an attribute.  
     XmlAttribute attr = root.GetAttributeNode("ISBN");  
  
    // Display the value of the attribute.  
     String attrValue = attr.InnerXml;  
     Console.WriteLine(attrValue);  
  
    }  
}  
```  
  
 前の例で示したように、属性コレクションから 1 つの属性ノードを取得することもできます。 次のコード例を示します 1 行のコードを書き込む 1 つの属性を取得するインデックス番号によって、XML ドキュメントのルートからツリーとも呼ばれる、 **DocumentElement**プロパティです。  
  
```  
XmlAttribute attr = doc.DocumentElement.Attributes[0];  
```  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
