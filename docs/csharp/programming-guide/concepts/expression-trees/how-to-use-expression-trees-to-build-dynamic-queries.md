---
title: "方法: 式ツリーを使用して動的クエリをビルドする (C#) | Microsoft Docs"
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
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7de999848870de80996f308affde088088e32e52
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>方法 : 式ツリーを使用して動的クエリをビルドする (C#)
LINQ では、<xref:System.Linq.IQueryable%601> を実装するデータ ソースをターゲットとする構造化されたクエリを表すために、式ツリーが使われます。 たとえば、LINQ プロバイダーは、リレーショナル データ ストアのクエリを行うために、<xref:System.Linq.IQueryable%601> インターフェイスを実装します。 C# コンパイラは、このようなデータ ソースをターゲットとするクエリをコンパイルして、実行時に式ツリーを作成するコードを生成します。 クエリ プロバイダーは式ツリー データ構造を走査して、データ ソースに適したクエリ言語に変換できます。  
  
 LINQ では、<xref:System.Linq.Expressions.Expression%601> 型の変数に代入されるラムダ式を表すためにも、式ツリーが使われます。  
  
 このトピックでは、式ツリーを使って動的な LINQ クエリを作成する方法について説明します。 動的クエリは、コンパイル時にクエリの詳細がわからない場合に便利です。 たとえば、データをフィルター処理するための述語をエンド ユーザーが指定できるユーザー インターフェイスをアプリケーションで提供することがあります。 クエリに LINQ を使うには、このようなアプリケーションでは式ツリーを使って実行時に LINQ クエリを作成する必要があります。  
  
## <a name="example"></a>例  
 次の例では、式ツリーを使って `IQueryable` データ ソースに対するクエリを作成して実行する方法を示します。 このコードは、次のクエリを表す式ツリーを作成します。  
  
 `companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16)).OrderBy(company => company)`  
  
 クエリ全体を構成する式を表す式ツリーの作成には、<xref:System.Linq.Expressions> 名前空間のファクトリ メソッドが使われます。 標準クエリ演算子メソッドの呼び出しを表す式は、これらのメソッドの <xref:System.Linq.Queryable> の実装を参照します。 最終的な式ツリーが、`IQueryable` データ ソースのプロバイダーの <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> の実装に渡されて、`IQueryable` 型の実行可能なクエリが作成されます。 結果は、そのクエリ変数を列挙することにより取得されます。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 このコードでは、`Queryable.Where` メソッドに渡される述語で固定数の式を使います。 ただし、ユーザー入力に依存する可変個の述語式を結合するアプリケーションを作成することもできます。 また、ユーザーからの入力に応じて、クエリで呼び出される標準クエリ演算子を変えることもできます。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   新しい**コンソール アプリケーション** プロジェクトを作成します。  
  
-   System.Core.dll がまだ参照されていない場合は、参照を追加します。  
  
-   System.Linq.Expressions 名前空間をインクルードします。  
  
-   例のコードをコピーして、`Main` メソッドに貼り付けます。  
  
## <a name="see-also"></a>関連項目  
 [式ツリー (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)   
 [方法 : 式ツリーを実行する (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)   
 [方法: 実行時に述語フィルターを動的に指定する](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
