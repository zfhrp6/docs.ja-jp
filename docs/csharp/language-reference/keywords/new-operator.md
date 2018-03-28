---
title: new 演算子 (C# リファレンス)
ms.date: 03/15/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab582cd14bc649ca8d1678a583a8f95e78c6bf7e
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2018
---
# <a name="new-operator-c-reference"></a>new 演算子 (C# リファレンス)
オブジェクトを作成し、コンストラクターを呼び出すために使用します。 例:  
  
```csharp
Class1 obj  = new Class1();  
```  
  
 匿名型のインスタンスの作成にも使用します。  
  
```csharp
var query = from cust in customers  
            select new { Name = cust.Name, Address = cust.PrimaryAddress };  
```  
  
 `new` 演算子は値型の既定コンストラクターの呼び出しにも使用します。 例:  
  
```csharp
int i = new int();  
```  
  
 上記のステートメントでは、`i` は `int` 型の既定値 `0` に初期化されます。 このステートメントは次のステートメントと同じ効果があります。  
  
```csharp
int i = 0;  
```  
  
 既定値の一覧については、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」を参照してください。  
  
 すべての値型には暗黙的に既定のパブリック コンストラクターがあるため、[構造体](../../../csharp/language-reference/keywords/struct.md) に対して既定のコンストラクターを宣言するとエラーになります。 パラメーター付きのコンストラクターを構造体型で宣言し、その初期値を設定することは可能ですが、これが必要になるのは、既定値以外の値が必要な場合のみです。  
  
 構造体などの値型オブジェクトと、クラスなどの参照型オブジェクトは両方とも自動的に破棄されますが、値型オブジェクトは含まれているコンテキストが破棄されたときに破棄され、参照型オブジェクトはそれに対する最後の参照が削除された後、ガベージ コレクターによって随時破棄されます。 ファイル ハンドルなどのリソース、またはネットワーク接続を含む型の場合、格納されているリソースができるだけ早く解放されるように、決定的なクリーンアップを使用することをお勧めします。 詳細については、「[using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)」を参照してください。  
  
 `new` 演算子はオーバーロードできません。  
  
 `new` 演算子によるメモリの割り当てが失敗した場合、<xref:System.OutOfMemoryException> 例外がスローされます。  
  
## <a name="example"></a>例  
 次の例では、`struct` オブジェクトおよびクラス オブジェクトは、`new` 演算子を使用して作成、初期化され、そのあと値が代入されます。 既定値と代入値が表示されます。  
  
 [!code-csharp[csrefKeywordsOperator#7](codesnippet/CSharp/new-operator_1.cs)]  
  
 この例では、文字列の既定値は `null` です。 このため、文字列の既定値は表示されません。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
