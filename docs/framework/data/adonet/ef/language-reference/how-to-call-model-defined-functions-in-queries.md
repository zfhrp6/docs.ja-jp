---
title: "方法: クエリを使用してモデル定義関数を呼び出す | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 方法: クエリを使用してモデル定義関数を呼び出す
ここでは、概念モデルで定義されている関数を [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリから呼び出す方法について説明します。  
  
 以下に示す手順は、モデル定義関数を [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリから呼び出す方法をまとめたものです。  各手順の詳しい説明は、その後の例で示します。  この手順では、関数を概念モデルで定義済みであると想定します。  詳細については、「[How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/ja-jp/0dad7b8b-58f6-4271-b238-f34810d68e5f)」を参照してください。  
  
### 概念モデルで定義された関数を呼び出すには  
  
1.  概念モデルで定義された関数にマップされているアプリケーションに、共通言語ランタイム \(CLR\) メソッドを追加します。  メソッドをマップするには、ユーザーが <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> をメソッドに適用する必要があります。  属性の <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> パラメーターと <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> パラメーターが、それぞれ概念モデルの名前空間名と関数名であることに注意してください。  LINQ の関数名解決では、大文字と小文字が区別されます。  
  
2.  [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリを使用して関数を呼び出します。  
  
## 使用例  
 次の例は、概念モデルで定義されている関数を [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリから呼び出す方法を示しています。  この例では、School モデルを使用します。  School モデルについては、「[Creating the School Sample Database](http://msdn.microsoft.com/ja-jp/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)」および「[Generating the School .edmx File](http://msdn.microsoft.com/ja-jp/c48b3907-a8be-4fe6-884c-e95af1852758)」を参照してください。  
  
 次の概念モデル関数は、あるインストラクターが雇用されてから経過した年数を返します。  関数を概念モデルに追加する方法については、「[How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/ja-jp/0dad7b8b-58f6-4271-b238-f34810d68e5f)」を参照してください\)。  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
 <!-- TODO: review snippet reference [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/obj/debug/edmxresourcestoembed/school.csdl#1)]  -->  
  
## 使用例  
 次に、次のメソッドをアプリケーションに追加し、<xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> を使用して概念モデル関数にマップします。  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## 使用例  
 これで、[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリから概念モデル関数を呼び出すことができます。  次のコードは、雇用年数が 10 年を超えるすべてのインストラクターを表示するメソッドを呼び出します。  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## 参照  
 [.edmx File Overview](http://msdn.microsoft.com/ja-jp/f4c8e7ce-1db6-417e-9759-15f8b55155d4)   
 [LINQ to Entities でのクエリ](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)   
 [LINQ to Entities クエリ内の関数の呼び出し](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)   
 [方法: モデル定義関数をオブジェクト メソッドとして呼び出す](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)