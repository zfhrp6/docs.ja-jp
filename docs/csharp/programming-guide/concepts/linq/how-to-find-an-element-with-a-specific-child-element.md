---
title: '方法: 特定の子要素を持つ要素を検索する (C#)'
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: e7528784f898f0f9ba84095b080eb82f8458424e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323889"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a>方法: 特定の子要素を持つ要素を検索する (C#)
このトピックでは、特定の値を含む子要素を持つ特定の要素を検索する方法について説明します。  
  
## <a name="example"></a>例  
 この例では、"Examp2.EXE" の値を含む `Test` 子要素を持つ `CommandLine` 要素を検索します。  
  
 この例では、「[サンプル XML ファイル: テスト構成 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md)」の XML ドキュメントを使用します。  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```  
0002  
0006  
```  
  
## <a name="example"></a>例  
 次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。 詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)」を参照してください。  
  
 この例では、「[サンプル XML ファイル : 名前空間内のテスト構成](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md)」の XML ドキュメントを使用します。  
  
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
  
 このコードを実行すると、次の出力が生成されます。  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [基本的なクエリ (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [射影操作 (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
