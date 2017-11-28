---
title: "方法: 属性の値を取得する (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 12720ca8bd1937d37f8d30400e0b25afa22a40cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="254ff-102">方法: 属性の値を取得する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="254ff-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="254ff-103">このトピックでは、属性の値を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="254ff-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="254ff-104">主に 2 つの方法があります。1 つは、<xref:System.Xml.Linq.XAttribute> を目的の型にキャストする方法です。その後、明示的な変換演算子によって、要素または属性のコンテンツが指定した型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="254ff-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="254ff-105">もう 1 つは、<xref:System.Xml.Linq.XAttribute.Value%2A> プロパティを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="254ff-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="254ff-106">ただし、通常はキャストがより適切な方法です。</span><span class="sxs-lookup"><span data-stu-id="254ff-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="254ff-107">属性を NULL 値が許容される型にキャストすると、存在が不明確な属性の値を取得する場合にコードをより簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="254ff-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="254ff-108">この手法の例については、「[方法: 要素の値を取得する (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="254ff-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="254ff-109">例</span><span class="sxs-lookup"><span data-stu-id="254ff-109">Example</span></span>  
 <span data-ttu-id="254ff-110">属性の値を取得するには、<xref:System.Xml.Linq.XAttribute> オブジェクトを目的の型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="254ff-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="254ff-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="254ff-111">This example produces the following output:</span></span>  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="254ff-112">例</span><span class="sxs-lookup"><span data-stu-id="254ff-112">Example</span></span>  
 <span data-ttu-id="254ff-113">属性が名前空間内にある場合にその属性の値を取得する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="254ff-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="254ff-114">詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="254ff-114">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="254ff-115">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="254ff-115">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="254ff-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="254ff-116">See Also</span></span>  
 [<span data-ttu-id="254ff-117">LINQ to XML 軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="254ff-117">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
