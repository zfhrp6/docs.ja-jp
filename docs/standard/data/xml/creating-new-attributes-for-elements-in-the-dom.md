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
# <a name="creating-new-attributes-for-elements-in-the-dom"></a><span data-ttu-id="20226-102">DOM の要素に対する新しい属性の作成</span><span class="sxs-lookup"><span data-stu-id="20226-102">Creating New Attributes for Elements in the DOM</span></span>
<span data-ttu-id="20226-103">新しい属性を作成するとは異なる属性、ノードではありませんが、要素ノードのプロパティし、に含まれるために、他のノード型の作成、 **XmlAttributeCollection**要素に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="20226-103">Creating new attributes is different than creating other node types, because attributes are not nodes, but are properties of an element node and are contained in an **XmlAttributeCollection** associated with the element.</span></span> <span data-ttu-id="20226-104">属性を作成して要素に追加するには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="20226-104">There are multiple ways to create an attribute and attach it to an element:</span></span>  
  
-   <span data-ttu-id="20226-105">要素ノードを取得しを使用して**SetAttribute**その要素の属性コレクションに属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="20226-105">Get the element node and use **SetAttribute** to add an attribute to the attribute collection of that element.</span></span>  
  
-   <span data-ttu-id="20226-106">作成、 **XmlAttribute**ノードを使用して、 **CreateAttribute**メソッドは、要素ノードを取得しを使用して**SetAttributeNode**ノードをその属性のコレクションに追加するには要素。</span><span class="sxs-lookup"><span data-stu-id="20226-106">Create an **XmlAttribute** node using the **CreateAttribute** method, get the element node, then use **SetAttributeNode** to add the node to the attribute collection of that element.</span></span>  
  
 <span data-ttu-id="20226-107">次の例を使用して、要素に属性を追加する方法を示しています、 **SetAttribute**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="20226-107">The following example shows how to add an attribute to an element using the **SetAttribute** method.</span></span>  
  
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
  
 <span data-ttu-id="20226-108">次の例は、新しい属性を使用して作成する、 **CreateAttribute**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="20226-108">The following example shows a new attribute being created using the **CreateAttribute** method.</span></span> <span data-ttu-id="20226-109">属性の属性コレクションに追加し、表示、 **book**要素を使用して、 **SetAttributeNode**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="20226-109">It then shows the attribute added to the attribute collection of the **book** element using the **SetAttributeNode** method.</span></span>  
  
 <span data-ttu-id="20226-110">次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="20226-110">Given the following XML:</span></span>  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 <span data-ttu-id="20226-111">新しい属性を作成し、その属性の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="20226-111">create a new attribute and give it a value:</span></span>  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 <span data-ttu-id="20226-112">作成した属性を要素に追加します。</span><span class="sxs-lookup"><span data-stu-id="20226-112">and attach it to the element:</span></span>  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 <span data-ttu-id="20226-113">**出力**</span><span class="sxs-lookup"><span data-stu-id="20226-113">**Output**</span></span>  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 <span data-ttu-id="20226-114">完全なコード サンプルはあります<xref:System.Xml.XmlDocument.CreateAttribute%2A>です。</span><span class="sxs-lookup"><span data-stu-id="20226-114">The full code sample can be found at <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span></span>  
  
 <span data-ttu-id="20226-115">作成することも、 **XmlAttribute**ノードと使用、 **InsertBefore**または**InsertAfter**コレクション内の適切な位置に配置する方法です。</span><span class="sxs-lookup"><span data-stu-id="20226-115">You can also create an **XmlAttribute** node and use the **InsertBefore** or **InsertAfter** methods to place it in the appropriate position in the collection.</span></span> <span data-ttu-id="20226-116">同じ名前を持つ属性が既に既存の属性のコレクションである場合**XmlAttribute**からコレクションと新しいノードが削除された**XmlAttribute**ノードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="20226-116">If an attribute with the same name is already present in the attribute collection, the existing **XmlAttribute** node is removed from the collection and the new **XmlAttribute** node is inserted.</span></span> <span data-ttu-id="20226-117">同じように実行して、 **SetAttribute**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="20226-117">This performs the same way as the **SetAttribute** method.</span></span> <span data-ttu-id="20226-118">既存のノードを行うには参照ポイントとして、パラメーターとして、これらのメソッドを使用、 **InsertBefore**と**InsertAfter**です。</span><span class="sxs-lookup"><span data-stu-id="20226-118">These methods take, as a parameter, an existing node as a reference point to do the **InsertBefore** and **InsertAfter**.</span></span> <span data-ttu-id="20226-119">新しいノードでの既定値を挿入する位置を示す参照ノードを指定しない場合、 **InsertAfter**メソッドは、コレクションの先頭に新しいノードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="20226-119">If you do not provide a reference node indicating where to insert the new node, the default for the **InsertAfter** method is to insert the new node at the beginning of the collection.</span></span> <span data-ttu-id="20226-120">既定の位置、 **InsertBefore**参照ノードが指定されていない場合、コレクションの末尾です。</span><span class="sxs-lookup"><span data-stu-id="20226-120">The default position for the **InsertBefore**, if no reference node is provided, is at the end of the collection.</span></span>  
  
 <span data-ttu-id="20226-121">作成した場合、 **XmlNamedNodeMap**属性の名前を使用して属性を追加することができます、<xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>です。</span><span class="sxs-lookup"><span data-stu-id="20226-121">If you created an **XmlNamedNodeMap** of attributes, you can add an attribute by name using the <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>.</span></span> <span data-ttu-id="20226-122">詳細については、次を参照してください。 [NamedNodeMaps と NodeLists のノード コレクション](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)です。</span><span class="sxs-lookup"><span data-stu-id="20226-122">For more information, see [Node Collections in NamedNodeMaps and NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).</span></span>  
  
