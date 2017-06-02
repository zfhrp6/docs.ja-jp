---
title: "LINQ の概要 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: cbc19731f16d839dbd041c271821382bc4031506
ms.contentlocale: ja-jp
ms.lasthandoff: 05/10/2017

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
  
-   SQL Server データベース: [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)  
  
-   XML ドキュメント: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
-   ADO.NET データセット: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
-   .NET のコレクション、ファイル、文字列など: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>関連項目  
 [統合言語クエリ (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
