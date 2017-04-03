---
title: "方法: 軸メソッドの呼び出しを連結する (LINQ to XML) (C#) | Microsoft Docs"
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
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a47129d3c84d7bfb49929529a50b064c8424b4c3
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a>方法: 軸メソッドの呼び出しを連結する (LINQ to XML) (C#)
コードで使用する一般的なパターンでは、軸メソッドを呼び出してから、拡張メソッド軸のいずれかを呼び出します。  
  
 要素のコレクションを返す `Elements` という名前の軸が 2 つ存在します。<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> メソッドと <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> メソッドです。 この 2 つの軸を組み合わせて、ツリー内の指定した深さで指定した名前を持つ要素をすべて検索できます。  
  
## <a name="example"></a>例  
 この例では、<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> と <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> を使用して、すべての `PurchaseOrder` 要素のすべての `Address` 要素に含まれるすべての `Name` 要素を検索します。  
  
 この例では、「[サンプル XML ファイル: 複数の購買発注書 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)」の XML ドキュメントを使用します。  
  
```csharp  
XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements("PurchaseOrder")  
        .Elements("Address")  
        .Elements("Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 このコードが正しく動作するのは、`Elements` 軸のいずれかの実装が、<xref:System.Xml.Linq.XContainer> の <xref:System.Collections.Generic.IEnumerable%601> に対する拡張メソッドとして存在しているためです。 <xref:System.Xml.Linq.XElement> は <xref:System.Xml.Linq.XContainer> から派生しているため、<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> メソッド呼び出しの結果に対して <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> メソッドを呼び出すことができます。  
  
## <a name="example"></a>例  
 祖先が介在する可能性と介在しないが可能性がある場合に、特定の要素の深さにあるすべての要素を取得しなければならないことがあります。 たとえば、次のドキュメントで、`ConfigParameter` 要素の子である `Customer` 要素はすべて取得し、`ConfigParameter` 要素の子である `Root` は取得しないとします。  
  
```xml  
<Root>  
  <ConfigParameter>RootConfigParameter</ConfigParameter>  
  <Customer>  
    <Name>Frank</Name>  
    <Config>  
      <ConfigParameter>FirstConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
  <Customer>  
    <Name>Bob</Name>  
    <!--This customer doesn't have a Config element-->  
  </Customer>  
  <Customer>  
    <Name>Bill</Name>  
    <Config>  
      <ConfigParameter>SecondConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
</Root>  
```  
  
 これは、次のように <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> 軸を使って行うことができます。  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a>例  
 次の例は名前空間に含まれている XML 用の手法です。これらの手法は上の例と同じ機能を表しています。 詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)」を参照してください。  
  
 この例では、「[サンプル XML ファイル: 名前空間内の複数の購買発注書](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)」の XML ドキュメントを使用します。  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement purchaseOrders = XElement.Load("PurchaseOrdersInNamespace.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements(aw + "PurchaseOrder")  
        .Elements(aw + "Address")  
        .Elements(aw + "Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML 軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
