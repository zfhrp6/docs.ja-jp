---
title: "Visual Basic における LINQ to XML の概要 |Microsoft ドキュメント"
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
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
caps.latest.revision: 17
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
ms.openlocfilehash: 508d4a97b0636f10607326eb35c4c5d8c7860873
ms.lasthandoff: 03/13/2017

---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visual Basic における LINQ to XML の概要
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]サポートを提供[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]XML リテラルと XML 軸プロパティです。 これにより、内の XML を操作するための使い慣れた便利な構文を使用して、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コードです。 *XML リテラル*XML をコード内で直接有効にします。 *XML 軸プロパティ*access 子ノードが、子孫ノードは、XML リテラルの属性に有効にします。 詳細については、次を参照してください。 [XML リテラルの概要](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)と[Visual Basic における XML のへのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)します。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]メモリ内 XML プログラミング API を利用するには、特別に設計された[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]します。 呼び出すことができますが、 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] Api を直接のみ[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]XML リテラルを宣言し、XML 軸プロパティに直接アクセスすることができます。  
  
> [!NOTE]
>  ASP.NET ページ内の宣言型コードでは、XML リテラルと XML 軸プロパティがサポートされていません。 Visual Basic の XML の機能を使用するには、コードを ASP.NET アプリケーションでは分離コード ページに配置します。  
  
 ![ビデオへのリンク](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo")関連のビデオ デモンストレーションでは、次を参照してください。 [LINQ to XML の使用方法ですか?](http://go.microsoft.com/fwlink/?LinkId=143034)と[LINQ to XML を使用して作成する Excel ワークシートの操作方法?](http://go.microsoft.com/fwlink/?LinkId=143536)します。  
  
## <a name="creating-xml"></a>XML を作成します。  
 2 つの方法で XML ツリーを作成する[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]です。 直接コードでは、リテラル XML を宣言することができますか、使用して、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]ツリーを作成する Api。 両方のプロセスには、XML ツリーの最後の構造を反映するようにコードが有効にします。 たとえば、次のコード例では、XML 要素を作成します。  
  
 [!code-vb[VbXmlSamples&#5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]  
  
 詳細については、次を参照してください。 [Visual Basic における XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)します。  
  
## <a name="accessing-and-navigating-xml"></a>アクセスして、XML 内の移動  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]アクセスと、XML 構造を移動するには、XML 軸プロパティを提供します。 これらのプロパティを使用すると、XML 子要素の名前を指定することによって XML 要素と属性にアクセスできます。 また、明示的に呼び出せる、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]内の移動および要素と属性を検索するためのメソッドです。 たとえば、次のコード例は XML 軸プロパティを使用して、属性および XML 要素の子要素を参照してください。 コード例では、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]子要素を取得し、それらを効率的に変換を実行する XML 要素として出力をクエリします。  
  
 [!code-vb[VbXmlSamples&#8;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]  
  
 詳細については、次を参照してください。 [Visual Basic における XML のへのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)します。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]使用してグローバル XML 名前空間のエイリアスを指定することができます、`Imports`ステートメントです。 次の例では、使用する方法、 `Imports` XML 名前空間をインポートするステートメント。  
  
 [!code-vb[VbXMLSamples&#1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]  
  
 XML 軸プロパティにアクセスし、XML ドキュメントと要素の XML リテラルを宣言する場合は、XML 名前空間の別名を使用できます。  
  
 取得することができます、<xref:System.Xml.Linq.XNamespace>を使用して特定の名前空間プレフィックスのオブジェクト、 [GetXmlNamespace 演算子](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)</xref:System.Xml.Linq.XNamespace>。  
  
 詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)します。  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>XML リテラルでの XML 名前空間の使用  
 次の例では、作成する方法、<xref:System.Xml.Linq.XElement>グローバル名前空間を使用するオブジェクト`ns`:</xref:System.Xml.Linq.XElement>  
  
 [!code-vb[VbXMLSamples&#2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラで XML 名前空間を使用するための XML 表記を使用する同等のコードを XML 名前空間エイリアスを含む XML リテラルを変換する、`xmlns`属性です。 コンパイルされると、前のセクションの例のコードには、次の例として本質的に同じ実行可能コードが生成されます。  
  
 [!code-vb[VbXMLSamples&#3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>XML 軸プロパティ XML 名前空間の使用  
 XML リテラルで宣言されている XML 名前空間では、XML 軸プロパティで使用するため使用できません。 ただし、XML 軸プロパティを持つグローバル名前空間を使用できます。 コロンを使用して、ローカルの要素名からの XML 名前空間プレフィックスを区切ります。 例を次に示します。  
  
 [!code-vb[VbXMLSamples&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]  
  
## <a name="see-also"></a>関連項目  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Visual Basic で XML を作成します。](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Visual Basic における XML へのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)   
 [Visual Basic で XML を操作します。](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
