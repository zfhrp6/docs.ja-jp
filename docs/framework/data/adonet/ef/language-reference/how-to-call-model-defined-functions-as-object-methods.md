---
title: "方法: モデル定義関数をオブジェクト メソッドとして呼び出す | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 方法: モデル定義関数をオブジェクト メソッドとして呼び出す
ここでは、モデル定義関数を <xref:System.Data.Objects.ObjectContext> オブジェクトのメソッドまたはカスタム クラスの静的メソッドとして呼び出す方法について説明します。  *モデル定義関数*は、概念モデルで定義される関数です。  このトピックで説明する手順は、これらの関数を LINQ to Entities クエリから呼び出すのではなく、直接呼び出す方法を示すものです。  モデル定義関数を LINQ to Entities クエリに呼び出す方法の詳細については、「[方法: クエリを使用してモデル定義関数を呼び出す](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)」を参照してください。  
  
 モデル定義関数を <xref:System.Data.Objects.ObjectContext> メソッドとして呼び出す場合も、カスタム クラスの静的メソッドとして呼び出す場合も、ます <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> でメソッドをモデル定義関数にマップする必要があります。  ただし、<xref:System.Data.Objects.ObjectContext> クラスのメソッドを定義するときには、<xref:System.Data.Objects.ObjectContext.QueryProvider%2A> プロパティを使用して LINQ プロバイダーを公開する必要があります。それに対して、カスタム クラスの静的メソッドを定義するときには、<xref:System.Linq.IQueryable.Provider%2A> プロパティを使用して LINQ プロバイダーを公開する必要があります。  詳細については、下の手順の後に示した例を参照してください。  
  
 下の手順は、モデル定義関数を <xref:System.Data.Objects.ObjectContext> オブジェクトのメソッドおよびカスタム クラスの静的メソッドとして呼び出す方法の概要を示したものです。  詳細な手順は、その後の例で示します。  この手順では、関数を概念モデルで定義済みであると想定します。  詳細については、「[How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/ja-jp/0dad7b8b-58f6-4271-b238-f34810d68e5f)」を参照してください。  
  
### モデル定義関数を ObjectContext オブジェクトのメソッドとして呼び出すには  
  
1.  ソース ファイルを追加して、部分クラスを拡張します。このクラスは、<xref:System.Data.Objects.ObjectContext> クラスから派生したものであり、Entity Framework ツールによって自動生成されます。  CLR スタブを別のソース ファイルで定義すると、ファイルを再生成しても変更内容が失われません。  
  
2.  共通言語ランタイム \(CLR\) メソッドを、次のことを行う <xref:System.Data.Objects.ObjectContext> クラスに追加します。  
  
    -   概念モデルで定義された関数にマップします。  メソッドをマップするには、ユーザーが <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> をメソッドに適用する必要があります。  属性の <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> パラメーターと <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> パラメーターが、それぞれ概念モデルの名前空間と概念モデルの関数名であることに注意してください。  LINQ の関数名解決では、大文字と小文字が区別されます。  
  
    -   <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> プロパティによって返される <xref:System.Linq.IQueryProvider.Execute%2A> メソッドの結果を返します。  
  
3.  メソッドを <xref:System.Data.Objects.ObjectContext> クラスのインスタンスのメンバーとして呼び出します。  
  
### モデル定義関数をカスタム クラスの静的メソッドとして呼び出すには  
  
1.  クラスを次のことを行う静的メソッドでアプリケーションに追加します。  
  
    -   概念モデルで定義された関数にマップします。  メソッドをマップするには、ユーザーが <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> をメソッドに適用する必要があります。  属性の <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> パラメーターと <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> パラメーターが、それぞれ概念モデルの名前空間と概念モデルの関数名であることに注意してください。  
  
    -   <xref:System.Linq.IQueryable> 引数を受け取ります。  
  
    -   <xref:System.Linq.IQueryable.Provider%2A> プロパティによって返される <xref:System.Linq.IQueryProvider.Execute%2A> メソッドの結果を返します。  
  
2.  メソッドをカスタム クラスの静的メソッドのメンバーとして呼び出します。  
  
## 使用例  
 **モデル定義関数を ObjectContext オブジェクトのメソッドとして呼び出す**  
  
 次の例で、モデル定義関数を <xref:System.Data.Objects.ObjectContext> オブジェクトのメソッドとして呼び出す方法を説明します。  この例では、[AdventureWorks Sales Model](http://msdn.microsoft.com/ja-jp/f16cd988-673f-4376-b034-129ca93c7832) を使用します。  
  
 指定製品の製品収益を返す下の概念モデル関数について考察してください   \(関数を概念モデルに追加する方法については、「[How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/ja-jp/0dad7b8b-58f6-4271-b238-f34810d68e5f)」を参照してください\)。  
  
 <!-- TODO: review snippet reference [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/obj/x86/debug/edmxresourcestoembed/adventureworks.csdl#4)]  -->
 <!-- TODO: review snippet reference [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/obj/x86/debug/edmxresourcestoembed/adventureworks.csdl#4)]  -->
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  
  
## 使用例  
 次のコードでは、メソッドを上の概念モデル関数にマップする `AdventureWorksEntities` クラスに追加します。  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## 使用例  
 次のコードでは、上のメソッドを呼び出して、指定製品の製品収益を表示します。  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## 使用例  
 次の例で、コレクション \(<xref:System.Linq.IQueryable%601> オブジェクトとして\) を返すモデル定義関数を呼び出す方法を説明します。  指定された製品 ID に関して `SalesOrderDetails` をすべて返す下の概念モデル関数について考察してください。  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## 使用例  
 次のコードでは、メソッドを上の概念モデル関数にマップする `AdventureWorksEntities` クラスに追加します。  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## 使用例  
 次のコードは、メソッドを呼び出します。  返された <xref:System.Linq.IQueryable%601> クエリがさらに絞り込まれて、各 `SalesOrderDetail` のライン合計を返すことに注意してください。  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## 使用例  
 **モデル定義関数をカスタム クラスの静的メソッドとして呼び出す**  
  
 次の例で、モデル定義関数をカスタム クラスの静的メソッドとして呼び出す方法を説明します。  この例では、[AdventureWorks Sales Model](http://msdn.microsoft.com/ja-jp/f16cd988-673f-4376-b034-129ca93c7832) を使用します。  
  
> [!NOTE]
>  ユーザーが、モデル定義関数をカスタム クラスの静的メソッドとして呼び出すときには、モデル定義関数はコレクションを受け取って、コレクションの値の集計結果を返す必要があります。  
  
 SalesOrderDetail コレクションの製品収益を返す下の概念モデル関数について考察してください   \(関数を概念モデルに追加する方法については、「[How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/ja-jp/0dad7b8b-58f6-4271-b238-f34810d68e5f)」を参照してください\)。  
  
 <!-- TODO: review snippet reference [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/obj/x86/debug/edmxresourcestoembed/adventureworks.csdl#1)]  -->
 <!-- TODO: review snippet reference [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/obj/x86/debug/edmxresourcestoembed/adventureworks.csdl#1)]  -->
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]  
  
## 使用例  
 次のコードでは、上の概念モデル関数にマップする静的メソッドを持つアプリケーションにクラスを追加します。  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## 使用例  
 次のコードでは、上のメソッドを呼び出して、SalesOrderDetail コレクションの製品収益を表示します。  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## 参照  
 [.edmx File Overview](http://msdn.microsoft.com/ja-jp/f4c8e7ce-1db6-417e-9759-15f8b55155d4)   
 [LINQ to Entities でのクエリ](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)   
 [LINQ to Entities クエリ内の関数の呼び出し](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)