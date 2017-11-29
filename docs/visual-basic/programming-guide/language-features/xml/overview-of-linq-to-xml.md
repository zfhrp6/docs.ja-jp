---
title: "Visual Basic における LINQ to XML の概要"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: baa60939654857f40d323b6412978ed4ff918177
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visual Basic における LINQ to XML の概要
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]サポートを提供[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XML リテラルと XML 軸プロパティです。 これにより、内の XML を操作するための使い慣れた便利な構文を使用して、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コード。 *XML リテラル*コード内で直接、XML を有効にします。 *XML 軸プロパティ*access ノードが子、子孫ノード、および XML リテラルの属性を有効にします。 詳細については、次を参照してください。 [XML リテラルの概要](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)と[Visual Basic における XML のへのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)です。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]メモリ内 XML プログラミング API を具体的に活用するために設計されています[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]です。 呼び出すことができます、 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Api を直接のみ[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]XML リテラルを宣言および XML 軸のプロパティに直接アクセスすることができます。  
  
> [!NOTE]
>  ASP.NET ページ内の宣言型コードでは、XML リテラルおよび XML 軸プロパティがサポートされていません。 Visual Basic の XML の機能を使用するには、ASP.NET アプリケーションの分離コード ページで、コードを配置します。  
  
 ![ビデオへのリンク](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo")関連のビデオ デモンストレーションでは、次を参照してください。 [LINQ to XML による開始操作方法?](http://go.microsoft.com/fwlink/?LinkId=143034)と[方法 Excel スプレッドシートを作成する LINQ to XML を使用して?](http://go.microsoft.com/fwlink/?LinkId=143536)です。  
  
## <a name="creating-xml"></a>XML を作成します。  
 2 つの方法で XML ツリーを作成する[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。 直接コードでは、リテラル XML を宣言することができますか、使用して、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]ツリーを作成するための Api です。 両方のプロセスには、XML ツリーの最終構造を反映するようにコードが有効にします。 たとえば、次のコード例では、XML 要素を作成します。  
  
 [!code-vb[VbXmlSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]  
  
 詳細については、次を参照してください。 [Visual Basic における XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)です。  
  
## <a name="accessing-and-navigating-xml"></a>アクセスして、XML を移動します。  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]アクセスして XML 構造を移動するためには、XML 軸プロパティを提供します。 これらのプロパティを使用すると、XML 子要素の名前を指定することによって XML 要素と属性にアクセスできます。 代わりに、明示的に呼び出すできます、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]を移動して、要素と属性を検索するためのメソッドです。 たとえば、次のコード例は、属性および XML 要素の子要素を参照する XML 軸のプロパティを使用します。 コード例では、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリに子要素を取得し、それらを効率的に変換を実行する、XML 要素として出力します。  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]  
  
 詳細については、次を参照してください。 [Visual Basic における XML のへのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)です。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]使用してグローバル XML 名前空間のエイリアスを指定することができます、`Imports`ステートメントです。 次の例を使用する方法を示しています、 `Imports` XML 名前空間をインポートするステートメント。  
  
 [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]  
  
 XML 軸プロパティにアクセスし、XML ドキュメントと xml 要素の XML リテラルを宣言するときに、XML 名前空間の別名を使用することができます。  
  
 取得することができます、<xref:System.Xml.Linq.XNamespace>を使用して特定の名前空間プレフィックスのオブジェクト、 [GetXmlNamespace 演算子](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)です。  
  
 詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)です。  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>XML リテラルの XML 名前空間の使用  
 次の例を作成する方法を示しています、<xref:System.Xml.Linq.XElement>をグローバル名前空間を使用するオブジェクト`ns`:  
  
 [!code-vb[VbXMLSamples#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コンパイラがコードで XML 名前空間を使用するための XML 表記を使用する同等のコードに XML 名前空間エイリアスを含む XML リテラルに変換、`xmlns`属性。 コンパイルすると、前のセクションの例のコードには、次の例として本質的に同じ実行可能コードが生成されます。  
  
 [!code-vb[VbXMLSamples#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>XML 軸のプロパティでの XML 名前空間の使用  
 XML リテラルで宣言されている XML 名前空間では、XML 軸のプロパティで使用するため使用できません。 ただし、XML 軸プロパティを持つグローバル名前空間を使用できます。 コロンを使用して、ローカルの要素名から XML 名前空間プレフィックスを区切ります。 例を次に示します。  
  
 [!code-vb[VbXMLSamples#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]  
  
## <a name="see-also"></a>関連項目  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Visual Basic での XML へのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [Visual Basic での XML の操作](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
