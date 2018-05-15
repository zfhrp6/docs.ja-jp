---
title: 名前と値のペアの保持 (C#)
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: ac1e6464618c00cba4ded92492fe4a687e1a25f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="maintaining-namevalue-pairs-c"></a><span data-ttu-id="e6f97-102">名前と値のペアの保持 (C#)</span><span class="sxs-lookup"><span data-stu-id="e6f97-102">Maintaining Name/Value Pairs (C#)</span></span>
<span data-ttu-id="e6f97-103">多くのアプリケーションでは、情報を名前と値のペアとして保持するのが最適な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e6f97-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="e6f97-104">このような情報には、構成情報やグローバル設定などがあります。</span><span class="sxs-lookup"><span data-stu-id="e6f97-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="e6f97-105"> には、名前と値のペアのセットを簡単に保持できるようにするメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="e6f97-105"> contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="e6f97-106">情報を属性として保持することも、子要素のセットとして保持することもできます。</span><span class="sxs-lookup"><span data-stu-id="e6f97-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="e6f97-107">情報を属性として保持する場合と子要素として保持する場合の違いの 1 つは、要素の特定の名前を持つ属性は 1 つしか存在できないという制約が属性にはあることです。</span><span class="sxs-lookup"><span data-stu-id="e6f97-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="e6f97-108">この制限は子要素には適用されません。</span><span class="sxs-lookup"><span data-stu-id="e6f97-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="e6f97-109">SetAttributeValue と SetElementValue</span><span class="sxs-lookup"><span data-stu-id="e6f97-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="e6f97-110">名前と値のペアの保持を容易にする 2 つのメソッドは、<xref:System.Xml.Linq.XElement.SetAttributeValue%2A> と <xref:System.Xml.Linq.XElement.SetElementValue%2A> です。</span><span class="sxs-lookup"><span data-stu-id="e6f97-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="e6f97-111">これらの 2 つのメソッドは、よく似たセマンティクスを持っています。</span><span class="sxs-lookup"><span data-stu-id="e6f97-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="e6f97-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> は、要素の属性を追加、変更、または削除できます。</span><span class="sxs-lookup"><span data-stu-id="e6f97-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
-   <span data-ttu-id="e6f97-113">存在しない属性の名前を指定して <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> を呼び出すと、新しい属性が作成され、その属性が指定した要素に追加されます。</span><span class="sxs-lookup"><span data-stu-id="e6f97-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="e6f97-114">既存の属性の名前およびコンテンツを指定して <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> を呼び出すと、その属性のコンテンツが指定したコンテンツに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="e6f97-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="e6f97-115">既存の属性の名前を指定して <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> を呼び出し、コンテンツに NULL を指定すると、その属性が親から削除されます。</span><span class="sxs-lookup"><span data-stu-id="e6f97-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="e6f97-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> は、要素の子要素を追加、変更、または削除できます。</span><span class="sxs-lookup"><span data-stu-id="e6f97-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
-   <span data-ttu-id="e6f97-117">存在しない子要素の名前を指定して <xref:System.Xml.Linq.XElement.SetElementValue%2A> を呼び出すと、新しい要素が作成され、その要素が指定した要素に追加されます。</span><span class="sxs-lookup"><span data-stu-id="e6f97-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="e6f97-118">既存の要素の名前およびコンテンツを指定して <xref:System.Xml.Linq.XElement.SetElementValue%2A> を呼び出すと、その要素のコンテンツが指定したコンテンツに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="e6f97-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="e6f97-119">既存の要素の名前を指定して <xref:System.Xml.Linq.XElement.SetElementValue%2A> を呼び出し、コンテンツに NULL を指定すると、その要素が親から削除されます。</span><span class="sxs-lookup"><span data-stu-id="e6f97-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6f97-120">例</span><span class="sxs-lookup"><span data-stu-id="e6f97-120">Example</span></span>  
 <span data-ttu-id="e6f97-121">次の例では、属性を持たない要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="e6f97-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="e6f97-122">次に、<xref:System.Xml.Linq.XElement.SetAttributeValue%2A> メソッドを使用して名前と値のペアの一覧を作成して保持します。</span><span class="sxs-lookup"><span data-stu-id="e6f97-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="e6f97-123">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e6f97-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="e6f97-124">例</span><span class="sxs-lookup"><span data-stu-id="e6f97-124">Example</span></span>  
 <span data-ttu-id="e6f97-125">次の例では、子要素を持たない要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="e6f97-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="e6f97-126">次に、<xref:System.Xml.Linq.XElement.SetElementValue%2A> メソッドを使用して名前と値のペアの一覧を作成して保持します。</span><span class="sxs-lookup"><span data-stu-id="e6f97-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="e6f97-127">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e6f97-127">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6f97-128">参照</span><span class="sxs-lookup"><span data-stu-id="e6f97-128">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>  
 [<span data-ttu-id="e6f97-129">XML ツリーの変更 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e6f97-129">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
