---
title: "XElement オブジェクトと XDocument Objects2 の有効なコンテンツ |Microsoft ドキュメント"
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
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f752ae346167709b95e758d15c1785ba7b6fcc5f
ms.lasthandoff: 03/13/2017

---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>XElement オブジェクトと XDocument オブジェクトの有効なコンテンツ
ここでは、コンストラクターやメソッドに渡すことができる有効な引数について説明します。これらのコンストラクターやメソッドは、コンテンツを要素やドキュメントに追加するためのものです。  
  
## <a name="valid-content"></a>有効なコンテンツ  
 クエリは多くの場合、<xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Xml.Linq.XElement><xref:System.Collections.Generic.IEnumerable%601><xref:System.Xml.Linq.XAttribute>。</xref:System.Xml.Linq.XAttribute></xref:System.Collections.Generic.IEnumerable%601></xref:System.Xml.Linq.XElement></xref:System.Collections.Generic.IEnumerable%601>に評価されます。 コレクションを渡すことができます<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XAttribute>オブジェクトを<xref:System.Xml.Linq.XElement>コンス トラクター</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> 。 したがって、XML ツリーの設定に使用するメソッドとコンストラクターに対して、クエリの結果をコンテンツとして渡すと便利です。  
  
 単純コンテンツを追加するときに、さまざまな型をこのメソッドに渡すことができます。 有効な型は、次のとおりです。  
  
-   <xref:System.String></xref:System.String>  
  
-   <xref:System.Double></xref:System.Double>  
  
-   <xref:System.Single></xref:System.Single>  
  
-   <xref:System.Decimal></xref:System.Decimal>  
  
-   <xref:System.Boolean></xref:System.Boolean>  
  
-   <xref:System.DateTime></xref:System.DateTime>  
  
-   <xref:System.TimeSpan></xref:System.TimeSpan>  
  
-   <xref:System.DateTimeOffset></xref:System.DateTimeOffset>  
  
-   `Object.ToString` を実装する任意の型  
  
-   <xref:System.Collections.Generic.IEnumerable%601>。</xref:System.Collections.Generic.IEnumerable%601>を実装する任意の型  
  
 複合コンテンツを追加するときは、次のような型をこのメソッドに渡すことができます。  
  
-   <xref:System.Xml.Linq.XObject></xref:System.Xml.Linq.XObject>  
  
-   <xref:System.Xml.Linq.XNode></xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XAttribute>  
  
-   実装する任意の型<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>  
  
 オブジェクトを実装する場合<xref:System.Collections.Generic.IEnumerable%601>、オブジェクトのコレクションが列挙され、コレクション内のすべての項目が追加されます</xref:System.Collections.Generic.IEnumerable%601>。 コレクションに含まれる場合<xref:System.Xml.Linq.XNode>または<xref:System.Xml.Linq.XAttribute>オブジェクト、コレクション内の各アイテムは個別に追加されます</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XNode>。 コレクションにテキスト (またはテキストに変換されるオブジェクト) が含まれている場合、コレクション内のテキストが連結され、1 つのテキスト ノードとして追加されます。  
  
 コンテンツが `null` の場合は、何も追加されません。 コレクションを渡すとき、コレクション内の項目は `null` にできます。 コレクション内の `null` 項目は、ツリーに影響を与えません。  
  
 追加する属性の名前は、そのコンテナー要素内で一意であることが必要です。  
  
 追加するときに<xref:System.Xml.Linq.XNode>または<xref:System.Xml.Linq.XAttribute>オブジェクトの場合、新しいコンテンツに親があるない場合、オブジェクトは単に、XML ツリーにアタッチします</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XNode>。 新しいコンテンツに既に親があり、別の XML ツリーの一部となっている場合は、新しいコンテンツが複製され、新しく複製されたコンテンツが XML ツリーにアタッチされます。  
  
## <a name="valid-content-for-documents"></a>ドキュメントの有効なコンテンツ  
 属性と単純コンテンツをドキュメントに追加することはできません。  
  
 <xref:System.Xml.Linq.XDocument>。</xref:System.Xml.Linq.XDocument>を作成する必要がある多くのシナリオはありません。 代わりに、使用して XML ツリー作成通常、<xref:System.Xml.Linq.XElement>ルート ノードです</xref:System.Xml.Linq.XElement>。 しない限り、ドキュメントを作成 (たとえば、最上位のレベルでは、処理命令とコメントを作成する必要があるまたはドキュメント型をサポートする必要がある) する特定の要件がある、方が容易に<xref:System.Xml.Linq.XElement>ルート ノードとして</xref:System.Xml.Linq.XElement>。  
  
 ドキュメントの有効なコンテンツは次のとおりです。  
  
-   0 または&1; 個<xref:System.Xml.Linq.XDocumentType>オブジェクト</xref:System.Xml.Linq.XDocumentType>。 ドキュメントの型は、要素の前に置く必要があります。  
  
-   0 個または&1; 個の要素。  
  
-   0 個以上のコメント。  
  
-   0 個以上の処理命令。  
  
-   空白のみを含む、0 個以上のテキスト ノード。  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>コンテンツの追加が可能なコンストラクターと関数  
 次の方法では、子コンテンツへの追加<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>::</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>できます。  
  
|メソッド|説明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A></xref:System.Xml.Linq.XElement.%23ctor%2A>|<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>の構築します。|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A></xref:System.Xml.Linq.XDocument.%23ctor%2A>|<xref:System.Xml.Linq.XDocument>。</xref:System.Xml.Linq.XDocument>の構築します。|  
|<xref:System.Xml.Linq.XContainer.Add%2A></xref:System.Xml.Linq.XContainer.Add%2A>|<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>の子コンテンツの末尾に追加します。|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A></xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<xref:System.Xml.Linq.XNode>。</xref:System.Xml.Linq.XNode>後にコンテンツを追加します。|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<xref:System.Xml.Linq.XNode>。</xref:System.Xml.Linq.XNode>する前にコンテンツを追加します。|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A></xref:System.Xml.Linq.XContainer.AddFirst%2A>|<xref:System.Xml.Linq.XContainer>。</xref:System.Xml.Linq.XContainer>の子コンテンツの冒頭にコンテンツを追加します。|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A></xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>のすべてのコンテンツ (子ノードおよび属性) を置き換えます|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A></xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>属性に置き換えられます|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A></xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|子ノードを新しいコンテンツに置き換えます。|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A></xref:System.Xml.Linq.XNode.ReplaceWith%2A>|ノードを新しいコンテンツに置き換えます。|  
  
## <a name="see-also"></a>関連項目  
 [XML ツリー (Visual Basic) の作成](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
