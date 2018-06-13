---
title: 名前またはインデックスによる順序付けられていないノードの取得
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 785a609455a35dd87a9593f00b58fd160ac708e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572942"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a><span data-ttu-id="ba70b-102">名前またはインデックスによる順序付けられていないノードの取得</span><span class="sxs-lookup"><span data-stu-id="ba70b-102">Unordered Node Retrieval by Name or Index</span></span>
<span data-ttu-id="ba70b-103">W3C (World Wide Web Consortium) 仕様で NamedNodeMap として定義されている **XmlNamedNodeMap** は、名前またはインデックスでノードを参照する機能を持っており、順序付けられていないノード セットを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba70b-103">The **XmlNamedNodeMap** is described in the World Wide Web Consortium (W3C) specification as the NamedNodeMap and is required to handle an unordered set of nodes with the ability to reference nodes by their name or index.</span></span> <span data-ttu-id="ba70b-104">**XmlNamedNodeMap** にアクセスできるのは、メソッドまたはプロパティから **XmlNamedNodeMap** が返されたときだけです。</span><span class="sxs-lookup"><span data-stu-id="ba70b-104">The only way you have access to an **XmlNamedNodeMap** is when an **XmlNamedNodeMap** is returned through a method or property.</span></span> <span data-ttu-id="ba70b-105">**XmlNamedNodeMap** を返すメソッドやプロパティには、次の 3 つがあります。</span><span class="sxs-lookup"><span data-stu-id="ba70b-105">There are three methods or properties that return an **XmlNamedNodeMap**:</span></span>  
  
-   <span data-ttu-id="ba70b-106">XmlElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="ba70b-106">XmlElement.Attributes</span></span>  
  
-   <span data-ttu-id="ba70b-107">XmlDocumentType.Entities</span><span class="sxs-lookup"><span data-stu-id="ba70b-107">XmlDocumentType.Entities</span></span>  
  
-   <span data-ttu-id="ba70b-108">XmlDocumentType.Notations</span><span class="sxs-lookup"><span data-stu-id="ba70b-108">XmlDocumentType.Notations</span></span>  
  
 <span data-ttu-id="ba70b-109">たとえば、**XmlDocumentType.Entities** プロパティは、ドキュメント型宣言で宣言された **XmlEntity** ノードのコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="ba70b-109">For example, the **XmlDocumentType.Entities** property gets the collection of **XmlEntity** nodes declared in the document type declaration.</span></span> <span data-ttu-id="ba70b-110">このコレクションは **XmlNamedNodeMap** として返され、**Count** プロパティを使用してコレクションを反復処理し、エンティティ情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="ba70b-110">This collection is returned as an **XmlNamedNodeMap**, and you can iterate through the collection with the use of the **Count** property and display entity information.</span></span> <span data-ttu-id="ba70b-111">**XmlNamedNodeMap** の反復処理の例については、「<xref:System.Xml.XmlDocumentType.Entities%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba70b-111">For an example of iterating through an **XmlNamedNodeMap**, see <xref:System.Xml.XmlDocumentType.Entities%2A>.</span></span>  
  
 <span data-ttu-id="ba70b-112">**XmlAttributeCollection** は **XmlNamedNodeMap** から派生しており、属性だけは変更できますが、記法とエンティティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="ba70b-112">The **XmlAttributeCollection** is derived from **XmlNamedNodeMap** and only attributes are modifiable, while notations and entities are read-only.</span></span> <span data-ttu-id="ba70b-113">属性に対して **XmlNamedNodeMap** を使用すると、XML 名に基づいて属性のノードを取得できます。</span><span class="sxs-lookup"><span data-stu-id="ba70b-113">Using the **XmlNamedNodeMap** for the attributes, you can get nodes for those attributes based on their XML names.</span></span> <span data-ttu-id="ba70b-114">これは、要素ノードの属性コレクションを操作する簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="ba70b-114">This provides an easy method for manipulating the collection of attributes on an element node.</span></span> <span data-ttu-id="ba70b-115">**XmlNodeList** にも **IEnumerable** インターフェイスが実装されていますが、文字列ではなくインデックス アクセサーを使用するという点で異なります。</span><span class="sxs-lookup"><span data-stu-id="ba70b-115">This can be contrasted directly with **XmlNodeList**, which also implements the **IEnumerable** interface, but with an index accessor rather than a string.</span></span> <span data-ttu-id="ba70b-116">**RemoveNamedItem** メソッドと **SetNamedItem** メソッドは **XmlAttributeCollection** に対してだけ使用します。</span><span class="sxs-lookup"><span data-stu-id="ba70b-116">The **RemoveNamedItem** and **SetNamedItem** methods are only used against an **XmlAttributeCollection**.</span></span> <span data-ttu-id="ba70b-117">属性コレクションに追加したり、属性コレクションから削除すると、**AttributeCollection** または **XmlNamedNodeMap** のどちらの実装を使用した場合でも、要素の属性コレクションが変更されます。</span><span class="sxs-lookup"><span data-stu-id="ba70b-117">Adding or removing from an attribute collection, whether using the **AttributeCollection** or the **XmlNamedNodeMap** implementation, modifies the attribute collection on the element.</span></span> <span data-ttu-id="ba70b-118">属性を移動する方法と新しい属性を作成する方法を次のコード サンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="ba70b-118">The following code example shows how to move an attribute and create a new attribute.</span></span>  
  
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
  
 <span data-ttu-id="ba70b-119">**AttributeCollection** から属性を削除するコード サンプルについては、「[XmlNamedNodeMap.RemoveNamedItem メソッド](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba70b-119">To see an additional code example which shows an attribute being removed from an **AttributeCollection**, see [XmlNamedNodeMap.RemoveNamedItem Method](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem).</span></span> <span data-ttu-id="ba70b-120">メソッドとプロパティの詳細については、「[XmlNamedNodeMap メンバー](AllMembers.T:System.Xml.XmlNamedNodeMap)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba70b-120">For more information on the methods and properties, see [XmlNamedNodeMap Members](AllMembers.T:System.Xml.XmlNamedNodeMap).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba70b-121">参照</span><span class="sxs-lookup"><span data-stu-id="ba70b-121">See Also</span></span>  
 [<span data-ttu-id="ba70b-122">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="ba70b-122">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
