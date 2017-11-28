---
title: "複合キーを使用した結合"
description: "複合キーを使用して結合する方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: c285e768d64d1da7e428e29fc67838e87575500c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="join-by-using-composite-keys"></a>複合キーを使用した結合

この例では、複数のキーを使用して一致項目を定義する結合操作の実行方法を示します。 この操作は複合キーを使用して行います。 比較対象とする値を使用し、匿名型または名前付きの型として複合キーを作成します。 メソッドの境界を越えてクエリ変数が渡される場合は、キーの <xref:System.Object.Equals%2A> と <xref:System.Object.GetHashCode%2A> をオーバーライドする名前付きの型を使用してください。 各キーのプロパティ名とその出現順序は一致している必要があります。  
  
## <a name="example"></a>例  
 次の例では、複合キーを使用して 3 つのテーブルのデータを結合する方法を示します。  
  
```csharp  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,        d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 複合キーの型の推定は、キーに含まれるプロパティの名前とその出現順序によって異なります。 ソース シーケンス内のプロパティの名前が異なる場合は、キー内で新しい名前を割り当てる必要があります。 たとえば、`Orders` テーブルと `OrderDetails` テーブルの列にそれぞれ異なる名前が使用されている場合、匿名型で同じ名前を割り当てることにより、復号キーを作成できます。  
  
```csharp  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 複合キーは、`group` 句でも使用できます。  

## <a name="see-also"></a>関連項目  
 [LINQ クエリ式](index.md)  
 [join 句](../language-reference/keywords/join-clause.md)  
 [group 句](../language-reference/keywords/group-clause.md)
