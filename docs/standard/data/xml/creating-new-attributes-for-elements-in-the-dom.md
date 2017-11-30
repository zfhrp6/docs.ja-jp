---
title: "DOM の要素に対する新しい属性の作成"
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
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6970ffc38e900c9b47c58c8ae4b81b9551f5589b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a>DOM の要素に対する新しい属性の作成
新しい属性を作成するとは異なる属性、ノードではありませんが、要素ノードのプロパティし、に含まれるために、他のノード型の作成、 **XmlAttributeCollection**要素に関連付けられています。 属性を作成して要素に追加するには、次の 2 つの方法があります。  
  
-   要素ノードを取得しを使用して**SetAttribute**その要素の属性コレクションに属性を追加します。  
  
-   作成、 **XmlAttribute**ノードを使用して、 **CreateAttribute**メソッドは、要素ノードを取得しを使用して**SetAttributeNode**ノードをその属性のコレクションに追加するには要素。  
  
 次の例を使用して、要素に属性を追加する方法を示しています、 **SetAttribute**メソッドです。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
public class Sample  
  
  public shared sub Main()  
  
  Dim doc as XmlDocument = new XmlDocument()  
  doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _  
              "<title>Pride And Prejudice</title>" & _  
              "</book>")  
  Dim root as XmlElement = doc.DocumentElement  
  
  'Add a new attribute.  
  root.SetAttribute("genre", "urn:samples", "novel")  
  
  Console.WriteLine("Display the modified XML...")  
  Console.WriteLine(doc.InnerXml)  
  
  end sub  
end class  
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
    doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +  
                "<title>Pride And Prejudice</title>" +  
                "</book>");  
    XmlElement root = doc.DocumentElement;  
  
    // Add a new attribute.  
    root.SetAttribute("genre", "urn:samples", "novel");  
  
    Console.WriteLine("Display the modified XML...");  
    Console.WriteLine(doc.InnerXml);  
  }  
```  
  
 次の例は、新しい属性を使用して作成する、 **CreateAttribute**メソッドです。 属性の属性コレクションに追加し、表示、 **book**要素を使用して、 **SetAttributeNode**メソッドです。  
  
 次の XML を使用します。  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 新しい属性を作成し、その属性の値を設定します。  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 作成した属性を要素に追加します。  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 **出力**  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 完全なコード サンプルはあります<xref:System.Xml.XmlDocument.CreateAttribute%2A>です。  
  
 作成することも、 **XmlAttribute**ノードと使用、 **InsertBefore**または**InsertAfter**コレクション内の適切な位置に配置する方法です。 同じ名前を持つ属性が既に既存の属性のコレクションである場合**XmlAttribute**からコレクションと新しいノードが削除された**XmlAttribute**ノードを挿入します。 同じように実行して、 **SetAttribute**メソッドです。 既存のノードを行うには参照ポイントとして、パラメーターとして、これらのメソッドを使用、 **InsertBefore**と**InsertAfter**です。 新しいノードでの既定値を挿入する位置を示す参照ノードを指定しない場合、 **InsertAfter**メソッドは、コレクションの先頭に新しいノードを挿入します。 既定の位置、 **InsertBefore**参照ノードが指定されていない場合、コレクションの末尾です。  
  
 作成した場合、 **XmlNamedNodeMap**属性の名前を使用して属性を追加することができます、<xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>です。 詳細については、次を参照してください。 [NamedNodeMaps と NodeLists のノード コレクション](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)です。  
  
## <a name="default-attributes"></a>既定の属性  
 既定の属性を持つと宣言された要素を作成すると、既定値を持つ新しい既定の属性が XML ドキュメント オブジェクト モデル (DOM) によって作成され、その要素に割り当てられます。 既定の属性の子ノードも同時に作成されます。  
  
## <a name="attribute-child-nodes"></a>属性の子ノード  
 属性ノードの値は、その属性の子ノードになります。 有効な子ノードの 2 つの種類があります: **XmlText**ノード、および**XmlEntityReference**ノード。 これらは、という意味で子ノードなどのメソッド**FirstChild**と**LastChild**子ノードとして処理します。 属性が子ノードを持つという点は、属性または属性の子ノードを削除するときに重要になります。 詳細については、次を参照してください。 [DOM の要素ノードからの属性の削除](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md)です。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
