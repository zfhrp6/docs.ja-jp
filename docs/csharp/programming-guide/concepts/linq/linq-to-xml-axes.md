---
title: "LINQ to XML 軸 (C#) | Microsoft Docs"
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
ms.assetid: 3f7d54ff-b608-43a1-9e2d-e70668b72df8
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 696a9057d5eb9d2a8c3a263c02571a0913af89f3
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-axes-c"></a>LINQ to XML 軸 (C#)
XML ツリーを作成した後、または XML ドキュメントを XML ツリーに読み込んだ後は、クエリを実行して要素や属性を調べたり、その値を取得したりできます。  
  
 クエリを記述する前に、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 軸について理解しておく必要があります。 軸メソッドは 2 種類あります。まず、単一の <xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、または <xref:System.Xml.Linq.XNode> オブジェクトで呼び出すメソッドがあります。 これらのメソッドは、単一のオブジェクトに対して機能し、<xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XAttribute>、または <xref:System.Xml.Linq.XNode> オブジェクトのコレクションを返します。 第 2 に、コレクションに対して機能し、コレクションを返す拡張メソッドがあります。 拡張メソッドは、ソース コレクションを列挙し、コレクション内の各アイテムに対して適切な軸メソッドを呼び出し、結果を連結します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[LINQ to XML 軸の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|軸を定義し、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クエリのコンテキストにおける使用方法について説明します。|  
|[方法: 要素のコレクションを取得する (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|<xref:System.Xml.Linq.XContainer.Elements%2A> メソッドについて説明します。 このメソッドは、要素の子要素のコレクションを取得します。|  
|[方法: 要素の値を取得する (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|要素の値を取得する方法について説明します。|  
|[方法: 要素名をフィルター処理する (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|軸を使用する場合に要素名をフィルター処理する方法について説明します。|  
|[方法: 軸メソッドの呼び出しを連結する (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|軸メソッドの呼び出しを連結する方法について説明します。|  
|[方法: 単一の子要素を取得する (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|タグ名を指定して要素の単一の子要素を取得する方法について説明します。|  
|[方法: 属性のコレクションを取得する (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|<xref:System.Xml.Linq.XElement.Attributes%2A> メソッドについて説明します。 このメソッドは、要素の属性を取得します。|  
|[方法: 単一の属性を取得する (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|属性名を指定して要素の単一の属性を取得する方法について説明します。|  
|[方法: 属性の値を取得する (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|属性の値を取得する方法について説明します。|  
|[方法: 要素の浅い値を取得する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|要素の浅い値を取得する方法について説明します。|  
  
## <a name="see-also"></a>関連項目  
 [拡張メソッド](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)   
 [プログラミング ガイド (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
