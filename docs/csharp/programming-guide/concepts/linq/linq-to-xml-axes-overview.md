---
title: "LINQ to XML 軸の概要 (C#) | Microsoft Docs"
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
ms.assetid: 516792fb-461d-40a8-8a50-9993a51258fc
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b43d3cb5cc7154c1133c5fa17e5bdacca97a38c9
ms.lasthandoff: 03/13/2017


---
# <a name="linq-to-xml-axes-overview-c"></a>LINQ to XML 軸の概要 (C#)
XML ツリーを作成した後、または XML ドキュメントを XML ツリーに読み込んだ後は、クエリを実行して要素や属性を調べたり、その値を取得したりできます。 コレクションの取得には、*軸メソッド* (*軸*とも呼ぶ) を使用します。 一部の軸は、<xref:System.Collections.Generic.IEnumerable%601> コレクションを返す <xref:System.Xml.Linq.XElement> クラスおよび <xref:System.Xml.Linq.XDocument> クラスのメソッドです。 一部の軸は <xref:System.Xml.Linq.Extensions> クラスの拡張メソッドです。 拡張メソッドとして実装されている軸は、コレクションに対して機能し、コレクションを返します。  
  
 「[XElement クラスの概要](http://msdn.microsoft.com/library/d35180fe-7016-4895-9bfc-ba1e3f7875ec)」で説明しているように、<xref:System.Xml.Linq.XElement> オブジェクトは単一の要素ノードを表します。 要素のコンテンツは、複合要素 (構造化コンテンツとも呼ばれる) または単純要素です。 単純要素は、空の場合と値を含む場合があります。 ノードに構造化コンテンツが含まれている場合、さまざまな軸メソッドを使用して子孫要素の列挙を取得できます。 最もよく使用される軸メソッドは、<xref:System.Xml.Linq.XContainer.Elements%2A> と <xref:System.Xml.Linq.XContainer.Descendants%2A> です。  
  
 コレクションを返す軸メソッド以外に、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クエリでよく使用されるメソッドが 2 つあります。 <xref:System.Xml.Linq.XContainer.Element%2A> メソッドは、1 つの <xref:System.Xml.Linq.XElement> を返します。 <xref:System.Xml.Linq.XElement.Attribute%2A> メソッドは、1 つの <xref:System.Xml.Linq.XAttribute> を返します。  
  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリは多くの用途において、ツリーを調べてデータを抽出し、それを変換する方法として最も強力です。 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリは <xref:System.Collections.Generic.IEnumerable%601> を実装するオブジェクトを操作し、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 軸は <xref:System.Xml.Linq.XElement>コレクションの <xref:System.Collections.Generic.IEnumerable%601> と <xref:System.Xml.Linq.XAttribute> コレクションの <xref:System.Collections.Generic.IEnumerable%601> を返します。 クエリを実行するには、これらのコレクションが必要です。  
  
 要素と属性のコレクションを取得する軸メソッドに加えて、ツリーを詳細に反復処理するための軸メソッドもあります。 たとえば、要素と属性を処理する代わりに、ツリーのノードを操作できます。 ノードは、要素や属性よりも細かい粒度レベルです。 ノードの操作時には、XML コメント、テキスト ノード、処理命令などを調べることができます。 この機能は、たとえば、文書を XML として保存できるワード プロセッサを作成する場合に重要です。 ただし、大多数の XML プログラマが主に扱うのは、要素、属性、およびその値です。  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>要素のコレクションを取得するメソッド  
 <xref:System.Xml.Linq.XElement> で呼び出して要素のコレクションを返す <xref:System.Xml.Linq.XElement> クラス (またはその基本クラス) のメソッドを、次にまとめて示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName>|この要素の先祖の <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> を返します。 オーバーロードでは、指定された <xref:System.Xml.Linq.XName> を持つ先祖の <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> を返します。|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName>|この要素の子孫の <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> を返します。 オーバーロードでは、指定された <xref:System.Xml.Linq.XName> を持つ子孫の <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> を返します。|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>|この要素の子要素の <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> を返します。 オーバーロードでは、指定された <xref:System.Xml.Linq.XName> を持つ子要素の <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> を返します。|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName>|この要素の後に続く要素の <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> を返します。 オーバーロードでは、指定された <xref:System.Xml.Linq.XName> を持つ要素の後に続く要素の <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> を返します。|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>|この要素に先立つ要素の <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> を返します。 オーバーロードでは、指定された <xref:System.Xml.Linq.XName> を持つ要素に先立つ要素の <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> を返します。|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName>|この要素とその先祖の <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> を返します。 オーバーロードでは、指定された <xref:System.Xml.Linq.XName> を持つ要素の <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> を返します。|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName>|この要素とその子孫の <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> を返します。 オーバーロードでは、指定された <xref:System.Xml.Linq.XName> を持つ要素の <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> を返します。|  
  
## <a name="method-for-retrieving-a-single-element"></a>1 つの要素を取得するメソッド  
 次のメソッドは、<xref:System.Xml.Linq.XElement> オブジェクトから 1 つの子を取得します。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>|指定された <xref:System.Xml.Linq.XName> を持つ最初の子 <xref:System.Xml.Linq.XElement> オブジェクトを返します。|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>属性のコレクションを取得するメソッド  
 次のメソッドは、<xref:System.Xml.Linq.XElement> オブジェクトから属性を取得します。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName>|すべての属性の <xref:System.Xml.Linq.XAttribute> の <xref:System.Collections.Generic.IEnumerable%601> を返します。|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>1 つの属性を取得するメソッド  
 次のメソッドは、<xref:System.Xml.Linq.XElement> オブジェクトから 1 つの属性を取得します。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>|指定された <xref:System.Xml.Linq.XName> を持つ <xref:System.Xml.Linq.XAttribute> を返します。|  
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML 軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
