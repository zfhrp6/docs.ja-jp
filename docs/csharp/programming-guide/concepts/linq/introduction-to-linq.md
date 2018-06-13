---
title: LINQ の概要 (C#)
ms.date: 07/20/2015
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
ms.openlocfilehash: 3c32c20efec55568a668c5dba55baf8f3ebbee7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323317"
---
# <a name="introduction-to-linq-c"></a>LINQ の概要 (C#)
統合言語クエリ (LINQ) は、.NET Framework Version 3.5 で導入された、オブジェクトとデータの溝を埋める画期的な手法です。  
  
 これまでは、データに対するクエリは、コンパイル時の型チェックや IntelliSense のサポートなしに、単純な文字列として表現されてきました。 さらに、SQL データベース、XML ドキュメント、さまざまな Web サービスといったデータ ソースの種類ごとに、異なるクエリ言語を習得する必要がありました。 LINQ により、"*クエリ*" は C# での高度な言語構成要素になります。 厳密に型指定されているオブジェクトのコレクションに対して、言語キーワードと使い慣れた演算子を用いてクエリを記述します。  
  
 C# を使って LINQ クエリを記述できます。対象は、<xref:System.Collections.IEnumerable> またはジェネリック <xref:System.Collections.Generic.IEnumerable%601> インターフェイスをサポートする SQL Server データベース、XML ドキュメント、ADO.NET データセット、その他のオブジェクトのコレクションです。 サード パーティからも、多くの Web サービスとその他のデータベース実装に対する LINQ のサポートが提供されます。  
  
 新しいプロジェクトで LINQ クエリを使用できるほか、既存のプロジェクトで LINQ 以外のクエリを使用することもできます。 唯一の要件は、プロジェクトが .NET Framework 3.5 以降をターゲットとしていることです。  
  
 次の Visual Studio の図は、SQL Server データベースに対して部分的に完了した LINQ クエリを示しています。このクエリは C# および Visual Basic の両方で記述されており、完全な型チェックと IntelliSense に対応しています。  
  
 ![Intellisense を使用する LINQ クエリ](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")  
  
## <a name="next-steps"></a>次の手順  
 LINQ の詳細については、最初に「[C# の LINQ の概要](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)」の概要に関するセクションで基本的な概念を理解し、次に関心のある LINQ テクノロジのドキュメントを参照してください。  
  
-   SQL Server データベース: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
-   XML ドキュメント: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
-   ADO.NET データセット: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
-   .NET のコレクション、ファイル、文字列など: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>参照  
 [統合言語クエリ (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
