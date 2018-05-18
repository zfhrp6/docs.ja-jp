---
title: '方法: クエリでラムダ式を使用する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: 7b9808e1f9bfca362a1cc97aa97d77482928cc68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>方法: クエリでラムダ式を使用する (C# プログラミング ガイド)
クエリ構文でラムダ式を直接使うことはありませんが、メソッドの呼び出しで使い、クエリ式はメソッドの呼び出しを含むことができます。 実際、一部のクエリ操作はメソッド構文でのみ表現できます。 クエリ構文とメソッド構文の違いについて詳しくは、「[LINQ でのクエリ構文とメソッド構文](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次の例を見ると、<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> 標準クエリ演算子を使用することにより、メソッド ベースのクエリでラムダ式を使用する方法がわかります。 この例の <xref:System.Linq.Enumerable.Where%2A> メソッドにはデリゲート型 <xref:System.Func%601> の入力パラメーターがあり、そのデリゲートは入力として整数を受け取ってブール値を返すことに注意してください。 ラムダ式は、そのデリゲートに変換できます。 これが <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> メソッドを使用する [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] のクエリであったなら、パラメーターの型は `Expression<Func<int,bool>>` になりますが、ラムダ式の表現はまったく同じです。 式の型の詳細については、<xref:System.Linq.Expressions.Expression?displayProperty=nameWithType> に関する記事をご覧ください。  
  
 [!code-csharp[csProgGuideLINQ#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_1.cs)]  
  
## <a name="example"></a>例  
 次の例では、クエリ式のメソッド呼び出しでラムダ式を使う方法を示します。 <xref:System.Linq.Enumerable.Sum%2A> 標準クエリ演算子はクエリ構文を使って呼び出すことができないため、ラムダが必要です。  
  
 このクエリは最初に、`GradeLevel` 列挙型で定義されている成績レベルに従って、学生をグループ分けします。 その後、各グループについて、各学生の合計点数を追加します。 これには、2 つの `Sum` 演算が必要です。 内側の `Sum` は各学生の合計点数を計算し、外側の `Sum` はグループ内のすべての学生の集計中の合計を保持します。  
  
 [!code-csharp[csProgGuideLINQ#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_2.cs)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このコードを実行するには、メソッドをコピーして「[方法: オブジェクトのコレクションを照会する](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md)」で提供されている `StudentClass` に貼り付けた後、`Main` メソッドからそれを呼び出します。  
  
## <a name="see-also"></a>参照  
 [ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [式ツリー](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)
