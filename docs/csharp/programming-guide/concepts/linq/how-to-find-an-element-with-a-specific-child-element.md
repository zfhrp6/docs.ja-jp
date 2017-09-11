---
title: "方法: 特定の子要素を持つ要素を検索する (C#)"
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
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: dcbfe8efb16dd5e672deeac2fffea109689dacc5
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="e57d9-102">方法: 特定の子要素を持つ要素を検索する (C#)</span><span class="sxs-lookup"><span data-stu-id="e57d9-102">How to: Find an Element with a Specific Child Element (C#)</span></span>
<span data-ttu-id="e57d9-103">このトピックでは、特定の値を含む子要素を持つ特定の要素を検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e57d9-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e57d9-104">例</span><span class="sxs-lookup"><span data-stu-id="e57d9-104">Example</span></span>  
 <span data-ttu-id="e57d9-105">この例では、"Examp2.EXE" の値を含む `Test` 子要素を持つ `CommandLine` 要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="e57d9-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="e57d9-106">この例では、「[サンプル XML ファイル: テスト構成 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="e57d9-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="e57d9-107">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e57d9-107">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="e57d9-108">例</span><span class="sxs-lookup"><span data-stu-id="e57d9-108">Example</span></span>  
 <span data-ttu-id="e57d9-109">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="e57d9-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e57d9-110">詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e57d9-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="e57d9-111">この例では、「[サンプル XML ファイル : 名前空間内のテスト構成](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="e57d9-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfigInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<XElement> tests =  
    from el in root.Elements(ad + "Test")  
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="e57d9-112">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e57d9-112">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="e57d9-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e57d9-113">See Also</span></span>  
 <span data-ttu-id="e57d9-114"><xref:System.Xml.Linq.XElement.Attribute%2A></span><span class="sxs-lookup"><span data-stu-id="e57d9-114"><xref:System.Xml.Linq.XElement.Attribute%2A></span></span>   
 <span data-ttu-id="e57d9-115"><xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="e57d9-115"><xref:System.Xml.Linq.XContainer.Elements%2A></span></span>   
 <span data-ttu-id="e57d9-116">[基本的なクエリ (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="e57d9-116">[Basic Queries (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span></span>  
 <span data-ttu-id="e57d9-117">[標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="e57d9-117">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 [<span data-ttu-id="e57d9-118">射影操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="e57d9-118">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)

