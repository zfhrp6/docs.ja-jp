---
title: "インデックスによる順序付けられたノードの取得"
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
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 13d3077b1536d4e96cb9e4f1f09313dd793a906e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ordered-node-retrieval-by-index"></a>インデックスによる順序付けられたノードの取得
World Wide Web Consortium (W3C) XML ドキュメント オブジェクト モデル (DOM) nodelist も、によって処理される順序なしのセットではなく、ノードの順序付きリストを処理することのできる、 **XmlNamedNodeMap**です。 Microsoft .NET Framework の NodeList が呼び出された**XmlNodeList**です。 メソッドとプロパティを返す、 **XmlNodeList**は。  
  
-   XmlNode.ChildNodes  
  
-   XmlDocument.GetElementsByTagName  
  
-   XmlElement.GetElementsByTagName  
  
-   XmlNode.SelectNodes  
  
 **XmlNodeList**が、**カウント**内のノードを反復処理するループを記述するために使用できるプロパティ、 **XmlNodeList**次のコード例のように。  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
   doc.Load("books.xml")  
  
    ' Retrieve all book titles.  
    Dim root as XmlElement = doc.DocumentElement  
    Dim elemList as XmlNodeList = root.GetElementsByTagName("title")  
    Dim i as integer  
    for i=0  to elemList.Count-1  
        ' Display all book titles in the Node List.  
        Console.WriteLine(elemList.ItemOf(i).InnerXml)  
    next  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
// Retrieve all book titles.  
XmlElement root = doc.DocumentElement;  
XmlNodeList elemList = root.GetElementsByTagName("title");  
for (int i=0; i < elemList.Count; i++)  
{     
   // Display all book titles in the Node List.  
   Console.WriteLine(elemList[i].InnerXml);  
}   
```  
  
 加え、**カウント**プロパティがある、 **GetEnumerator**メソッドを提供する、`foreach`スタイルの反復処理内のノードのコレクションを**XmlNodeList**. `foreach` ステートメントの使用方法を次のコード サンプルに示します。  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("books.xml")  
  
' Get book titles.  
Dim root As XmlElement = doc.DocumentElement  
Dim elemList As XmlNodeList = root.GetElementsByTagName("title")  
Dim ienum As IEnumerator = elemList.GetEnumerator()  
' Loop over the XmlNodeList using the enumerator ienum          
While ienum.MoveNext()  
    ' Display the book title.  
    Dim title As XmlNode = CType(ienum.Current, XmlNode)  
    Console.WriteLine(title.InnerText)  
End While  
```  
  
```csharp  
{  
     XmlDocument doc = new XmlDocument();  
     doc.Load("books.xml");  
  
     // Get book titles.  
     XmlElement root = doc.DocumentElement;  
     XmlNodeList elemList = root.GetElementsByTagName("title");  
     IEnumerator ienum = elemList.GetEnumerator();    
     // Loop over the XmlNodeList using the enumerator ienum          
     while (ienum.MoveNext())  
     {  
          // Display the book title.  
           XmlNode title = (XmlNode) ienum.Current;  
           Console.WriteLine(title.InnerText);  
     }  
  }  
```  
  
 詳細については、メソッドとプロパティで使用できる、 **XmlNodeList**を参照してください<xref:System.Xml.XmlNodeList>です。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