## <a name="default-attributes"></a><span data-ttu-id="20226-123">既定の属性</span><span class="sxs-lookup"><span data-stu-id="20226-123">Default Attributes</span></span>  
 <span data-ttu-id="20226-124">既定の属性を持つと宣言された要素を作成すると、既定値を持つ新しい既定の属性が XML ドキュメント オブジェクト モデル (DOM) によって作成され、その要素に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="20226-124">If you create an element that is declared to have a default attribute, then a new default attribute with its default value is created by the XML Document Object Model (DOM) and attached to the element.</span></span> <span data-ttu-id="20226-125">既定の属性の子ノードも同時に作成されます。</span><span class="sxs-lookup"><span data-stu-id="20226-125">The child nodes of the default attribute are also created at this time.</span></span>  
  
## <a name="attribute-child-nodes"></a><span data-ttu-id="20226-126">属性の子ノード</span><span class="sxs-lookup"><span data-stu-id="20226-126">Attribute Child Nodes</span></span>  
 <span data-ttu-id="20226-127">属性ノードの値は、その属性の子ノードになります。</span><span class="sxs-lookup"><span data-stu-id="20226-127">The value of an attribute node becomes its child nodes.</span></span> <span data-ttu-id="20226-128">有効な子ノードの 2 つの種類があります: **XmlText**ノード、および**XmlEntityReference**ノード。</span><span class="sxs-lookup"><span data-stu-id="20226-128">There are only two types of valid child nodes: **XmlText** nodes, and **XmlEntityReference** nodes.</span></span> <span data-ttu-id="20226-129">これらは、という意味で子ノードなどのメソッド**FirstChild**と**LastChild**子ノードとして処理します。</span><span class="sxs-lookup"><span data-stu-id="20226-129">These are child nodes in the sense that methods such as **FirstChild** and **LastChild** process them as child nodes.</span></span> <span data-ttu-id="20226-130">属性が子ノードを持つという点は、属性または属性の子ノードを削除するときに重要になります。</span><span class="sxs-lookup"><span data-stu-id="20226-130">This distinction of an attribute having child nodes is important when trying to remove attributes or attribute child nodes.</span></span> <span data-ttu-id="20226-131">詳細については、次を参照してください。 [DOM の要素ノードからの属性の削除](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md)です。</span><span class="sxs-lookup"><span data-stu-id="20226-131">For more information, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20226-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="20226-132">See Also</span></span>  
 [<span data-ttu-id="20226-133">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="20226-133">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
