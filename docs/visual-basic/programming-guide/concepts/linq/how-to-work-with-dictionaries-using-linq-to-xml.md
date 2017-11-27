---
title: "方法: LINQ to XML (Visual Basic) を使用してディクショナリを使用"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dc7290a3afca22ffc92914efacdb768a72e2aef7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a>方法: LINQ to XML (Visual Basic) を使用してディクショナリを使用
さまざまなデータ構造と XML を相互に変換すると便利な場合がよくあります。 このトピックでは、<xref:System.Collections.Generic.Dictionary%602> と XML を相互に変換することによる、一般的な相互変換の実装について説明します。  
  
## <a name="example"></a>例  
 この例では、埋め込み式の中で XML リテラルと、クエリを使用します。 新しいクエリ プロジェクト<xref:System.Xml.Linq.XElement>するオブジェクトの新しいコンテンツになる、 `Root` <xref:System.Xml.Linq.XElement>オブジェクト。  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>例  
 次のコードは、XML からディクショナリを作成します。  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a>関連項目  
 [射影と変換 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
