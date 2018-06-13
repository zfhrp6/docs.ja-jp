---
title: '方法 : 名前空間を持つドキュメントを作成する (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 204d8a9cbb6ce47c6334c7309d27910c75b90ae0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643079"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a><span data-ttu-id="ef98a-102">方法 : 名前空間を持つドキュメントを作成する (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef98a-102">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ef98a-103">このトピックでは、Visual Basic で名前空間を持つドキュメントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ef98a-103">This topic shows how to create a document with namespaces in Visual Basic.</span></span>  
  
 <span data-ttu-id="ef98a-104">Visual Basic で XML リテラルを使用している場合、ユーザーは 1 つのグローバルな既定の XML 名前空間を定義できます。</span><span class="sxs-lookup"><span data-stu-id="ef98a-104">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="ef98a-105">この名前空間は、XML リテラルと XML プロパティの両方の既定の名前空間です。</span><span class="sxs-lookup"><span data-stu-id="ef98a-105">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="ef98a-106">既定の XML 名前空間は、プロジェクト レベルまたはファイル レベルで定義できます。</span><span class="sxs-lookup"><span data-stu-id="ef98a-106">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="ef98a-107">ファイル レベルで定義すると、プロジェクト レベルの既定の名前空間がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="ef98a-107">If it is defined at the file level, it overrides the default namespace at the project level.</span></span>  
  
 <span data-ttu-id="ef98a-108">他の名前空間を定義して、それらの名前空間のプレフィックスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ef98a-108">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span>  
  
 <span data-ttu-id="ef98a-109">既定の名前空間およびプレフィックスを持つ名前空間の両方を定義する場合は、`Imports` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="ef98a-109">You define both default namespaces and namespaces with a prefix by using the `Imports` keyword.</span></span>  
  
 <span data-ttu-id="ef98a-110">詳細については、次を参照してください。 [Visual Basic で XML リテラルの概要](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md)です。</span><span class="sxs-lookup"><span data-stu-id="ef98a-110">For more information, see [Introduction to XML Literals in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).</span></span>  
  
 <span data-ttu-id="ef98a-111">既定の XML 名前空間は要素だけに適用され、属性には適用されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ef98a-111">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="ef98a-112">属性は、既定では常に名前空間に含まれません。</span><span class="sxs-lookup"><span data-stu-id="ef98a-112">Attributes are by default always in no namespace.</span></span> <span data-ttu-id="ef98a-113">ただし、名前空間プレフィックスを使用して属性を名前空間に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ef98a-113">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef98a-114">例</span><span class="sxs-lookup"><span data-stu-id="ef98a-114">Example</span></span>  
 <span data-ttu-id="ef98a-115">この例では、1 つの名前空間を含むドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="ef98a-115">This example creates a document that contains a namespace.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child aw:Att="attvalue"/>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="ef98a-116">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ef98a-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="ef98a-117">例</span><span class="sxs-lookup"><span data-stu-id="ef98a-117">Example</span></span>  
 <span data-ttu-id="ef98a-118">この例では、2 つの名前空間を含むドキュメントを作成します。このうちの 1 つは既定の名前空間です。</span><span class="sxs-lookup"><span data-stu-id="ef98a-118">This example creates a document that contains two namespaces, one of which is the default namespace.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child Att="attvalue"/>  
                <fc:Child2>child2 content</fc:Child2>  
            </Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="ef98a-119">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ef98a-119">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="ef98a-120">例</span><span class="sxs-lookup"><span data-stu-id="ef98a-120">Example</span></span>  
 <span data-ttu-id="ef98a-121">次の例では、名前空間プレフィックスを持つ名前空間を 2 つ含むドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="ef98a-121">The following example creates a document that contains multiple namespaces, both with namespace prefixes.</span></span>  
  
 <span data-ttu-id="ef98a-122">XML ツリーをシリアル化するとき、各要素が指定された名前空間に含まれるように、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] によって必要に応じて名前空間宣言が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ef98a-122">When serializing an XML tree, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] emits namespace declarations as required so that each element is in its designated namespace.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="ef98a-123">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ef98a-123">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef98a-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef98a-124">See Also</span></span>  
 [<span data-ttu-id="ef98a-125">XML 名前空間 (Visual Basic) の使用</span><span class="sxs-lookup"><span data-stu-id="ef98a-125">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
