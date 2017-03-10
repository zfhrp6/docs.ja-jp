---
title: "Overview of LINQ to XML in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "LINQ to XML [Visual Basic], about LINQ to XML"
  - "LINQ [Visual Basic], LINQ to XML"
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Overview of LINQ to XML in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、XML リテラルと XML 軸プロパティをとおして [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] をサポートします。  これにより、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コードでは、使い慣れた便利な構文を使用して XML を操作できます。*XML リテラル*を使用すると、コード内に XML を直接含めることができます。  *XML 軸プロパティ*は、XML リテラルの子ノード、子孫ノード、および属性へのアクセスを可能にします。  詳細については、「[XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)」および「[Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)」を参照してください。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] は、[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] を活用するように特別に設計されたメモリ内 XML プログラミング API です。  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] API を直接呼び出すこともできますが、XML リテラルの宣言と XML 軸プロパティへの直接的なアクセスは [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] でのみ可能です。  
  
> [!NOTE]
>  XML リテラルと XML 軸プロパティは、ASP.NET ページ内の宣言コードではサポートされません。  Visual Basic の XML 機能を使用するには、ASP.NET アプリケーションの分離コード ページにコードを配置します。  
  
 ![ビデオへのリンク](../../../../csharp/programming-guide/concepts/linq/media/playvideo.png "PlayVideo") 関連するビデオ デモについては、「[How Do I Get Started with LINQ to XML? \(操作方法: LINQ to XML を使用する\)](http://go.microsoft.com/fwlink/?LinkId=143034)」および「[How Do I Create Excel Spreadsheets using LINQ to XML? \(操作方法: LINQ to XML を使用して Excel スプレッドシートを作成する\)](http://go.microsoft.com/fwlink/?LinkId=143536)」を参照してください。  
  
## XML の作成  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で XML ツリーを作成する方法は 2 つあります。  XML リテラルをコード内に直接宣言するか、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] API を使用してツリーを作成します。  どちらの処理でも、XML ツリーの最終構造を反映するコードを記述できます。  たとえば、次のコード例では、XML 要素が作成されます。  
  
 [!code-vb[VbXmlSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/overview-of-linq-to-xml_1.vb)]  
  
 詳細については、「[Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)」を参照してください。  
  
## XML へのアクセスとナビゲーション  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、XML 構造体へのアクセスとナビゲーションを行うための XML 軸プロパティが用意されています。  これらのプロパティを使用して XML 子要素の名前を指定することで、XML の要素と属性にアクセスできます。  または、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] メソッドを明示的に呼び出して、要素と属性のナビゲーションおよび検索を実行することもできます。  たとえば、次のコード例では、XML 軸プロパティを使用して XML 要素の属性と子要素を参照します。  このコード例では、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリを使用して子要素を取得し、それらを XML 要素として出力することで、変換を効率よく行っています。  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/overview-of-linq-to-xml_2.vb)]  
  
 詳細については、「[Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)」を参照してください。  
  
## XML 名前空間  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、`Imports` ステートメントを使用して、グローバル XML 名前空間のエイリアスを指定できます。  次の例は、`Imports` ステートメントを使用して XML 名前空間をインポートする方法を示しています。  
  
 [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/overview-of-linq-to-xml_3.vb)]  
  
 XML 名前空間のエイリアスは、XML 軸プロパティにアクセスしたり、XML ドキュメントや XML 要素の XML リテラルを宣言したりするときに使用できます。  
  
 [GetXmlNamespace Operator](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)を使用すると、特定の名前空間プレフィックスの <xref:System.Xml.Linq.XNamespace> オブジェクトを取得できます。  
  
 詳細については、「[Imports Statement \(XML Namespace\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)」を参照してください。  
  
### XML リテラルでの XML 名前空間の使用  
 次の例は、グローバル名前空間 `ns` を使用する <xref:System.Xml.Linq.XElement> オブジェクトの作成方法を示しています。  
  
 [!code-vb[VbXMLSamples#2](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/overview-of-linq-to-xml_4.vb)]  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラは、XML 名前空間のエイリアスを含む XML リテラルを、XML 表記の XML 名前空間を使用する同等のコードに変換し、`xmlns` 属性を追加します。  前のセクションで示した例のコードをコンパイルすると、次の例と本質的に同一の実行可能コードが生成されます。  
  
 [!code-vb[VbXMLSamples#3](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/overview-of-linq-to-xml_5.vb)]  
  
### XML 軸プロパティでの XML 名前空間の使用  
 XML リテラル内で宣言された XML 名前空間は、XML 軸プロパティでは使用できません。  ただし、XML 軸プロパティでグローバル名前空間を使用することはできます。  XML 名前空間プレフィックスとローカル要素名を区切るには、コロンを使用します。  例を次に示します。  
  
 [!code-vb[VbXMLSamples#4](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/overview-of-linq-to-xml_6.vb)]  
  
## 参照  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)   
 [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)