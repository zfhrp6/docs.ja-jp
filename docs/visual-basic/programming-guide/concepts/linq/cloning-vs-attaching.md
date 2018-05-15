---
title: 複製とアタッチ (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3c3bd105-c9d3-49bd-875b-27ab4e8bc7a3
ms.openlocfilehash: 35a265d2aaef40977a9a6b89d174e9a585c525c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="cloning-vs-attaching-visual-basic"></a><span data-ttu-id="9a01e-102">複製とアタッチ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a01e-102">Cloning vs. Attaching (Visual Basic)</span></span>
<span data-ttu-id="9a01e-103"><xref:System.Xml.Linq.XNode> オブジェクト (<xref:System.Xml.Linq.XElement> を含む) や <xref:System.Xml.Linq.XAttribute> オブジェクトを新しいツリーに追加するときに、新しいコンテンツに親がない場合、単にオブジェクトが XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="9a01e-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="9a01e-104">新しいコンテンツに既に親があり、別の XML ツリーの一部となっている場合は、新しいコンテンツが複製されます。</span><span class="sxs-lookup"><span data-stu-id="9a01e-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="9a01e-105">新しく複製されたコンテンツは、XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="9a01e-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a01e-106">例</span><span class="sxs-lookup"><span data-stu-id="9a01e-106">Example</span></span>  
 <span data-ttu-id="9a01e-107">次のコードでは、親を持つ要素をツリーに追加する場合と親を持たない要素をツリーに追加する場合の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="9a01e-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 <span data-ttu-id="9a01e-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9a01e-108">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a01e-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a01e-109">See Also</span></span>  
 [<span data-ttu-id="9a01e-110">XML ツリー (Visual Basic) を作成します。</span><span class="sxs-lookup"><span data-stu-id="9a01e-110">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
