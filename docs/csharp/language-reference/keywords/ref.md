---
title: "ref (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.assetid: b8a5e59c-907d-4065-b41d-95bf4273c0bd
caps.latest.revision: 32
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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 353abf8a0c852acbbb2949f9640c1465dec8593b
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="ref-c-reference"></a>ref (C# リファレンス)
`ref` キーワードによって、値渡しではなく、参照渡しによって引数が渡されます。 参照渡しで渡すことにより、呼び出されたメソッドのパラメーターに対する変更が、呼び出し元のメソッドに反映されます。 たとえば、呼び出し元がローカル変数の式、または配列要素のアクセス式を渡し、呼び出されたメソッドが ref パラメーターが参照するオブジェクトを置き換える場合、呼び出し元のローカル変数または配列要素は新しいオブジェクトを参照します。  
  
> [!NOTE]
>  参照渡しの概念と参照型の概念を混同しないでください。 2 つの概念は同じではありません。 メソッドのパラメーターは、値型か参照型かどうかに関係なく、`ref` によって変更できます。 参照渡しで渡される場合、値型はボックス化されません。  
  
 `ref` パラメーターを使用するには、メソッド定義と呼び出し元のメソッドの両方が、次の例に示すように `ref` キーワードを明示的に使用する必要があります。  
  
 [!code-cs[csrefKeywordsMethodParams#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_1.cs)]  
  
 `ref` パラメーターに渡す引数は、渡す前に初期化する必要があります。 これは、引数を渡す前に明示的に初期化する必要がある `out` パラメーターとは異なります。 詳細については、「[out](../../../csharp/language-reference/keywords/out.md)」を参照してください。  
  
 クラスのメンバーは、`ref` と `out` だけが異なるシグネチャを持つことはできません。 1 つの型の 2 つのメンバー間の違いが、1 つには `ref` パラメーターがあり、もう 1 つには `out` パラメーターがあることのみの場合は、コンパイラ エラーが発生します。 たとえば、次のコードはコンパイルされません。  
  
 [!code-cs[csrefKeywordsMethodParams#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_2.cs)]  
  
 ただし、次の例に示すように、1 つのメソッドに `ref` または `out` パラメーターがあり、もう 1 つのメソッドに値パラメーターがある場合は、オーバーロードすることができます。  
  
 [!code-cs[csrefKeywordsMethodParams#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_3.cs)]  
  
 非表示やオーバーライドなど、シグネチャの一致が必要な他の状況では、`ref` と `out` はシグネチャの一部であり互いに一致しません。  
  
 プロパティは変数ではありません。 プロパティはメソッドであり、`ref` パラメーターに渡すことはできません。  
  
 配列を渡す方法については、「[ref と out を使用した配列の引き渡し](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)」を参照してください。  
  
 次の種類のメソッドには、`ref` キーワードと `out` キーワードを使用することはできません。  
  
-   [async](../../../csharp/language-reference/keywords/async.md) 修飾子を使用して定義した Async メソッド。  
  
-   [yield return](../../../csharp/language-reference/keywords/yield.md) または `yield break` ステートメントを含む Iterator メソッド。  
  
## <a name="example"></a>例  
 前の例は、参照渡しで値型を渡したときの動作を示しています。 また、`ref` キーワードを使用して参照型を渡すこともできます。 参照型を参照渡しで渡すと、呼び出されたメソッドで、参照パラメーターが参照する呼び出し元のメソッドのオブジェクトを置換できます。 オブジェクトの格納場所は、参照パラメーターの値としてメソッドに渡されます。 パラメーターの格納場所の値を変更する場合は (新しいオブジェクトをポイント)、呼び出し元が参照する格納場所を変更することもできます。 次の例では、参照型のインスタンスを `ref` パラメーターとして渡します。 参照型を値渡しまたは参照渡しで渡す方法の詳細については、「[参照型パラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)」を参照してください。  
  
 [!code-cs[csrefKeywordsMethodParams#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_4.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [パラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)   
 [メソッド パラメーター](../../../csharp/language-reference/keywords/method-parameters.md)   

 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)
