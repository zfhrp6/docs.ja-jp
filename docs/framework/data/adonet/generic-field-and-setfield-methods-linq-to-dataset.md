---
title: "Generic Field and SetField Methods (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Generic Field and SetField Methods (LINQ to DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] では、<xref:System.Data.DataRow> クラスの拡張メソッドとして、列値にアクセスするための <xref:System.Data.DataRowExtensions.Field%2A> メソッドおよび <xref:System.Data.DataRowExtensions.SetField%2A> メソッドが提供されています。これらのメソッドを使用すると、開発者は列値に容易にアクセスでき、特に、Null 値へのアクセスが容易になっています。<xref:System.Data.DataSet> が <xref:System.DBNull.Value> を使って Null 値を表現するのに対し、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] では、[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] で導入された Null 許容型が使用されます。  <xref:System.Data.DataRow> の既存の列アクセサーを使用する場合、返されたオブジェクトを適切な型にキャストする必要があります。  <xref:System.Data.DataRow> の特定のフィールドが NULL 値を許容している場合、Null 値を明示的にチェックする必要があります。<xref:System.DBNull.Value> を取得して、それを暗黙的に別の型にキャストしようとすると、<xref:System.InvalidCastException> がスローされます。  次の例では、<xref:System.Data.DataRow.IsNull%2A> メソッドを使用して Null 値をチェックしなかった場合、インデクサーが <xref:System.DBNull.Value> を返し、それを <xref:System.String> にキャストしようとすると、例外がスローされます。  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> は、<xref:System.Data.DataRow> の列値にアクセスするためのメソッドです。<xref:System.Data.DataRowExtensions.SetField%2A> は、<xref:System.Data.DataRow> の列値を設定するためのメソッドです。  <xref:System.Data.DataRowExtensions.Field%2A> メソッドも <xref:System.Data.DataRowExtensions.SetField%2A> メソッドも Null 許容型を扱うことができるため、前出の例のように Null 値を明示的にチェックする必要はありません。  また、どちらのメソッドもジェネリック メソッドであるため、戻り値の型をキャストする必要もありません。  
  
 次の例では、<xref:System.Data.DataRowExtensions.Field%2A> メソッドを使用します。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> メソッドおよび <xref:System.Data.DataRowExtensions.SetField%2A> メソッドのジェネリック パラメーター `T` に指定するデータ型は、基になる値の型と一致している必要があります。  それ以外の場合、<xref:System.InvalidCastException> 例外がスローされます。  指定する列の名前も <xref:System.Data.DataSet> 内の列名と一致している必要があります。一致していない場合、<xref:System.ArgumentException> がスローされます。  どちらの場合も、例外は、実行時にデータが列挙されて、クエリが実行されたときにスローされます。  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> メソッド自体は、型変換を一切実行しません。  ただし、型変換がまったく発生しないということではありません。  <xref:System.Data.DataRowExtensions.SetField%2A> メソッドは、[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] の <xref:System.Data.DataRow> クラスの動作を公開します。  <xref:System.Data.DataRow> オブジェクトによって型変換が実行され、変換後の値が <xref:System.Data.DataRow> オブジェクトに保存される場合もあります。  
  
## 参照  
 <xref:System.Data.DataRowExtensions>