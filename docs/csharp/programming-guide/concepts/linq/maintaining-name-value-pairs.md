---
title: "名前と値のペアの保持 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9515411123ad800df4e800d698921b76f6590286
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="maintaining-namevalue-pairs-c"></a><span data-ttu-id="e78e9-102">名前と値のペアの保持 (C#)</span><span class="sxs-lookup"><span data-stu-id="e78e9-102">Maintaining Name/Value Pairs (C#)</span></span>
<span data-ttu-id="e78e9-103">多くのアプリケーションでは、情報を名前と値のペアとして保持するのが最適な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e78e9-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="e78e9-104">このような情報には、構成情報やグローバル設定などがあります。</span><span class="sxs-lookup"><span data-stu-id="e78e9-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="e78e9-105"> には、名前と値のペアのセットを簡単に保持できるようにするメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="e78e9-105"> contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="e78e9-106">情報を属性として保持することも、子要素のセットとして保持することもできます。</span><span class="sxs-lookup"><span data-stu-id="e78e9-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="e78e9-107">情報を属性として保持する場合と子要素として保持する場合の違いの 1 つは、要素の特定の名前を持つ属性は 1 つしか存在できないという制約が属性にはあることです。</span><span class="sxs-lookup"><span data-stu-id="e78e9-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="e78e9-108">この制限は子要素には適用されません。</span><span class="sxs-lookup"><span data-stu-id="e78e9-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="e78e9-109">SetAttributeValue と SetElementValue</span><span class="sxs-lookup"><span data-stu-id="e78e9-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="e78e9-110">名前と値のペアの保持を容易にする 2 つのメソッドは、<xref:System.Xml.Linq.XElement.SetAttributeValue%2A> と <xref:System.Xml.Linq.XElement.SetElementValue%2A> です。</span><span class="sxs-lookup"><span data-stu-id="e78e9-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="e78e9-111">これらの 2 つのメソッドは、よく似たセマンティクスを持っています。</span><span class="sxs-lookup"><span data-stu-id="e78e9-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="e78e9-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> は、要素の属性を追加、変更、または削除できます。</span><span class="sxs-lookup"><span data-stu-id="e78e9-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
-   <span data-ttu-id="e78e9-113">存在しない属性の名前を指定して <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> を呼び出すと、新しい属性が作成され、その属性が指定した要素に追加されます。</span><span class="sxs-lookup"><span data-stu-id="e78e9-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="e78e9-114">既存の属性の名前およびコンテンツを指定して <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> を呼び出すと、その属性のコンテンツが指定したコンテンツに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="e78e9-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="e78e9-115">既存の属性の名前を指定して <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> を呼び出し、コンテンツに NULL を指定すると、その属性が親から削除されます。</span><span class="sxs-lookup"><span data-stu-id="e78e9-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="e78e9-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> は、要素の子要素を追加、変更、または削除できます。</span><span class="sxs-lookup"><span data-stu-id="e78e9-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
-   <span data-ttu-id="e78e9-117">存在しない子要素の名前を指定して <xref:System.Xml.Linq.XElement.SetElementValue%2A> を呼び出すと、新しい要素が作成され、その要素が指定した要素に追加されます。</span><span class="sxs-lookup"><span data-stu-id="e78e9-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="e78e9-118">既存の要素の名前およびコンテンツを指定して <xref:System.Xml.Linq.XElement.SetElementValue%2A> を呼び出すと、その要素のコンテンツが指定したコンテンツに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="e78e9-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="e78e9-119">既存の要素の名前を指定して <xref:System.Xml.Linq.XElement.SetElementValue%2A> を呼び出し、コンテンツに NULL を指定すると、その要素が親から削除されます。</span><span class="sxs-lookup"><span data-stu-id="e78e9-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e78e9-120">例</span><span class="sxs-lookup"><span data-stu-id="e78e9-120">Example</span></span>  
 <span data-ttu-id="e78e9-121">次の例では、属性を持たない要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="e78e9-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="e78e9-122">次に、<xref:System.Xml.Linq.XElement.SetAttributeValue%2A> メソッドを使用して名前と値のペアの一覧を作成して保持します。</span><span class="sxs-lookup"><span data-stu-id="e78e9-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22);  
root.SetAttributeValue("Left", 20);  
root.SetAttributeValue("Bottom", 122);  
root.SetAttributeValue("Right", 300);  
root.SetAttributeValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
  
// Replace the value of Top.  
root.SetAttributeValue("Top", 10);  
Console.WriteLine(root);  
  
// Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="e78e9-123">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e78e9-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="e78e9-124">例</span><span class="sxs-lookup"><span data-stu-id="e78e9-124">Example</span></span>  
 <span data-ttu-id="e78e9-125">次の例では、子要素を持たない要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="e78e9-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="e78e9-126">次に、<xref:System.Xml.Linq.XElement.SetElementValue%2A> メソッドを使用して名前と値のペアの一覧を作成して保持します。</span><span class="sxs-lookup"><span data-stu-id="e78e9-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22);  
root.SetElementValue("Left", 20);  
root.SetElementValue("Bottom", 122);  
root.SetElementValue("Right", 300);  
root.SetElementValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Replace the value of Top.  
root.SetElementValue("Top", 10);  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Remove DefaultColor.  
root.SetElementValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="e78e9-127">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e78e9-127">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e78e9-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="e78e9-128">See Also</span></span>  
 <span data-ttu-id="e78e9-129"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span><span class="sxs-lookup"><span data-stu-id="e78e9-129"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A></span></span>   
 <span data-ttu-id="e78e9-130"><xref:System.Xml.Linq.XElement.SetElementValue%2A></span><span class="sxs-lookup"><span data-stu-id="e78e9-130"><xref:System.Xml.Linq.XElement.SetElementValue%2A></span></span>   
 [<span data-ttu-id="e78e9-131">XML ツリーの変更 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e78e9-131">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)

