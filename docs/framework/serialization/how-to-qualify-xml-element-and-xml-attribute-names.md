---
title: "方法 : XML 要素および XML 属性名を修飾する | Microsoft Docs"
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
  - "XML 要素の修飾"
  - "XML 名の修飾"
  - "XML 名前空間, 要素と名前の修飾"
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 方法 : XML 要素および XML 属性名を修飾する
[コード例](#cpconworkingwithxmlnamespacesanchor1)  
  
 [XmlSerializerNamespaces](frlrfSystemXmlSerializationXmlSerializerNamespacesClassTopic) クラスのインスタンスに格納される XML 名前空間は、W3C \(World Wide Web Consortium\) \(www.w3.org\) の仕様『Namespaces in XML』に準拠する必要があります。  
  
 XML 名前空間を使用すると、XML ドキュメント内の XML 要素および XML 属性の名前を修飾できます。修飾名は、プレフィックスとローカル名がコロンで区切られた構成になっています。プレフィックスはプレースホルダーとしてのみ機能し、名前空間を指定する URI に割り当てられます。汎用的に管理される URI 名前空間とローカル名を組み合わせることにより、生成される名前は、必ず汎用的に一意になります。  
  
 **XmlSerializerNamespaces** のインスタンスを作成し、そのオブジェクトに名前空間のペアを追加することで、XML ドキュメントで使用されるプレフィックスを指定できます。  
  
### XML ドキュメントにおける修飾名を作成するには  
  
1.  **XmlSerializerNamespaces** クラスのインスタンスを作成します。  
  
2.  すべてのプレフィックスと名前空間のペアを **XmlSerializerNamespaces** に追加します。  
  
3.  [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx) が XML ドキュメントにシリアル化する各メンバーやクラスに、適切な **System.Xml.Serialization** 属性を適用します。  
  
     適用できる属性は、[XmlAnyElementAttribute](frlrfSystemXmlSerializationXmlAnyElementAttributeClassTopic)、[XmlArrayAttribute](frlrfSystemXmlSerializationXmlArrayAttributeClassTopic)、[XmlArrayItemAttribute](frlrfSystemXmlSerializationXmlArrayItemAttributeClassTopic)、[XmlAttributeAttribute](frlrfSystemXmlSerializationXmlAttributeAttributeClassTopic)、[XmlElementAttribute](frlrfSystemXmlSerializationXmlElementAttributeClassTopic)、[XmlRootAttribute](frlrfSystemXmlSerializationXmlRootAttributeClassTopic)、および [XmlTypeAttribute](frlrfSystemXmlSerializationXmlTypeAttributeClassTopic) です。  
  
4.  各属性の **Namespace** プロパティを、**XmlSerializerNamespaces** のいずれかの名前空間値に設定します。  
  
5.  **XmlSerializerNamespaces** を **XmlSerializer** の **Serialize** メソッドに渡します。  
  
## 使用例  
 **XmlSerializerNamespaces** を作成し、このオブジェクトにプレフィックスと名前空間のペアを 2 つ追加する例を次に示します。このコードでは、`Books` クラスのインスタンスをシリアル化するために使用される **XmlSerializer** を作成します。また、**XmlSerializerNamespaces** を使用して **Serialize** メソッドを呼び出し、XML にプレフィックス付き名前空間を含めることができるようにします。  
  
```vb  
Option Explicit   
public class Price  
{  
    [XmlAttribute(Namespace = "http://www.cpandl.com")]  
    public string currency;  
    [XmlElement(Namespace = "http://www.cohowinery.com")]  
    public decimal price;  
}  
  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Serialization  
  
Public Class Run  
  
    Public Shared Sub Main()  
        Dim test As New Run()  
        test.SerializeObject("XmlNamespaces.xml")  
    End Sub 'Main  
  
    Public Sub SerializeObject(filename As String)  
        Dim mySerializer As New XmlSerializer(GetType(Books))  
        ' Writing a file requires a TextWriter.  
        Dim myWriter As New StreamWriter(filename)  
  
        ' Creates an XmlSerializerNamespaces and adds two  
        ' prefix-namespace pairs.   
        Dim myNamespaces As New XmlSerializerNamespaces()  
        myNamespaces.Add("books", "http://www.cpandl.com")  
        myNamespaces.Add("money", "http://www.cohowinery.com")  
  
        ' Creates a Book.  
        Dim myBook As New Book()  
        myBook.TITLE = "A Book Title"  
        Dim myPrice As New Price()  
        myPrice.price = CDec(9.95)  
        myPrice.currency = "US Dollar"  
        myBook.PRICE = myPrice  
        Dim myBooks As New Books()  
        myBooks.Book = myBook  
        mySerializer.Serialize(myWriter, myBooks, myNamespaces)  
        myWriter.Close()  
    End Sub  
End Class  
  
Public Class Books  
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _  
    Public Book As Book  
End Class 'Books  
  
<XmlType([Namespace] := "http://www.cpandl.com")> _  
Public Class Book  
  
    <XmlElement([Namespace] := "http://www.cpandl.com")> _  
    Public TITLE As String  
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _  
    Public PRICE As Price  
End Class  
  
Public Class Price  
    <XmlAttribute([Namespace] := "http://www.cpandl.com")> _  
    Public currency As String  
    Public <XmlElement([Namespace] := "http://www.cohowinery.com")> _  
        price As Decimal  
End Class  
  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Serialization;  
  
public class Run  
{  
    public static void Main()  
    {  
        Run test = new Run();  
        test.SerializeObject("XmlNamespaces.xml");  
    }  
    public void SerializeObject(string filename)  
    {  
        XmlSerializer mySerializer = new XmlSerializer(typeof(Books));  
        // Writing a file requires a TextWriter.  
        TextWriter myWriter = new StreamWriter(filename);  
  
        // Creates an XmlSerializerNamespaces and adds two  
        // prefix-namespace pairs.  
        XmlSerializerNamespaces myNamespaces =   
        new XmlSerializerNamespaces();  
        myNamespaces.Add("books", "http://www.cpandl.com");  
        myNamespaces.Add("money", "http://www.cohowinery.com");  
  
        // Creates a Book.  
        Book myBook = new Book();  
        myBook.TITLE = "A Book Title";  
        Price myPrice = new Price();  
        myPrice.price = (decimal) 9.95;  
        myPrice.currency = "US Dollar";  
        myBook.PRICE = myPrice;  
        Books myBooks = new Books();  
        myBooks.Book = myBook;  
        mySerializer.Serialize(myWriter,myBooks,myNamespaces);  
        myWriter.Close();  
    }  
}  
  
public class Books  
{  
    [XmlElement(Namespace = "http://www.cohowinery.com")]  
    public Book Book;  
}  
  
[XmlType(Namespace ="http://www.cpandl.com")]  
public class Book  
{  
    [XmlElement(Namespace = "http://www.cpandl.com")]  
    public string TITLE;  
    [XmlElement(Namespace ="http://www.cohowinery.com")]  
    public Price PRICE;  
}  
```  
  
## 参照  
 [XML スキーマ定義ツールと XML シリアル化](../../../docs/framework/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)   
 [XML シリアル化の概要](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [XmlSerializer Class](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)   
 [XML シリアル化を制御する属性](../../../docs/framework/serialization/attributes-that-control-xml-serialization.md)   
 [XmlSerializerNamespaces Class](frlrfSystemXmlSerializationXmlSerializerNamespacesClassTopic)   
 [方法 : XML ストリームの代替要素名を指定する](../../../docs/framework/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)   
 [方法 : オブジェクトをシリアル化する](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [方法 : オブジェクトを逆シリアル化する](../../../docs/framework/serialization/how-to-deserialize-an-object.md)