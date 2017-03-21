---
title: "方法: 中間値 (Visual Basic) を計算 |Microsoft ドキュメント"
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
ms.assetid: 933a97b2-dfe7-4f4d-94ad-e6e20df84abd
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 58c93ad2de0f4292dde2ee60e60588bbe2cbaa60
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-calculate-intermediate-values-visual-basic"></a>方法: 中間値 (Visual Basic) を計算
この例では、並べ替え、フィルタリング、および選択を実行する際に使用できる中間値を計算する方法について説明します。  
  
## <a name="example"></a>例  
 次の例では、`Let` 句を使用します。  
  
 この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 数値データ (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)します。  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim extensions As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
    Where extension > 25 _  
    Order By extension _  
    Select extension  
For Each ex As Decimal In extensions  
    Console.WriteLine(ex)  
Next  
  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a>例  
 次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。 詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)します。  
  
 この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 数値データ、Namespace を](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md)します。  
  
```vb  
Imports <xmlns="http://www.adatum.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim extensions As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
            Where extension > 25 _  
            Order By extension _  
            Select extension  
        For Each ex As Decimal In extensions  
            Console.WriteLine(ex)  
        Next  
    End Sub  
End Module  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a>関連項目  
 [基本的なクエリ (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
