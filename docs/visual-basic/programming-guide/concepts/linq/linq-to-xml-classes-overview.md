---
title: "LINQ to XML クラスの概要 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: f11b62b5-d522-4c23-92ae-23186dc16447
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
ms.openlocfilehash: 12885f93bb7e56dd66d36090d41700195313e944
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-classes-overview-visual-basic"></a>LINQ to XML クラスの概要 (Visual Basic)
このトピックの一覧を提供する、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]内のクラス、<xref:System.Xml.Linq>名前空間、およびそれぞれの簡単な説明</xref:System.Xml.Linq>。  
  
## <a name="linq-to-xml-classes"></a>LINQ to XML クラス  
  
### <a name="xattribute-class"></a>XAttribute クラス  
 <xref:System.Xml.Linq.XAttribute>XML 属性を表します。</xref:System.Xml.Linq.XAttribute> 詳細な情報と例については、次を参照してください。 [XAttribute クラスの概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md)します。  
  
### <a name="xcdata-class"></a>XCData クラス  
 <xref:System.Xml.Linq.XCData>CDATA テキスト ノードを表します。</xref:System.Xml.Linq.XCData>  
  
### <a name="xcomment-class"></a>XComment クラス  
 <xref:System.Xml.Linq.XComment>XML コメントを表します。</xref:System.Xml.Linq.XComment>  
  
### <a name="xcontainer-class"></a>XContainer クラス  
 <xref:System.Xml.Linq.XContainer>子ノードを持つすべてのノードの抽象の基本クラスです。</xref:System.Xml.Linq.XContainer> 次のクラスから派生、<xref:System.Xml.Linq.XContainer>クラス:</xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XElement>  
  
-   <xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>XDeclaration クラス  
 <xref:System.Xml.Linq.XDeclaration>XML 宣言を表します。</xref:System.Xml.Linq.XDeclaration> XML 宣言は、ドキュメントの XML バージョンとエンコーディングを宣言するために使用されます。 また、XML 宣言では、XML ドキュメントがスタンドアロンかどうかを指定します。 ドキュメントがスタンドアロンである場合、外部 DTD、または内部サブセットから参照されている外部パラメーター エンティティのいずれかに外部マークアップ宣言がありません。  
  
### <a name="xdocument-class"></a>XDocument クラス  
 <xref:System.Xml.Linq.XDocument>XML ドキュメントを表します。</xref:System.Xml.Linq.XDocument> 詳細な情報と例については、次を参照してください。 [XDocument クラスの概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md)します。  
  
### <a name="xdocumenttype-class"></a>XDocumentType クラス  
 <xref:System.Xml.Linq.XDocumentType>XML ドキュメント型定義 (DTD) を表します。</xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xelement-class"></a>XElement クラス  
 <xref:System.Xml.Linq.XElement>XML 要素を表します。</xref:System.Xml.Linq.XElement> 詳細な情報と例については、次を参照してください。 [XElement クラスの概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md)します。  
  
### <a name="xname-class"></a>XName クラス  
 <xref:System.Xml.Linq.XName>要素の名前を表します (<xref:System.Xml.Linq.XElement>) と属性 (<xref:System.Xml.Linq.XAttribute>).</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XName> 詳細な情報と例については、次を参照してください。 [XDocument クラスの概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md)します。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] は、XML 名ができる限り単純になるように設計されています。 XML 名は、その複雑さのために XML の高度な領域として扱われることがよくあります。 この複雑さの原因として考えられるのは、開発者がプログラミングで通常使用する名前空間ではなく、名前空間プレフィックスです。 名前空間プレフィックスは、XML を入力するときに必要なキー ストロークを減らしたり、XML を読みやすくしたりするために役立ちます。 ただし、プレフィックスは、多くの場合、完全な XML 名前空間を使用するためのショートカットに過ぎないと、ほとんどの場合必要はありません。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]すべてのプレフィックスを対応する XML 名前空間に解決することによって XML の名前を簡単になります。 プレフィックスは次の場合は必須では、を通じて使用可能な<xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A>メソッド</xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A>。  
  
 必要に応じて名前空間プレフィックスを制御することができます。 XSLT や XAML などの他の XML システムを使用する場合は、状況によって名前空間プレフィックスを制御する必要があります。 たとえば、名前空間プレフィックスを使用し、XSLT スタイルシートに組み込まれている XPath 式がある場合は、XPath 式内で使用しているものと一致する名前空間プレフィックスで XML ドキュメントがシリアル化されるようにする必要があります。  
  
### <a name="xnamespace-class"></a>XNamespace クラス  
 <xref:System.Xml.Linq.XNamespace><xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement>名前空間を表します</xref:System.Xml.Linq.XNamespace> 名前空間は、 <xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>コンポーネント  
  
### <a name="xnode-class"></a>XNode クラス  
 <xref:System.Xml.Linq.XNode>XML ツリーのノードを表す抽象クラスです。</xref:System.Xml.Linq.XNode> 次のクラスから派生、<xref:System.Xml.Linq.XNode>クラス:</xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XText></xref:System.Xml.Linq.XText>  
  
-   <xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment>  
  
-   <xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction>  
  
-   <xref:System.Xml.Linq.XDocumentType></xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>XNodeDocumentOrderComparer クラス  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer>ノードをドキュメント順で比較する機能を提供します。</xref:System.Xml.Linq.XNodeDocumentOrderComparer>  
  
### <a name="xnodeequalitycomparer-class"></a>XNodeEqualityComparer クラス  
 <xref:System.Xml.Linq.XNodeEqualityComparer>ノードの値の等価性を比較する機能を提供します。</xref:System.Xml.Linq.XNodeEqualityComparer>  
  
### <a name="xobject-class"></a>XObject クラス  
 <xref:System.Xml.Linq.XObject><xref:System.Xml.Linq.XNode> <xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XNode>の抽象基本クラスは、します。</xref:System.Xml.Linq.XObject> このクラスには、注釈およびイベント機能が用意されています。  
  
### <a name="xobjectchange-class"></a>XObjectChange クラス  
 <xref:System.Xml.Linq.XObjectChange><xref:System.Xml.Linq.XObject>。</xref:System.Xml.Linq.XObject>イベントが発生したときに、イベントの種類を指定します。</xref:System.Xml.Linq.XObjectChange>  
  
### <a name="xobjectchangeeventargs-class"></a>XObjectChangeEventArgs クラス  
 <xref:System.Xml.Linq.XObjectChangeEventArgs>データを提供、<xref:System.Xml.Linq.XObject.Changing>と<xref:System.Xml.Linq.XObject.Changed>イベント</xref:System.Xml.Linq.XObject.Changed></xref:System.Xml.Linq.XObject.Changing>。</xref:System.Xml.Linq.XObjectChangeEventArgs>  
  
### <a name="xprocessinginstruction-class"></a>XProcessingInstruction クラス  
 <xref:System.Xml.Linq.XProcessingInstruction>XML 処理命令を表します。</xref:System.Xml.Linq.XProcessingInstruction> 処理命令は、XML を処理するアプリケーションに情報を伝達します。  
  
### <a name="xtext-class"></a>XText クラス  
 <xref:System.Xml.Linq.XText>テキスト ノードを表します。</xref:System.Xml.Linq.XText> このクラスを使用する必要はほとんどありません。 このクラスは、主に混合コンテンツに使用されます。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML プログラミングの概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
