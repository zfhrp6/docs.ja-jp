---
title: '方法 : 名前空間プレフィックスを制御する (Visual Basic) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: f60f90ef6742dfd725f51ff7e760436117346e85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641681"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a>方法 : 名前空間プレフィックスを制御する (Visual Basic) (LINQ to XML)
このトピックでは、名前空間プレフィックスを制御する方法について説明します。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 この例では、2 つの名前空間を宣言します。 指定する、`http://www.adventure-works.com`名前空間のプレフィックス`aw`、ことと、`www.fourthcoffee.com`名前空間のプレフィックスには`fc`します。  
  
### <a name="code"></a>コード  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
### <a name="comments"></a>コメント  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>関連項目  
 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
