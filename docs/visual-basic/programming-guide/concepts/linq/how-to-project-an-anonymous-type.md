---
title: "方法: プロジェクトの匿名型 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a9edd260e9bc36449445ee835648573c7bc9c229
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a>方法: プロジェクトの匿名型 (Visual Basic)
短期間しか使用しないことがわかっている新しい型にクエリを射影することが必要になる場合があります。 単に射影で使用するために新しい型を作成するのは大きな負担です。 この場合は、匿名型に射影する方法が効率的です。 匿名型を使用すると、クラス名を指定することなくクラスを定義し、そのクラスのオブジェクトを宣言して初期化できます。  
  
 匿名型は、c# での数学的概念の実装、*組*します。 タプルという数学用語は、1 タプル、2 タプル、3 タプル、4 タプル、5 タプル、n タプルという数列に基づいています。 組とは、それぞれが特定の型を持つオブジェクトの有限のシーケンスを意味します。 名前と値のペアの一覧と呼ばれることもあります。 内のアドレスの内容など、[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) XML ドキュメントに次のように表現できます。  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 匿名型のインスタンスを作成するときは、注文 n のタプルを作成すると考えると簡単です。 `Select` 句でタプルを作成するクエリを記述すると、そのクエリからタプルの `IEnumerable` が返されます。  
  
## <a name="example"></a>例  
 この例では、`Select` 句で匿名型を射影しています。 さらに、`Dim` を使用して `IEnumerable` オブジェクトを作成しています。 `For Each` ループ内では、繰り返し変数が、クエリ式で作成された匿名型のインスタンスになります。  
  
 この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 顧客と注文 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)します。  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>関連項目  
 [射影と変換 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
