---
title: 複製とアタッチ (C#)
ms.date: 07/20/2015
ms.assetid: 357c5efa-7b73-4f14-aa67-6bebdba4e7ea
ms.openlocfilehash: 31b5498e18e63ffba357b34780c7eb388e08b37f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="cloning-vs-attaching-c"></a><span data-ttu-id="d26f6-102">複製とアタッチ (C#)</span><span class="sxs-lookup"><span data-stu-id="d26f6-102">Cloning vs. Attaching (C#)</span></span>
<span data-ttu-id="d26f6-103"><xref:System.Xml.Linq.XNode> オブジェクト (<xref:System.Xml.Linq.XElement> を含む) や <xref:System.Xml.Linq.XAttribute> オブジェクトを新しいツリーに追加するときに、新しいコンテンツに親がない場合、単にオブジェクトが XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="d26f6-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="d26f6-104">新しいコンテンツに既に親があり、別の XML ツリーの一部となっている場合は、新しいコンテンツが複製されます。</span><span class="sxs-lookup"><span data-stu-id="d26f6-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="d26f6-105">新しく複製されたコンテンツは、XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="d26f6-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d26f6-106">例</span><span class="sxs-lookup"><span data-stu-id="d26f6-106">Example</span></span>  
 <span data-ttu-id="d26f6-107">次のコードでは、親を持つ要素をツリーに追加する場合と親を持たない要素をツリーに追加する場合の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="d26f6-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  
```  
  
 <span data-ttu-id="d26f6-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d26f6-108">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="d26f6-109">参照</span><span class="sxs-lookup"><span data-stu-id="d26f6-109">See Also</span></span>  
 [<span data-ttu-id="d26f6-110">XML ツリーの作成 (C#)</span><span class="sxs-lookup"><span data-stu-id="d26f6-110">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
