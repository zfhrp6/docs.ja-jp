---
title: "カスタム データベース関数を呼び出す方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fd5d812fbedcbef0f6ce10b324d60961eba804cf
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-call-custom-database-functions"></a>カスタム データベース関数を呼び出す方法
ここでは、データベースで定義されたカスタム関数を LINQ Entities クエリから呼び出す方法について説明します。  
  
 LINQ to Entities クエリから呼び出されるデータベース関数は、データベース内で実行されます。 データベース内で関数を実行すると、アプリケーションのパフォーマンスが向上します。  
  
 下に示す手順は、カスタム データベース関数を呼び出す方法の概要をまとめたものです。 各手順の詳しい説明は、その後の例で示します。  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>データベースで定義されるカスタム関数を呼び出すには  
  
1.  データベースにカスタム関数を作成します。  
  
     SQL Server でのユーザー定義関数の作成の詳細については、次を参照してください。 [CREATE FUNCTION (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkID=139871)です。  
  
2.  関数を .edmx ファイルのストア スキーマ定義言語 (SSDL) で宣言します。 関数の名前は、データベースで宣言される関数と同じ名前にする必要があります。  
  
     詳細については、次を参照してください。[関数要素 (SSDL)](http://msdn.microsoft.com/en-us/b60cfc3d-8b93-423e-8c99-b867256640a4)です。  
  
3.  対応するメソッドをアプリケーション コードのクラスに追加して、<xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> をそのメソッドに適用する必要があります。属性の <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> パラメーターと <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> パラメーターが、それぞれ概念モデルの名前空間名と概念モデルの関数名であることに注意してください。 LINQ の関数名解決では、大文字と小文字が区別されます。  
  
4.  LINQ to Entities クエリからメソッドを呼び出します。  
  
## <a name="example"></a>例  
 次の例は、カスタム データベース関数を LINQ to Entities クエリから呼び出す方法について説明します。 この例では、School モデルを使用します。 School モデルについては、次を参照してください。 [School サンプル データベースを作成する](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)と[学校 .edmx ファイルを生成する](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758)です。  
  
 次のコードは、`AvgStudentGrade` 関数を School のサンプル データベースに追加しています。  
  
> [!NOTE]
>  カスタム データベース関数を呼び出す手順は、データベース サーバーとは無関係にすべて同じです。 ただし、下に示すコードは、SQL Server データベースで関数を作成する方法に固有のものです。 他のデータベース サーバーでカスタム関数を作成する場合には、コードは異なることがあります。  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a>例  
 次に、関数を .edmx ファイルのストア スキーマ定義言語 (SSDL) で宣言します。 次のコードは、`AvgStudentGrade` 関数を SSDL で宣言しています。  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a>例  
 次に、メソッドを作成して、SSDL で宣言された関数にマップします。 次のクラスのメソッドは、<xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> を使用して SSDL (上を参照) で定義される関数にマップされます。 このメソッドが呼び出されると、データベース内の対応する関数が実行されます。  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a>例  
 最後に、メソッドを LINQ to Entities クエリで呼び出します。 次のコードは、学生の姓と平均の成績をコンソールに表示します。  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a>参照  
 [.edmx ファイルの概要](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [LINQ to Entities でのクエリ](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
