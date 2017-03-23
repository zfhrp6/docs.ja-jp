---
title: "LINQ to XML およびその他の XML Technologies2 |Microsoft ドキュメント"
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
ms.assetid: 72ce3a82-ffc6-488c-98e7-b9b40f3591ec
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
ms.openlocfilehash: 0254788fb9efa018e735a57990144c6b176d30d6
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ to XML およびその他の XML テクノロジ
このトピックでは比較[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]を次の XML テクノロジ: <xref:System.Xml.XmlReader>、XSLT、MSXML、および XmlLite</xref:System.Xml.XmlReader> 。 使用するテクノロジを決定するときに、ここで説明する情報を参照してください。  
  
 比較について[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]ドキュメント オブジェクト モデル (DOM) を参照してください[LINQ to XML およびです。(Visual Basic) の DOM](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)します。  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ to XML およびXmlReader  
 <xref:System.Xml.XmlReader>高速、前方参照専用、非キャッシュのパーサーです。</xref:System.Xml.XmlReader>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]上位に実装<xref:System.Xml.XmlReader>と緊密に統合されています</xref:System.Xml.XmlReader>。 ただしも使用できます<xref:System.Xml.XmlReader>自体</xref:System.Xml.XmlReader>。  
  
 たとえば、1 秒間に何百もの XML ドキュメントを解析する Web サービスを構築する際に、これらのドキュメントの構造が同じであるため、XML を解析するために実装するコードの作成が&1; つだけで済む場合は、 ここではおそらく使用する<xref:System.Xml.XmlReader>自体</xref:System.Xml.XmlReader>。  
  
 これに対し、多数の小さい XML ドキュメントを解析するシステムを構築して、それぞれが異なる場合はする生産性の向上を活用する[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]を提供します。  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ to XML およびXSLT  
 両方とも[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]し、XSLT が広範な XML ドキュメント変換機能を提供します。 XSLT は、ルール ベースの宣言型の方法です。 高度な XSLT プログラミングでは、ステートレスな方法が重視される関数型のプログラミング スタイルで XSLT を記述します。 変換は、副作用なしで実装される純粋関数を使用して記述できます。 このルール ベース (関数型) の方法に精通している開発者は多くありません。また、修得するのは難しく、相当の学習時間を要する場合があります。  
  
 XSLT は、パフォーマンスの高いアプリケーションを生成する、生産性の高いシステムとして利用できます。 たとえば、Web 関連の大企業の中には、さまざまなデータ ソースを基に取得した XML から HTML を生成するための手段として XSLT を使用している企業もあります。 XSLT を CLR コードにコンパイルするマネージ XSLT エンジンは、一部のシナリオではネイティブ XSLT エンジンより高いパフォーマンスを発揮します。  
  
 ただし、XSLT では、多くの開発者が持っている C# や Visual Basic の知識は活かされません。 開発者は、別の複雑なプログラミング言語でコードを記述する必要があります。 C# (または Visual Basic) と XSLT など、統合されていない&2; つの開発システムを使用すると、ソフトウェア システムの開発や保守が困難になります。  
  
 修得後[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]クエリ式、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]変換は、強力なテクノロジでありは簡単に使用します。 基本的には、XML ドキュメントを作成、関数型構築を使用してデータから取り込んで、さまざまなソースを構築する<xref:System.Xml.Linq.XElement>オブジェクトを動的にし、全体を新しい XML ツリーにまとめています</xref:System.Xml.Linq.XElement>。 変換では、まったく新しいドキュメントを生成できます。 変換を構築する[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]を比較的簡単かつ直感的で、その結果のコードでは読み取り可能です。 このため、開発と保守のコストを削減できます。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] は、XSLT に置き換わることを目的としていません。 複雑なドキュメント中心の XML 変換 (特に、ドキュメントの構造が明確に定義されていない場合) では、引き続き XSLT が最適なツールになります。  
  
 XSLT には、W3C (World Wide Web Consortium) 標準という利点があります。 標準となっている技術を使用するだけで十分な場合は、XSLT の方が適切といえます。  
  
 XSLT は XML であるため、プログラムで操作できます。  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ to XML およびMSXML  
 MSXML は、Microsoft Windows に付属する、XML 処理のための COM ベース テクノロジです。 MSXML は DOM をネイティブで実装し、XPath と XSLT をサポートしています。 MSXML には、非キャッシュの SAX2 イベントベース パーサーも含まれています。  
  
 MSXML はパフォーマンスが高く、セキュリティもほとんどのシナリオで既定で確保されます。また、Internet Explorer でアクセスできるため、AJAX スタイルのアプリケーションでクライアント側での XML の処理を実行できます。 MSXML は、C++、JavaScript、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 6.0 など、COM をサポートするすべてのプログラミング言語から使用できます。  
  
 ただし共通言語ランタイム (CLR) に基づくマネージ コードで使用することは推奨されません。  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ to XML およびXmlLite  
 XmlLite は、非キャッシュ、前方参照専用のプル パーサーで、 主に C++ で使用されます。 マネージ コードで使用することは推奨されません。  
  
 XmlLite の最大の利点は、ほとんどのシナリオで、軽量かつ高速で安全な XML パーサーとして利用できることです。 XmlLite は脅威の対象となる要素がほとんどないため、 信頼されていないドキュメントを解析し、サービス拒否攻撃やデータ漏洩攻撃などからの保護が必要な場合は、優れた方法となります。  
  
 XmlLite は、[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] と統合されていません。 しないプログラマの生産性の向上はもたらさ動機である[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]です。  
  
## <a name="see-also"></a>関連項目  
 [はじめに (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
