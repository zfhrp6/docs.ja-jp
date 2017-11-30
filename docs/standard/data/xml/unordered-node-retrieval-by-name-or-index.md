---
title: "名前またはインデックスによる順序付けられていないノードの取得"
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
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a8bea8f373dced08fd7a2a828255a593533df9d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="unordered-node-retrieval-by-name-or-index"></a><span data-ttu-id="e67d8-102">名前またはインデックスによる順序付けられていないノードの取得</span><span class="sxs-lookup"><span data-stu-id="e67d8-102">Unordered Node Retrieval by Name or Index</span></span>
<span data-ttu-id="e67d8-103">**XmlNamedNodeMap** NamedNodeMap として、World Wide Web Consortium (W3C) 仕様に記載されて、ノードを参照することで、名前またはインデックスでノードの順序なしのセットを処理するために必要です。</span><span class="sxs-lookup"><span data-stu-id="e67d8-103">The **XmlNamedNodeMap** is described in the World Wide Web Consortium (W3C) specification as the NamedNodeMap and is required to handle an unordered set of nodes with the ability to reference nodes by their name or index.</span></span> <span data-ttu-id="e67d8-104">アクセスがある唯一の方法、 **XmlNamedNodeMap**場合は、 **XmlNamedNodeMap**メソッドまたはプロパティを介して返されます。</span><span class="sxs-lookup"><span data-stu-id="e67d8-104">The only way you have access to an **XmlNamedNodeMap** is when an **XmlNamedNodeMap** is returned through a method or property.</span></span> <span data-ttu-id="e67d8-105">次の 3 つのメソッドまたはプロパティを返すがある、 **XmlNamedNodeMap**:</span><span class="sxs-lookup"><span data-stu-id="e67d8-105">There are three methods or properties that return an **XmlNamedNodeMap**:</span></span>  
  
-   <span data-ttu-id="e67d8-106">XmlElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="e67d8-106">XmlElement.Attributes</span></span>  
  
-   <span data-ttu-id="e67d8-107">XmlDocumentType.Entities</span><span class="sxs-lookup"><span data-stu-id="e67d8-107">XmlDocumentType.Entities</span></span>  
  
-   <span data-ttu-id="e67d8-108">XmlDocumentType.Notations</span><span class="sxs-lookup"><span data-stu-id="e67d8-108">XmlDocumentType.Notations</span></span>  
  
 <span data-ttu-id="e67d8-109">たとえば、 **XmlDocumentType.Entities**プロパティのコレクションを取得する**XmlEntity**ノードがドキュメント型宣言で宣言します。</span><span class="sxs-lookup"><span data-stu-id="e67d8-109">For example, the **XmlDocumentType.Entities** property gets the collection of **XmlEntity** nodes declared in the document type declaration.</span></span> <span data-ttu-id="e67d8-110">としてこのコレクションが返されます、 **XmlNamedNodeMap**を使用してコレクションを反復処理できると、**カウント**プロパティと表示のエンティティの情報です。</span><span class="sxs-lookup"><span data-stu-id="e67d8-110">This collection is returned as an **XmlNamedNodeMap**, and you can iterate through the collection with the use of the **Count** property and display entity information.</span></span> <span data-ttu-id="e67d8-111">反復処理する例については、 **XmlNamedNodeMap**を参照してください<xref:System.Xml.XmlDocumentType.Entities%2A>です。</span><span class="sxs-lookup"><span data-stu-id="e67d8-111">For an example of iterating through an **XmlNamedNodeMap**, see <xref:System.Xml.XmlDocumentType.Entities%2A>.</span></span>  
  
 <span data-ttu-id="e67d8-112">**XmlAttributeCollection**から派生した**XmlNamedNodeMap**属性だけは変更できますが、記法とエンティティは読み取り専用とします。</span><span class="sxs-lookup"><span data-stu-id="e67d8-112">The **XmlAttributeCollection** is derived from **XmlNamedNodeMap** and only attributes are modifiable, while notations and entities are read-only.</span></span> <span data-ttu-id="e67d8-113">使用して、 **XmlNamedNodeMap**属性については、XML 名に基づいてこれらの属性のノードを取得できます。</span><span class="sxs-lookup"><span data-stu-id="e67d8-113">Using the **XmlNamedNodeMap** for the attributes, you can get nodes for those attributes based on their XML names.</span></span> <span data-ttu-id="e67d8-114">これは、要素ノードの属性コレクションを操作する簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="e67d8-114">This provides an easy method for manipulating the collection of attributes on an element node.</span></span> <span data-ttu-id="e67d8-115">これは、直接のと対照的できます**XmlNodeList**もを実装する、 **IEnumerable**インターフェイスが文字列ではなくインデックス アクセサー。</span><span class="sxs-lookup"><span data-stu-id="e67d8-115">This can be contrasted directly with **XmlNodeList**, which also implements the **IEnumerable** interface, but with an index accessor rather than a string.</span></span> <span data-ttu-id="e67d8-116">**RemoveNamedItem**と**SetNamedItem**に対してメソッドを使用するだけ、 **XmlAttributeCollection**です。</span><span class="sxs-lookup"><span data-stu-id="e67d8-116">The **RemoveNamedItem** and **SetNamedItem** methods are only used against an **XmlAttributeCollection**.</span></span> <span data-ttu-id="e67d8-117">追加またはを使用しているかどうか、属性コレクションから削除する、 **AttributeCollection**または**XmlNamedNodeMap**実装では、要素の属性コレクションを変更します。</span><span class="sxs-lookup"><span data-stu-id="e67d8-117">Adding or removing from an attribute collection, whether using the **AttributeCollection** or the **XmlNamedNodeMap** implementation, modifies the attribute collection on the element.</span></span> <span data-ttu-id="e67d8-118">属性を移動する方法と新しい属性を作成する方法を次のコード サンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="e67d8-118">The following code example shows how to move an attribute and create a new attribute.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
  
