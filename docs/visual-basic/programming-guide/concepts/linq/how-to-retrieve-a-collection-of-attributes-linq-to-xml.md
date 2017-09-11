---
title: "方法: 属性 (LINQ to XML) のコレクションを取得する (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 696cb1c41d38cfc7f3d739265bf79af62ff456fe
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a><span data-ttu-id="01fa4-102">方法: 属性 (LINQ to XML) のコレクションを取得する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01fa4-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="01fa4-103">このトピックでは、<xref:System.Xml.Linq.XElement.Attributes%2A>メソッド</xref:System.Xml.Linq.XElement.Attributes%2A>。</span><span class="sxs-lookup"><span data-stu-id="01fa4-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="01fa4-104">このメソッドは、要素の属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="01fa4-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01fa4-105">例</span><span class="sxs-lookup"><span data-stu-id="01fa4-105">Example</span></span>  
 <span data-ttu-id="01fa4-106">次の例では、要素の属性のコレクションを反復処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="01fa4-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
```vb  
Dim val = _  
    <Value ID="1243" Type="int" ConvertableTo="double">100</Value>  
Dim listOfAttributes As IEnumerable(Of XAttribute) = _  
    From att In val.Attributes() _  
    Select att  
For Each att As XAttribute In listOfAttributes  
    Console.WriteLine(att)  
Next  
```  
  
 <span data-ttu-id="01fa4-107">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="01fa4-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="01fa4-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="01fa4-108">See Also</span></span>  
 [<span data-ttu-id="01fa4-109">LINQ to XML 軸 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01fa4-109">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
