---
title: "名前と値のペア (Visual Basic) の保持 |Microsoft ドキュメント"
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
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 54db297ecd39e37492dcf8bb4de4f64476662670
ms.lasthandoff: 03/13/2017


---
# <a name="maintaining-namevalue-pairs-visual-basic"></a>(Visual Basic) の名前/値ペアの保持
多くのアプリケーションでは、情報を名前と値のペアとして保持するのが最適な場合があります。 このような情報には、構成情報やグローバル設定などがあります。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] には、名前と値のペアのセットを簡単に保持できるようにするメソッドがあります。 情報を属性として保持することも、子要素のセットとして保持することもできます。  
  
 情報を属性として保持する場合と子要素として保持する場合の違いの&1; つは、要素の特定の名前を持つ属性は&1; つしか存在できないという制約が属性にはあることです。 この制限は子要素には適用されません。  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue と SetElementValue  
 名前と値の保持を容易にする&2; つのメソッドのペアは<xref:System.Xml.Linq.XElement.SetAttributeValue%2A><xref:System.Xml.Linq.XElement.SetElementValue%2A>.</xref:System.Xml.Linq.XElement.SetElementValue%2A> </xref:System.Xml.Linq.XElement.SetAttributeValue%2A> これらの&2; つのメソッドは、よく似たセマンティクスを持っています。  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>できますを追加、変更、または、要素の属性を削除します。</xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
  
-   呼び出した場合<xref:System.Xml.Linq.XElement.SetAttributeValue%2A>が存在しない属性の名前を持つメソッドが新しい属性を作成し、指定された要素に追加します</xref:System.Xml.Linq.XElement.SetAttributeValue%2A>。  
  
-   呼び出した場合<xref:System.Xml.Linq.XElement.SetAttributeValue%2A>コンテンツの既存の属性の名前、および指定の属性のコンテンツが指定された内容で置き換えられます</xref:System.Xml.Linq.XElement.SetAttributeValue%2A>。  
  
-   呼び出した場合<xref:System.Xml.Linq.XElement.SetAttributeValue%2A>、既存の名前を持つ属性があり、指定されたコンテンツの null 属性は親から削除するが</xref:System.Xml.Linq.XElement.SetAttributeValue%2A>。  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>できる追加、変更、または要素の子要素を削除します。</xref:System.Xml.Linq.XElement.SetElementValue%2A>  
  
-   呼び出した場合<xref:System.Xml.Linq.XElement.SetElementValue%2A>が存在しない子要素の名前を持つメソッドが新しい要素を作成し、指定された要素に追加します</xref:System.Xml.Linq.XElement.SetElementValue%2A>。  
  
-   呼び出した場合<xref:System.Xml.Linq.XElement.SetElementValue%2A>コンテンツの既存の要素の名前、および指定の要素のコンテンツが指定された内容で置き換えられます</xref:System.Xml.Linq.XElement.SetElementValue%2A>。  
  
-   呼び出した場合<xref:System.Xml.Linq.XElement.SetElementValue%2A>既存の要素の名前を持つ null コンテンツを指定して、要素が親から削除します</xref:System.Xml.Linq.XElement.SetElementValue%2A>。  
  
## <a name="example"></a>例  
 次の例では、属性を持たない要素を作成します。 次を使用して、<xref:System.Xml.Linq.XElement.SetAttributeValue%2A>メソッドを作成し、名前/値ペアのリストを維持します</xref:System.Xml.Linq.XElement.SetAttributeValue%2A>。  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22)  
root.SetAttributeValue("Left", 20)  
root.SetAttributeValue("Bottom", 122)  
root.SetAttributeValue("Right", 300)  
root.SetAttributeValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
  
' Replace the value of Top.  
root.SetAttributeValue("Top", 10)  
Console.WriteLine(root)  
  
' Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a>例  
 次の例では、子要素を持たない要素を作成します。 次を使用して、<xref:System.Xml.Linq.XElement.SetElementValue%2A>メソッドを作成し、名前/値ペアのリストを維持します</xref:System.Xml.Linq.XElement.SetElementValue%2A>。  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22)  
root.SetElementValue("Left", 20)  
root.SetElementValue("Bottom", 122)  
root.SetElementValue("Right", 300)  
root.SetElementValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Replace the value of Top.  
root.SetElementValue("Top", 10)  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Remove DefaultColor.  
root.SetElementValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A></xref:System.Xml.Linq.XElement.SetAttributeValue%2A>   
 <xref:System.Xml.Linq.XElement.SetElementValue%2A></xref:System.Xml.Linq.XElement.SetElementValue%2A>   
 [XML ツリー (LINQ to XML) の変更 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
