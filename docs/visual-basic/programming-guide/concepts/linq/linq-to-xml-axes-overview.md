---
title: "LINQ to XML 軸の概要 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 9161f151-cfa8-4408-94ba-08a9ba3a486d
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b127aa6b443e865c76831d886f110550ec785e9b
ms.lasthandoff: 03/13/2017


---
# <a name="linq-to-xml-axes-overview-visual-basic"></a>LINQ to XML 軸の概要 (Visual Basic)
XML ツリーを作成した後、または XML ドキュメントを XML ツリーに読み込んだ後は、クエリを実行して要素や属性を調べたり、その値を取得したりできます。 コレクションの取得、*軸メソッド*とも呼ばれます*軸*します。 内のメソッドを一部の軸、<xref:System.Xml.Linq.XElement>と<xref:System.Xml.Linq.XDocument>クラスの値を返す<xref:System.Collections.Generic.IEnumerable%601>コレクション</xref:System.Collections.Generic.IEnumerable%601></xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。 <xref:System.Xml.Linq.Extensions>クラス</xref:System.Xml.Linq.Extensions>の拡張メソッドを一部の軸 拡張メソッドとして実装されている軸は、コレクションに対して機能し、コレクションを返します。  
  
 」の説明に従って[XElement クラスの概要](http://msdn.microsoft.com/library/d35180fe-7016-4895-9bfc-ba1e3f7875ec)、<xref:System.Xml.Linq.XElement>オブジェクト&1; つの要素ノードを表します</xref:System.Xml.Linq.XElement>。 要素のコンテンツは、複合要素 (構造化コンテンツとも呼ばれる) または単純要素です。 単純要素は、空の場合と値を含む場合があります。 ノードに構造化コンテンツが含まれている場合、さまざまな軸メソッドを使用して子孫要素の列挙を取得できます。 最もよく使用される軸メソッドは、<xref:System.Xml.Linq.XContainer.Elements%2A>および<xref:System.Xml.Linq.XContainer.Descendants%2A>。</xref:System.Xml.Linq.XContainer.Descendants%2A> </xref:System.Xml.Linq.XContainer.Elements%2A>  
  
 コレクションを返す軸メソッド以外でよく使用される&2; つの以上メソッド[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]クエリ。 <xref:System.Xml.Linq.XContainer.Element%2A>メソッドは、1 つ<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>を返します</xref:System.Xml.Linq.XContainer.Element%2A> <xref:System.Xml.Linq.XElement.Attribute%2A>メソッドは、1 つ<xref:System.Xml.Linq.XAttribute>。</xref:System.Xml.Linq.XAttribute>を返します</xref:System.Xml.Linq.XElement.Attribute%2A>  
  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリは多くの用途において、ツリーを調べてデータを抽出し、それを変換する方法として最も強力です。 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]クエリの操作を実装するオブジェクトの<xref:System.Collections.Generic.IEnumerable%601>、および[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]戻り値の軸<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XElement>コレクション、および<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XAttribute>コレクション</xref:System.Xml.Linq.XAttribute></xref:System.Collections.Generic.IEnumerable%601></xref:System.Xml.Linq.XElement></xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>。 クエリを実行するには、これらのコレクションが必要です。  
  
 要素と属性のコレクションを取得する軸メソッドに加えて、ツリーを詳細に反復処理するための軸メソッドもあります。 たとえば、要素と属性を処理する代わりに、ツリーのノードを操作できます。 ノードは、要素や属性よりも細かい粒度レベルです。 ノードの操作時には、XML コメント、テキスト ノード、処理命令などを調べることができます。 この機能は、たとえば、文書を XML として保存できるワード プロセッサを作成する場合に重要です。 ただし、大多数の XML プログラマが主に扱うのは、要素、属性、およびその値です。  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>要素のコレクションを取得するメソッド  
 メソッドの概要、<xref:System.Xml.Linq.XElement>クラス (またはその基本クラス) で呼び出すこと、<xref:System.Xml.Linq.XElement>要素のコレクションを返します</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement>。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName>|返します、<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XElement>この要素の先祖。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 。 <xref:System.Collections.Generic.IEnumerable%601><xref:System.Xml.Linq.XElement>ある指定した<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>先祖</xref:System.Xml.Linq.XElement>の</xref:System.Collections.Generic.IEnumerable%601>オーバー ロードを返します|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName>|返します、<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XElement>この要素の子孫の。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 。 オーバー ロードを返しますが<xref:System.Collections.Generic.IEnumerable%601><xref:System.Xml.Linq.XElement>、指定した<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>がある子孫</xref:System.Xml.Linq.XElement>の</xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>|返します、<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XElement>この要素の子要素です。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 。 オーバー ロードを返しますが<xref:System.Collections.Generic.IEnumerable%601><xref:System.Xml.Linq.XElement>、指定した<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>がある子要素</xref:System.Xml.Linq.XElement>の</xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName>|返します、<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XElement>のこの要素の後にある要素。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 。 オーバー ロードを返しますが<xref:System.Collections.Generic.IEnumerable%601><xref:System.Xml.Linq.XElement>、指定した<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>があるこの要素の後に要素</xref:System.Xml.Linq.XElement>の</xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>|返します、<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XElement>のこの要素の前にある要素。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 。 <xref:System.Collections.Generic.IEnumerable%601><xref:System.Xml.Linq.XElement>この要素を指定した<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>を持つ前にある要素</xref:System.Xml.Linq.XElement>の</xref:System.Collections.Generic.IEnumerable%601>オーバー ロードを返します|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName>|返します、<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XElement>この要素とその祖先の。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 。 オーバー ロードを返しますが<xref:System.Collections.Generic.IEnumerable%601><xref:System.Xml.Linq.XElement>、指定した<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>がある要素</xref:System.Xml.Linq.XElement>の</xref:System.Collections.Generic.IEnumerable%601>|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName>|返します、<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XElement>この要素とその子孫の。</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 。 オーバー ロードを返しますが<xref:System.Collections.Generic.IEnumerable%601><xref:System.Xml.Linq.XElement>、指定した<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>がある要素</xref:System.Xml.Linq.XElement>の</xref:System.Collections.Generic.IEnumerable%601>|  
  
## <a name="method-for-retrieving-a-single-element"></a>1 つの要素を取得するメソッド  
 次のメソッドから&1; つの子の取得、<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>|最初の子<xref:System.Xml.Linq.XElement>を持つ指定した<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>オブジェクト</xref:System.Xml.Linq.XElement>を返します|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>属性のコレクションを取得するメソッド  
 次のメソッドからの属性を取得、<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName>|返します、<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XAttribute>のすべての属性。</xref:System.Xml.Linq.XAttribute> </xref:System.Collections.Generic.IEnumerable%601> 。|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>1 つの属性を取得するメソッド  
 次のメソッドから&1; つの属性の取得、<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>|<xref:System.Xml.Linq.XAttribute>指定した<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>を持つ</xref:System.Xml.Linq.XAttribute>を返します|  
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML 軸 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