Class test  
  
    Public Shared Sub Main()  
        Dim doc As New XmlDocument()  
        doc.LoadXml("<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> ")  
  
        ' Get the attributes of node "child2 "  
        Dim ac As XmlAttributeCollection = doc.DocumentElement.ChildNodes(1).Attributes  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
        Dim i As Integer  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Get the 'attr1' from child1.  
        Dim attr As XmlAttribute = doc.DocumentElement.ChildNodes(0).Attributes(0)  
  
        ' Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem(attr)  
  
        ''attr1' will be removed from 'child1' and added to 'child2'.  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Create a new attribute and add to the collection.  
        Dim attr2 As XmlAttribute = doc.CreateAttribute("attr4")  
        attr2.Value = "val4"  
        ac.SetNamedItem(attr2)  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
    End Sub 'Main  
End Class 'test  
```  
  
```csharp  
using System;  
using System.Xml;  
class test {  
    public static void Main() {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml( "<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> " );  
  
        // Get the attributes of node "child2"  
        XmlAttributeCollection ac = doc.DocumentElement.ChildNodes[1].Attributes;  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );  
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Get the 'attr1' from child1.  
        XmlAttribute attr = doc.DocumentElement.ChildNodes[0].Attributes[0];  
  
        // Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem( attr );  
  
        // 'attr1' will be removed from 'child1' and added to 'child2'.  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Create a new attribute and add to the collection.  
        XmlAttribute attr2 = doc.CreateAttribute( "attr4" );  
        attr2.Value = "val4";  
        ac.SetNamedItem( attr2 );  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );           
  
    }  
}  
```  
  
 <span data-ttu-id="e67d8-119">削除されている属性を表示する追加のコード例を参照する、 **AttributeCollection**を参照してください[XmlNamedNodeMap.RemoveNamedItem メソッド](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem)です。</span><span class="sxs-lookup"><span data-stu-id="e67d8-119">To see an additional code example which shows an attribute being removed from an **AttributeCollection**, see [XmlNamedNodeMap.RemoveNamedItem Method](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem).</span></span> <span data-ttu-id="e67d8-120">メソッドとプロパティの詳細については、次を参照してください。 [XmlNamedNodeMap メンバー](AllMembers.T:System.Xml.XmlNamedNodeMap)です。</span><span class="sxs-lookup"><span data-stu-id="e67d8-120">For more information on the methods and properties, see [XmlNamedNodeMap Members](AllMembers.T:System.Xml.XmlNamedNodeMap).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e67d8-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="e67d8-121">See Also</span></span>  
 [<span data-ttu-id="e67d8-122">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="e67d8-122">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
