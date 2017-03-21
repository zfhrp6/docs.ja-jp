---
title: "LINQ (Visual Basic) の概要 |Microsoft ドキュメント"
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
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
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
ms.openlocfilehash: 41964e2fcbb079b7650c3132c9035fc2f754f3de
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-linq-visual-basic"></a>LINQ (Visual Basic) の概要
統合言語クエリ (LINQ) は、革新で導入された .NET Framework version 3.5 そのブリッジのオブジェクトの世界とデータの世界の差です。  
  
 これまでは、データに対するクエリとして表現されるもの時間や IntelliSense のサポートをコンパイル時の型チェックなしの単純な文字列。 さらに、データ ソースの種類ごとに異なるクエリ言語を習得する必要がある: SQL データベース、XML ドキュメント、さまざまな Web サービス、およびなどです。 LINQ では、*クエリ*Visual Basic での第一級の言語構成要素。 言語のキーワードと使い慣れた演算子を使用してオブジェクトの厳密に型指定のコレクションに対するクエリを記述するとします。  
  
 Visual Basic で LINQ クエリを記述するには SQL Server データベース、XML ドキュメント、ADO.NET データセット、およびサポートするようなオブジェクトのコレクションの<xref:System.Collections.IEnumerable>または汎用<xref:System.Collections.Generic.IEnumerable%601>インターフェイス</xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.IEnumerable>。 LINQ のサポートは、多くの Web サービスおよびその他のデータベースの実装のサード パーティによっても表示されます。  
  
 新しいプロジェクト、または既存のプロジェクトでの LINQ 以外のクエリと並行 LINQ クエリを使用することができます。 唯一の要件は、プロジェクトが .NET Framework 3.5 以降を対象とします。  
  
 Visual Studio から次の図は、完全な型チェック、IntelliSense のサポートと、c# および Visual Basic の両方で、SQL Server データベースに対して LINQ クエリを部分的に完了を示します。  
  
 ![Intellisense を使用する LINQ クエリ](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")  
  
## <a name="next-steps"></a>次の手順  
 LINQ の詳細については、最初に Getting Started セクションで基本的な概念をよく理解[Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)で関心のある LINQ テクノロジのドキュメントを読み取り。  
  
-   SQL Server データベース: [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)  
  
-   XML ドキュメント: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
-   ADO.NET データセット: [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)  
  
-   .NET コレクション、ファイル、文字列に: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>関連項目  
 [統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
