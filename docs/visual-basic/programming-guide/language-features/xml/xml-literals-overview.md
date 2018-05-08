---
title: XML リテラルの概要 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: 03fc8c11b5553c9c3a63bdcb69bf6135050e2c89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="xml-literals-overview-visual-basic"></a>XML リテラルの概要 (Visual Basic)
*XML リテラル*XML を Visual Basic のコードに直接組み込むことができます。 XML リテラルの構文を表します[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト、およびそれには、XML 1.0 の構文に似ています。 これにより、簡単に、コードが、最終的な XML と同じ構造を有して XML 要素やドキュメントをプログラムで作成します。  
  
 Visual Basic XML リテラルをコンパイルする[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 密接に連携、統合、単純なオブジェクト モデルの作成と、XML を操作し、このモデルを提供[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]です。 詳細については、「<xref:System.Xml.Linq.XElement>」を参照してください。  
  
 XML リテラル Visual Basic の式を埋め込むことができます。 アプリケーションを作成、実行時に、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]リテラルごとに埋め込み式の値を組み込むためのオブジェクト。 これにより、XML リテラル内の動的なコンテンツを指定できます。 詳細については、次を参照してください。 [XML での埋め込み式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)です。  
  
 XML リテラルの構文と XML 1.0 の構文の違いの詳細については、次を参照してください。 [XML リテラルと XML 1.0 仕様](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)です。  
  
## <a name="simple-literals"></a>単純なリテラル  
 作成することができます、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]入力するか、有効な XML に貼り付けることによって、Visual Basic コード内のオブジェクト。 リテラル XML 要素を返します、<xref:System.Xml.Linq.XElement>オブジェクト。 詳細については、次を参照してください。 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)と[XML リテラルと XML 1.0 仕様](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)です。 次の例では、いくつかの子要素を持つ XML 要素を作成します。  
  
 [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_1.vb)]  
  
 XML ドキュメントを作成するには、XML リテラルでを起動して`<?xml version="1.0"?>`の次の例に示すようにします。 XML ドキュメント リテラルを返します、<xref:System.Xml.Linq.XDocument>オブジェクト。 詳細については、次を参照してください。 [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)です。  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
> [!NOTE]
>  Visual Basic で XML リテラルの構文は、XML 1.0 仕様で構文と同じではないです。 詳細については、次を参照してください。 [XML リテラルと XML 1.0 仕様](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)です。  
  
## <a name="line-continuation"></a>行の連結  
 XML リテラルは、行継続文字 (空白-アンダー スコアを入力してシーケンス) を使用することがなく複数行にまたがることができます。 これにより、XML リテラルの XML ドキュメントのコードで簡単に比較します。  
  
 コンパイラは、XML リテラルの一部として行継続文字を処理します。 属している場合にのみ領域アンダー スコアを入力シーケンスを使用する必要がありますので、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト。  
  
 ただし、組み込み式に複数の行がある場合は、行継続文字を必要しないでください。 詳細については、次を参照してください。 [XML での埋め込み式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)です。  
  
## <a name="embedding-queries-in-xml-literals"></a>XML リテラルでクエリの埋め込み  
 埋め込み式の中では、クエリを使用することができます。 これを行うときに、クエリによって返される要素が XML 要素に追加されます。 これにより、XML リテラルに、ユーザーのクエリの結果などの動的なコンテンツを追加できます。  
  
 次のコードがのメンバーからの XML 要素を作成する埋め込みクエリを使用するなど、`phoneNumbers2`配列し、それらの要素を追加してからの子として`contact2`です。  
  
 [!code-vb[VbXMLSamples#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_3.vb)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>コンパイラが XML リテラルからオブジェクトを作成する方法  
 Visual Basic コンパイラは、該当するショートカットへの呼び出しに XML リテラルを変換[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]を構築するコンス トラクター、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト。 たとえば、Visual Basic コンパイラは、変換次のコード例への呼び出しに、 <xref:System.Xml.Linq.XProcessingInstruction> XML バージョン命令のコンス トラクターを呼び出し、<xref:System.Xml.Linq.XElement>のコンス トラクター、 `<contact>`、 `<name>`、および`<phone>`要素、およびへの呼び出し、<xref:System.Xml.Linq.XAttribute>のコンス トラクター、`type`属性。 具体的には、属性を指定すると、次のサンプルでは、Visual Basic コンパイラが呼び出す、<xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29>コンス トラクターを 2 回クリックします。 1 つ目は、値を渡す`type`の`name`パラメーターと値を`home`の`value`パラメーター。 2 つ目は、値を渡すも`type`の`name`パラメーターは、値`work`の`value`パラメーター。  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XElement>  
 [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML での埋め込み式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)
