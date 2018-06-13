---
title: '方法 : 名前空間プレフィックスを制御する (C#) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: af864139d56bd3ebb22cca6369b82539b9d007da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327754"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="d3e8d-102">方法 : 名前空間プレフィックスを制御する (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d3e8d-102">How to: Control Namespace Prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="d3e8d-103">このトピックでは、XML ツリーをシリアル化する場合に名前空間プレフィックスを制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3e8d-103">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="d3e8d-104">多くの場合、名前空間プレフィックスを制御する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d3e8d-104">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="d3e8d-105">ただし、特定の XML プログラミング ツールでは、名前空間プレフィックスに対する特定の制御が必要です。</span><span class="sxs-lookup"><span data-stu-id="d3e8d-105">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="d3e8d-106">たとえば、特定の名前空間プレフィックスを参照する組み込みの XPath 式を含む XSLT スタイル シートや XAML ドキュメントを操作する場合は、ドキュメントをそれらの特定のプレフィックスでシリアル化することが重要になります。</span><span class="sxs-lookup"><span data-stu-id="d3e8d-106">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="d3e8d-107">これは、名前空間プレフィックスを制御する最も一般的な理由です。</span><span class="sxs-lookup"><span data-stu-id="d3e8d-107">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="d3e8d-108">名前空間プレフィックスを制御するもう 1 つの一般的な理由として、ユーザーが XML ドキュメントを手動で編集できるようにし、ユーザーにとって入力しやすい名前空間プレフィックスを作成する必要性が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="d3e8d-108">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="d3e8d-109">たとえば、XSD ドキュメントを生成するとします。</span><span class="sxs-lookup"><span data-stu-id="d3e8d-109">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="d3e8d-110">スキーマの規則では、スキーマ名前空間のプレフィックスとして `xs` または `xsd` のいずれかを使用することが推奨されています。</span><span class="sxs-lookup"><span data-stu-id="d3e8d-110">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="d3e8d-111">名前空間プレフィックスを制御するには、名前空間を宣言する属性を挿入します。</span><span class="sxs-lookup"><span data-stu-id="d3e8d-111">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="d3e8d-112">特定のプレフィックスを持つ名前空間を宣言すると、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] はシリアル化の際にその名前空間プレフィックスの使用を試みます。</span><span class="sxs-lookup"><span data-stu-id="d3e8d-112">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="d3e8d-113">プレフィックスを持つ名前空間を宣言する属性を作成するには、属性の名前の名前空間が <xref:System.Xml.Linq.XNamespace.Xmlns%2A> で、属性の名前が名前空間プレフィックスであるような属性を作成します。</span><span class="sxs-lookup"><span data-stu-id="d3e8d-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="d3e8d-114">属性の値は、名前空間の URI です。</span><span class="sxs-lookup"><span data-stu-id="d3e8d-114">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3e8d-115">例</span><span class="sxs-lookup"><span data-stu-id="d3e8d-115">Example</span></span>  
 <span data-ttu-id="d3e8d-116">この例では、2 つの名前空間を宣言します。</span><span class="sxs-lookup"><span data-stu-id="d3e8d-116">This example declares two namespaces.</span></span> <span data-ttu-id="d3e8d-117">`http://www.adventure-works.com` 名前空間のプレフィックスを `aw` と指定し、`www.fourthcoffee.com` 名前空間のプレフィックスを `fc` と指定します。</span><span class="sxs-lookup"><span data-stu-id="d3e8d-117">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="d3e8d-118">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d3e8d-118">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3e8d-119">参照</span><span class="sxs-lookup"><span data-stu-id="d3e8d-119">See Also</span></span>  
 [<span data-ttu-id="d3e8d-120">XML 名前空間の使用 (C#)</span><span class="sxs-lookup"><span data-stu-id="d3e8d-120">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
