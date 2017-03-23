---
title: "XML リテラルの概要 (Visual Basic) |Microsoft ドキュメント"
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
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 57d036910ba9e49385caca28de222a8a8e28ec56
ms.lasthandoff: 03/13/2017

---
# <a name="xml-literals-overview-visual-basic"></a>XML リテラルの概要 (Visual Basic)
*XML リテラル*に直接 XML を組み込むことができます、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コードです。 XML リテラルの構文を表す[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]オブジェクト、およびそれには、XML 1.0 の構文に似ています。 これにより、コード、最終的な XML と同じ構造では、XML 要素やドキュメントをプログラムで作成が簡単にします。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]XML リテラルをコンパイル[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]オブジェクトです。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]作成して、XML を操作するための簡単なオブジェクト モデルとこのモデルとも統合されて提供[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]します。 詳細については、 <xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>を参照してください。  
  
 埋め込むことができます、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] XML リテラル内の式。 アプリケーションの作成、実行時に、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]オブジェクト リテラルごとに、埋め込まれた式の値を組み込むことにします。 これにより、XML リテラルの中の動的なコンテンツを指定できます。 詳細については、次を参照してください。 [XML での埋め込み式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)します。  
  
 XML リテラルの構文と XML 1.0 の構文の違いについての詳細については、次を参照してください。 [XML リテラルと XML 1.0 仕様](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)します。  
  
## <a name="simple-literals"></a>単純なリテラル  
 作成することができます、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]内のオブジェクト、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コードを入力するか、有効な XML に貼り付けることです。 リテラル XML 要素を返します、<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。 詳細については、次を参照してください。 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)と[XML リテラルと XML 1.0 仕様](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)します。 次の例では、いくつかの子要素を持つ XML 要素を作成します。  
  
 [!code-vb[VbXMLSamples&#5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_1.vb)]  
  
 XML ドキュメントを作成して、XML リテラルを開始できます`<?xml version="1.0"?>`の次の例に示すようにします。 XML ドキュメント リテラル返します、<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument>。 詳細については、次を参照してください。 [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)します。  
  
 [!code-vb[VbXMLSamples&6;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
> [!NOTE]
>  XML リテラルの構文で[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]XML 1.0 仕様で構文と同じではありません。 詳細については、次を参照してください。 [XML リテラルと XML 1.0 仕様](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)します。  
  
## <a name="line-continuation"></a>行の連結  
 XML リテラルは、行継続文字 (空白のアンダー スコアを入力してシーケンス) を使用することがなく複数行にまたがることができます。 これにより、簡単に XML ドキュメントをコード内の XML リテラルを比較します。  
  
 コンパイラは、XML リテラルの一部として、行継続文字を処理します。 属している場合にのみに領域アンダー スコアを入力シーケンスを使用する必要がありますので、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]オブジェクトです。  
  
 ただし、組み込み式に複数の行がある場合は、行継続文字を必要操作を行います。 詳細については、次を参照してください。 [XML での埋め込み式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)します。  
  
## <a name="embedding-queries-in-xml-literals"></a>XML リテラルでクエリの埋め込み  
 組み込み式では、クエリを使用できます。 これを行うときに、クエリによって返される要素が XML 要素に追加されます。 これにより、XML リテラルに、ユーザーのクエリの結果などの動的コンテンツを追加できます。  
  
 メンバーからの XML 要素を作成する次のコードが埋め込まれたクエリを使用するなど、`phoneNumbers2`配列をそれらの要素の子として追加`contact2`します。  
  
 [!code-vb[VbXMLSamples&#7;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_3.vb)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>コンパイラが XML リテラルからオブジェクトを作成する方法  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでは、XML リテラルを変換と同等の呼び出しに[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]を構築するコンス トラクター、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]オブジェクトです。 たとえば、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラを使用して、次のコード例をへの呼び出しに変換されます、 <xref:System.Xml.Linq.XProcessingInstruction>XML バージョン手順では、コンス トラクターを呼び出し、<xref:System.Xml.Linq.XElement>のコンス トラクター、 `<contact>`、`<name>`と`<phone>`要素、およびへの呼び出し、<xref:System.Xml.Linq.XAttribute>のコンス トラクター、`type`属性</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XProcessingInstruction>。 具体的には、次のサンプルでは、属性から得られる、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラが呼び出す、<xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29>コンス トラクターを&2; 回クリックします</xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29>。 最初は値を渡す`type`の`name`パラメーターと値の`home`の`value`パラメーター。 2 つ目は、値を渡すも`type`の`name`パラメーターが、値`work`の`value`パラメーター。  
  
 [!code-vb[VbXMLSamples&6;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XElement>   
 [Visual Basic で XML を作成します。](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML での埋め込み式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)
