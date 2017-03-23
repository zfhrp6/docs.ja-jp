---
title: "方法: XmlReader (Visual Basic の場合) からの XML フラグメントをストリーム出力 |Microsoft ドキュメント"
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
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
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
ms.openlocfilehash: c9c60bb4730ef6569390f76f63c40a2cbd1c9524
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a>方法: XML フラグメントをストリームから XmlReader (Visual Basic)
大きな XML ファイルを処理する必要があるときに、XML ツリー全体をメモリに読み込むことができない場合があります。 このトピックは、 <xref:System.Xml.XmlReader>。</xref:System.Xml.XmlReader>を使用してフラグメントをストリーム出力する方法を示しています。  
  
 使用する最も効果的な方法のいずれか、<xref:System.Xml.XmlReader>を読み取る<xref:System.Xml.Linq.XElement>オブジェクト、独自のカスタムの軸メソッドを作成する方法です</xref:System.Xml.Linq.XElement></xref:System.Xml.XmlReader>。 軸メソッド通常コレクションを返しますなど<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XElement>、このトピックの例のように、</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 。 カスタムの軸メソッドを呼び出して XML フラグメントを作成した後で、<xref:System.Xml.Linq.XNode.ReadFrom%2A>メソッドを使用してコレクションを返す`yield return`</xref:System.Xml.Linq.XNode.ReadFrom%2A>。 これにより、カスタムの軸メソッドに遅延実行セマンティクスが付加されます。  
  
 XML ツリーを作成する場合、<xref:System.Xml.XmlReader>オブジェクト、<xref:System.Xml.XmlReader>要素に配置する必要があります</xref:System.Xml.XmlReader></xref:System.Xml.XmlReader>。 <xref:System.Xml.Linq.XNode.ReadFrom%2A>は、要素の終了タグを読み取るまで、メソッドは返されません</xref:System.Xml.Linq.XNode.ReadFrom%2A>。  
  
 部分ツリーを作成する場合は、インスタンスを作成できる、<xref:System.Xml.XmlReader>に変換するノードのリーダーを配置し、<xref:System.Xml.Linq.XElement>ツリーし、作成、<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement></xref:System.Xml.XmlReader>。  
  
 トピック[方法: ヘッダー情報 (Visual Basic) にアクセスして XML フラグメントをストリーム](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)情報より複雑なドキュメントをストリームする方法の例が含まれています。  
  
 トピック[方法: 実行のストリーミング変換の大きな XML ドキュメント (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md)最小メモリ量を低く抑えながら非常に大きな XML ドキュメントに変換する LINQ to XML の使用例が含まれています。  
  
## <a name="example"></a>例  
 次の例では、カスタムの軸メソッドを作成します。 このメソッドに対してクエリを実行するには、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリを使用します。 カスタムの軸メソッド `StreamRootChildDoc` は、`Child` 要素が繰り返し出現するドキュメントを読み取るために特に設計されたメソッドです。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 この例を実行すると、次の出力が生成されます。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 この例のソース ドキュメントは、非常に小さなドキュメントです。 ただし、何百万の `Child` 要素があっても、この例で使用されるメモリは非常に少量です。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: Visual Basic での IEnumerable(Of T) の実装](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)   
 [(Visual Basic) の XML の解析](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
