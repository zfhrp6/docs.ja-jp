---
title: "XAttribute クラスの概要 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1ce5f4be6006908b35057854f89432471fd9f06b
ms.lasthandoff: 03/13/2017

---
# <a name="xattribute-class-overview-visual-basic"></a>XAttribute クラスの概要 (Visual Basic)
属性は、要素に関連付けられている名前と値のペアです。 <xref:System.Xml.Linq.XAttribute>クラスは XML 属性を表します</xref:System.Xml.Linq.XAttribute>。  
  
## <a name="overview"></a>概要  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] での属性の操作は、要素の操作に似ています。 コンストラクターはほぼ同じです。 それぞれのコレクションの取得に使用するメソッドもほぼ同じです。 A[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]属性のコレクションのクエリ式によく似た、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]要素のコレクションの式をクエリします。  
  
 属性が要素に追加された順序は保持されます。 つまり、属性を反復処理する場合、属性は追加された順序と同じ順序で表示されます。  
  
## <a name="the-xattribute-constructor"></a>XAttribute コンストラクター  
 次のコンス トラクター、<xref:System.Xml.Linq.XAttribute>クラスは、最もよく使用するもの:</xref:System.Xml.Linq.XAttribute>  
  
|コンストラクター|説明|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|作成、<xref:System.Xml.Linq.XAttribute>オブジェクト</xref:System.Xml.Linq.XAttribute>。 `name` 引数には属性の名前を指定し、`content` には属性のコンテンツを指定します。|  
  
### <a name="creating-an-element-with-an-attribute"></a>属性を持つ要素の作成  
 次のコードは、Visual Basic で XML リテラルを使用して、属性を含む要素を示しています。  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>属性の関数型構築  
 構築する<xref:System.Xml.Linq.XAttribute>の構築と共にインラインで<xref:System.Xml.Linq.XElement>オブジェクトを次のように:</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XAttribute>  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a>属性はノードではない  
 属性と要素には、いくつかの違いがあります。 <xref:System.Xml.Linq.XAttribute>オブジェクトは、XML ツリー内のノードではありません。</xref:System.Xml.Linq.XAttribute> 属性は、XML 要素に関連付けられている名前と値のペアです。 ドキュメント オブジェクト モデル (DOM) とは異なり、XML の構造をより密接に反映します。 <xref:System.Xml.Linq.XAttribute>オブジェクトが実際に、この XML ツリーの操作でノードではない<xref:System.Xml.Linq.XAttribute>オブジェクトは、操作に非常に似て<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute>。  
  
 属性と要素の区別は主に、ノード レベルで XML ツリーを操作するコードを記述する開発者にとってのみ重要な意味を持ちます。 多くの開発者は、この区別を考慮する必要はありません。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML プログラミングの概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
