---
title: "方法: 単一の子要素を取得する (LINQ to XML) (C#) | Microsoft Docs"
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
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a8cc212a91e4646ef7001d41ba9bb5486cc60052
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a>方法: 単一の子要素を取得する (LINQ to XML) (C#)
このトピックでは、子要素名を指定して単一の子要素を取得する方法について説明します。 子要素の名前が既知であり、この名前を持つ要素が 1 つしか存在しない場合は、コレクションの代わりに 1 つの要素だけを取得する方が便利な場合があります。  
  
 <xref:System.Xml.Linq.XContainer.Element%2A> メソッドでは、<xref:System.Xml.Linq.XName> を指定して最初の子 <xref:System.Xml.Linq.XElement> を返します。  
  
 Visual Basic で単一の子要素を取得する場合の一般的な方法は、XML プロパティを使用し、配列インデクサー表記を使用して最初の要素を取得する方法です。  
  
## <a name="example"></a>例  
 次に <xref:System.Xml.Linq.XContainer.Element%2A> メソッドの使用例を示します。 この例では、`po` という名前の XML ツリーを受け取り、`Comment` という名前の最初の要素を検索します。  
  
 Visual Basic の例では、配列インデクサー表記を使用して単一の要素を取得しています。  
  
 この例では、「[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md)」の XML ドキュメントを使用します。  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a>例  
 上記と同じコードを使用して、名前空間内の XML から要素を取得する例を次に示します。 詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)」を参照してください。  
  
 この例では、XML ドキュメントの「[サンプル XML ファイル : 名前空間内の一般的な購買発注書](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md)」を使用します。  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML 軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)

