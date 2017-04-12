---
title: "プログラミング ガイド (LINQ to XML) (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: f1f942bf-3404-4354-b4c5-4fe35e37a02b
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
ms.openlocfilehash: 7e7ef63d587778d54bb4dd4d3d6cf3dc24442882
ms.lasthandoff: 03/13/2017

---
# <a name="programming-guide-linq-to-xml-visual-basic"></a>プログラミング ガイド (LINQ to XML) (Visual Basic)
ここでは、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] を使用したプログラミングに関する概念と方法の情報について説明します。  
  
## <a name="who-should-read-this-documentation"></a>このドキュメントの対象読者  
 このドキュメントは、Visual Basic との基本的な側面について既に理解している開発者を対象、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]です。  
  
 このドキュメントの目的はさせる[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]あらゆるタイプの開発者にとって使いやすいです。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]XML プログラミングを簡単にするには。 
           を使用するために上級開発者になる必要はありません。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]ジェネリック クラスに大きく依存します。 そのためがジェネリック型とクラスの使用を理解することが非常に重要です。 詳細については、次を参照してください。 [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[LINQ to XML プログラミングの概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)|概要、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]クラス、および&3; つの最も重要なクラスに関する詳細情報: <xref:System.Xml.Linq.XElement>、 <xref:System.Xml.Linq.XAttribute>、 <xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement>|  
|[XML ツリー (Visual Basic) の作成](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)|XML ツリーの作成に関する概念とタスク ベースの情報について説明します。 XML ツリーを作成するには、関数型構築を使用するか、文字列またはファイルから XML テキストを解析します。 使用することも、 <xref:System.Xml.XmlReader>XML ツリーを設定する</xref:System.Xml.XmlReader>。|  
|[XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)|名前空間を使用する XML ツリーの作成に関する詳細情報について説明します。|  
|[XML ツリーをシリアル化する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)|XML ツリーをシリアル化する複数の方法について説明し、どの方法を使用するかについてのガイダンスを紹介します。|  
|[LINQ to XML 軸 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)|列挙し、説明、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]軸メソッドは、理解する必要があります記述する前に[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]クエリ。|  
|[XML ツリー (Visual Basic) のクエリ](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)|XML ツリーのクエリの一般的な例について説明します。|  
|[XML ツリー (LINQ to XML) の変更 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)|ドキュメント オブジェクト モデル (DOM) と同様[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]場所に XML ツリーを変更することができます。|  
|[高度な LINQ to XML のプログラミング (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)|注釈、イベント、ストリーミング、およびその他の高度なシナリオに関する情報について説明します。|  
|[LINQ to XML のセキュリティ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-security.md)|LINQ to XML に関連するセキュリティの問題について説明し、セキュリティ上の脆弱性を改善するためのガイダンスを紹介します。|  
|[サンプル XML ドキュメント (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)|このドキュメントの多数の例で使用されているサンプル XML ドキュメントが含まれています。|  
  
## <a name="see-also"></a>関連項目  
 [はじめに (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)   
 [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)
