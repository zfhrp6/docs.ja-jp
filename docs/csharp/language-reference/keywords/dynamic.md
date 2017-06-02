---
title: "dynamic (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- dynamic_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
caps.latest.revision: 25
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 7cec26e59a865e78bf02a84cfe2d3b5177fa55af
ms.contentlocale: ja-jp
ms.lasthandoff: 03/24/2017

---
# <a name="dynamic-c-reference"></a>dynamic (C# リファレンス)
`dynamic` 型を使用すると、コンパイル時の型チェックをバイパスする処理が可能になります。 代わりに、演算は実行時に解決されます。 `dynamic` 型により、Office オートメーション API などの COM API、IronPython ライブラリなどの動的 API、および HTML ドキュメント オブジェクト モデル (DOM: Document Object Model) へのアクセスが容易になります。  
  
 ほとんどの環境で、`dynamic` 型は `object` 型のように動作します。 ただし、`dynamic` 型の式を含む演算はコンパイラによって解決または型チェックされません。 コンパイラは演算に関する情報をまとめてパッケージ化します。その情報が後で実行時に演算を評価するために使用されます。 このプロセスの過程で、`dynamic` 型の変数は `object` 型の変数にコンパイルされます。 そのため、`dynamic` 型はコンパイル時にのみ存在し、実行時には存在しません。  
  
 `dynamic` 型の変数と `object` 型の変数の違いを次に示します。 コンパイル時に各変数の型を確認するには、`WriteLine` ステートメントの `dyn` または `obj` にマウス ポインターを置きます。 IntelliSense 機能によって、`dyn` には **dynamic**、`obj` には **object** が表示されます。  
  
 [!code-cs[csrefKeywordsTypes#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_1.cs)]  
  
 `WriteLine` ステートメントは `dyn` および `obj` の実行時の型を表示します。 その時点では、両方が同じ整数型を持ちます。 次の出力が生成されます。  
  
 `System.Int32`  
  
 `System.Int32`  
  
 コンパイル時の `dyn` と `obj` の違いを確認するには、前の例の宣言と `WriteLine` ステートメントの間に次の 2 行を追加します。  
  
```csharp  
dyn = dyn + 3;  
obj = obj + 3;  
```  
  
 式 `obj + 3` に整数およびオブジェクトを追加しようとしたことに対してコンパイル エラーが報告されます。 ただし、`dyn + 3` に関するエラーは報告されません。 `dyn` を含む式はコンパイル時にはチェックされません。これは、`dyn` の型が `dynamic` であるためです。  
  
## <a name="context"></a>コンテキスト  
 次の状況では、`dynamic` キーワードを直接記述するか、構築型のコンポーネントとして記述できます。  
  
-   宣言では、プロパティ、フィールド、インデクサー、パラメーター、戻り値、ローカル変数、または型制約として記述できます。 次のクラス定義はさまざまな宣言で `dynamic` を使用します。  
  
     [!code-cs[csrefKeywordsTypes#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_2.cs)]  
  
-   明示的な型変換で、変換先の型として記述できます。  
  
     [!code-cs[csrefKeywordsTypes#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_3.cs)]  
  
-   `is` 演算子または `as` 演算子の右側、`typeof` への引数など、型が値として機能するコンテキストでは構築型の一部として記述できます。 たとえば、次の式では `dynamic` を使用できます。  
  
     [!code-cs[csrefKeywordsTypes#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_4.cs)]  
  
## <a name="example"></a>例  
 さまざまな宣言で `dynamic` を使用する例を次に示します。 また、`Main` メソッドで、コンパイル時の型チェックと実行時の型チェックの違いを確認できます。  
  
 [!code-cs[csrefKeywordsTypes#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_5.cs)]  
  
 使用例を含む詳細については、「[dynamic 型の使用](../../../csharp/programming-guide/types/using-type-dynamic.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Dynamic.ExpandoObject?displayProperty=fullName>   
 <xref:System.Dynamic.DynamicObject?displayProperty=fullName>   
 [dynamic 型の使用](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [object](../../../csharp/language-reference/keywords/object.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [as](../../../csharp/language-reference/keywords/as.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [方法: as 演算子と is 演算子を使用して安全にキャストする](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)   
 [チュートリアル: 動的オブジェクトの作成と使用](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
