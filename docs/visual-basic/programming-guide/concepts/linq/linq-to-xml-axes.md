---
title: "LINQ to XML 軸 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4d6466a78c3a8e9d21e30f2d3cf8a49ed89dafbf
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-axes-visual-basic"></a>LINQ to XML 軸 (Visual Basic)
XML ツリーを作成した後、または XML ドキュメントを XML ツリーに読み込んだ後は、クエリを実行して要素や属性を調べたり、その値を取得したりできます。  
  
 クエリを記述する前に、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 軸について理解しておく必要があります。 軸メソッドの&2; つの種類があります: は、1 つを呼び出す方法が最初に、<xref:System.Xml.Linq.XElement>オブジェクト、<xref:System.Xml.Linq.XDocument>オブジェクト、または<xref:System.Xml.Linq.XNode>オブジェクト</xref:System.Xml.Linq.XNode></xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。 これらのメソッドは、単一のオブジェクトに対して機能しのコレクションを返す<xref:System.Xml.Linq.XElement>、 <xref:System.Xml.Linq.XAttribute>、または<xref:System.Xml.Linq.XNode>オブジェクト</xref:System.Xml.Linq.XNode></xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement>。 第&2; に、コレクションに対して機能し、コレクションを返す拡張メソッドがあります。 拡張メソッドは、ソース コレクションを列挙し、コレクション内の各アイテムに対して適切な軸メソッドを呼び出し、結果を連結します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[LINQ to XML 軸の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|軸を定義し、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クエリのコンテキストにおける使用方法について説明します。|  
|[方法: 要素 (LINQ to XML) のコレクションを取得する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|導入されています、<xref:System.Xml.Linq.XContainer.Elements%2A>メソッド</xref:System.Xml.Linq.XContainer.Elements%2A>。 このメソッドは、要素の子要素のコレクションを取得します。|  
|[方法: 要素 (LINQ to XML) の値を取得 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|要素の値を取得する方法について説明します。|  
|[方法: 要素名 (LINQ to XML) をフィルター処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|軸を使用する場合に要素名をフィルター処理する方法について説明します。|  
|[方法: 軸メソッドの呼び出し (LINQ to XML) を連結する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|軸メソッドの呼び出しを連結する方法について説明します。|  
|[方法: 単一の子要素 (LINQ to XML) を取得 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|タグ名を指定して要素の単一の子要素を取得する方法について説明します。|  
|[方法: 属性 (LINQ to XML) のコレクションを取得する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|導入されています、<xref:System.Xml.Linq.XElement.Attributes%2A>メソッド</xref:System.Xml.Linq.XElement.Attributes%2A>。 このメソッドは、要素の属性を取得します。|  
|[方法: 単一の属性 (LINQ to XML) を取得する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|属性名を指定して要素の単一の属性を取得する方法について説明します。|  
|[方法: 属性 (LINQ to XML) の値を取得 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|属性の値を取得する方法について説明します。|  
|[方法: 要素 (Visual Basic) の浅い値を取得](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|要素の浅い値を取得する方法について説明します。|  
|[Visual Basic (LINQ to XML) での統合言語軸](../../../../visual-basic/programming-guide/concepts/linq/language-integrated-axes.md)|要約、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]統合軸です。|  
  
## <a name="see-also"></a>関連項目  
 [プログラミング ガイド (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
