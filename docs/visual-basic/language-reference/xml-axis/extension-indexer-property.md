---
title: "拡張インデクサー プロパティ (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 99d14b6e54a59ffc904a9e786c22498d23ee8ab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="extension-indexer-property-visual-basic"></a>拡張インデクサー プロパティ (Visual Basic)
コレクション内の個々の要素にアクセスできます。  
  
## <a name="syntax"></a>構文  
  
```  
object(index)  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`object`|必須です。 クエリ可能なコレクションです。 実装するコレクションである、<xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Linq.IQueryable%601>です。|  
|(|必ず指定します。 インデクサー プロパティの開始を示します。|  
|`index`|必須です。 コレクションの要素の 0 から始まる位置を示す整数式。|  
|)|必ず指定します。 インデクサー プロパティの終了を示します。|  
  
## <a name="return-value"></a>戻り値  
 コレクション内の指定された場所からオブジェクトまたは`Nothing`場合は、インデックスが範囲外です。  
  
## <a name="remarks"></a>コメント  
 拡張インデクサー プロパティを使用して、コレクション内の個々 の要素にアクセスすることができます。 このインデクサー プロパティは、通常の出力 XML 軸プロパティの使用です。 XML 子と XML 子孫軸プロパティのコレクションを返す<xref:System.Xml.Linq.XElement>オブジェクトまたは属性の値。  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コンパイラでは、拡張機能インデクサー プロパティを変換への呼び出しを`ElementAtOrDefault`メソッドです。 配列インデクサーとは異なり、`ElementAtOrDefault`メソッドを返します。`Nothing`場合は、インデックスが範囲外です。 この動作は、コレクション内の要素の数を容易に判別できない場合に便利です。  
  
 実装するコレクションの拡張機能プロパティのように、このインデクサー プロパティは<xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Linq.IQueryable%601>: コレクションは、インデクサーまたは既定のプロパティを持たない場合にのみ使用されます。  
  
 コレクションの最初の要素の値にアクセスする<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XAttribute>オブジェクト、XML を使用する`Value`プロパティです。 詳細については、次を参照してください。 [XML Value プロパティ](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)です。  
  
## <a name="example"></a>例  
 次の例は、拡張機能インデクサーを使用して、2 番目の子ノードのコレクションにアクセスする方法を示しています。<xref:System.Xml.Linq.XElement>オブジェクト。 コレクションには、すべての子要素がという名前を取得する子軸プロパティを使用してアクセス`phone`で、`contact`オブジェクト。  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XElement>  
 [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML Value プロパティ](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
