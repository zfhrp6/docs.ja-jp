---
title: "SQL-CLR Custom Type Mappings | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d916c7fb-4b56-4214-acbe-5e23365047b2
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# SQL-CLR Custom Type Mappings
SQL Server と共通言語ランタイム \(CLR\) 間の型マッピングは、SQLMetal コマンド ライン ツールのオブジェクト リレーショナル デザイナー \(O\/R デザイナー\) を使用すると、自動的に指定されます。  
  
 マッピングをカスタマイズしないと、「[SQL\-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)」で説明するように、これらのツールによって既定の型マッピングが割り当てられます。  これらの既定とは異なる型マッピングを使用する場合は、型マッピングをカスタマイズする必要があります。  
  
 型マッピングをカスタマイズする場合は、中間の DBML ファイルに変更を加える方法が推奨されます。  次に、SQLMetal または O\/R デザイナーでカスタマイズした DBML ファイルを使用して、コード ファイルとマッピング ファイルを作成します。  
  
 コード ファイルとマッピング ファイルから <xref:System.Data.Linq.DataContext> オブジェクトをインスタンス化すると、指定した型マッピングに従って <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=fullName> メソッドがデータベースを作成します。  マッピングに CLR の `type` 属性が指定されていない場合は、既定の型マッピングが使用されます。  
  
## SQLMetal または O\/R デザイナーを使用したカスタマイズ  
 SQLMetal と O\/R デザイナーを使用すると、コード ファイルの内外の型マッピング情報を含むオブジェクト ファイルを自動作成できます。  これらのファイルはマッピングを再作成するたびに SQLMetal または O\/R デザイナーによって上書きされるため、カスタム型マッピングを指定する場合は DBML ファイルをカスタマイズする方法をお勧めします。  
  
 SQLMetal または O\/R デザイナーで型マッピングをカスタマイズするには、最初に DBML ファイルを生成します。  次に、コード ファイルやマッピング ファイルを生成する前に、DBML ファイルを変更して適切な型マッピングを指定します。  SQLMetal では、DBML ファイルの `Type` 属性と `DbType` 属性を手動で変更して、型マッピングをカスタマイズする必要があります。  O\/R デザイナーでは、デザイナー内で変更を加えることができます。  O\/R デザイナーの使用方法の詳細については、「[LINQ to Visual Studio での SQL ツール](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio2.md)」を参照してください。  
  
> [!NOTE]
>  一部の型マッピングでは、データベースに対する変換操作中にオーバーフローやデータ損失の例外が発生することがあります。  カスタマイズを加える前に、「[SQL\-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)」の「型マッピングと実行時動作の関係」をよくお読みください。  
  
 型マッピングのカスタマイズが SQLMetal または O\/R デザイナーで認識されるためには、コード ファイルや外部のマッピング ファイルを生成するときに、必ずこれらのツールにカスタム DBML ファイルのパスを提供する必要があります。  型マッピングのカスタマイズでは必須ではありませんが、常に型マッピング情報をコード ファイルから分離し、外部の型マッピング ファイルを追加生成することをお勧めします。  コード ファイルの再コンパイルを要求しないことで、柔軟性を残しておくことができます。  
  
## データベースの変更の組み込み  
 データベースを変更すると、DBML ファイルを更新して、これらの変更を反映する必要があります。  その 1 つの方法として、新しい DBML ファイルを自動作成してから型マッピングのカスタマイズをやり直します。  もう 1 つは、新しい DBML ファイルとカスタマイズした DBML ファイルを比較し、カスタム DBML ファイルを手動で更新してデータベースの変更を反映させる方法です。  
  
## 参照  
 [SQL\-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)   
 [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)