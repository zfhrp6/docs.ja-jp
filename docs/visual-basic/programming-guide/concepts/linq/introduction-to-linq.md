---
title: LINQ (Visual Basic) の概要
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: 371801e1730c578b039adb6a88bd0bcdfd186db7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644863"
---
# <a name="introduction-to-linq-visual-basic"></a>LINQ (Visual Basic) の概要
統合言語クエリ (LINQ) は、.NET Framework Version 3.5 で導入された、オブジェクトとデータの溝を埋める画期的な手法です。  
  
 これまでは、データに対するクエリは、コンパイル時の型チェックや IntelliSense のサポートなしに、単純な文字列として表現されてきました。 さらに、SQL データベース、XML ドキュメント、さまざまな Web サービスといったデータ ソースの種類ごとに、異なるクエリ言語を習得する必要がありました。 LINQ により、*クエリ*Visual Basic でファースト クラスの言語構成要素。 厳密に型指定されているオブジェクトのコレクションに対して、言語キーワードと使い慣れた演算子を用いてクエリを記述します。  
  
 Visual Basic での LINQ クエリを記述するには SQL Server データベース、XML ドキュメント、ADO.NET データセット、およびサポートするようなオブジェクトのコレクションの<xref:System.Collections.IEnumerable>または汎用<xref:System.Collections.Generic.IEnumerable%601>インターフェイスです。 サード パーティからも、多くの Web サービスとその他のデータベース実装に対する LINQ のサポートが提供されます。  
  
 新しいプロジェクトで LINQ クエリを使用できるほか、既存のプロジェクトで LINQ 以外のクエリを使用することもできます。 唯一の要件は、プロジェクトが .NET Framework 3.5 以降をターゲットとしていることです。  
  
 次の Visual Studio の図は、SQL Server データベースに対して部分的に完了した LINQ クエリを示しています。このクエリは C# および Visual Basic の両方で記述されており、完全な型チェックと IntelliSense に対応しています。  
  
 ![Intellisense を使用する LINQ クエリ](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")  
  
## <a name="next-steps"></a>次の手順  
 LINQ に関する詳細については、はじめに」セクションで基本的な概念を理解することで開始[Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)としている LINQ テクノロジのドキュメントを読んで対象。  
  
-   SQL Server データベース: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
-   XML ドキュメント: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
-   ADO.NET データセット: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
-   .NET コレクション、ファイル、文字列など[LINQ to Objects (Visual Basic)。](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>関連項目  
 [統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
