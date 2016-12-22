---
title: "out パラメーター修飾子 (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "out パラメーター [C#]"
  - "パラメーター [C#], out"
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# out パラメーター修飾子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`out` キーワードを使用すると、引数が参照渡しされます。  これは [ref](../../../csharp/language-reference/keywords/ref.md) キーワードに似ていますが、`ref` の場合は、変数を初期化してから渡す必要があります。  `out` パラメーターを使用するには、メソッド定義と呼び出し元のメソッドの両方で `out` キーワードを明示的に使用する必要があります。  以下はその例です。  
  
 [!CODE [csrefKeywordsMethodParams#1](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsMethodParams#1)]  
  
 `out` 引数として渡す変数は、渡す前に初期化する必要はありませんが、呼び出されたメソッドでは、メソッドから制御を戻す前に値を代入する必要があります。  
  
 `ref` キーワードと `out` キーワードでは、実行時の動作は異なりますが、コンパイル時にはメソッド シグネチャの一部と見なされません。  そのため、2 つのメソッドのうち一方が `ref` 引数を受け取り、もう一方が `out` 引数を受け取るという点以外に違いがない場合、これらのメソッドはオーバーロードできません。  たとえば、次のコードはコンパイルされません。  
  
 [!CODE [csrefKeywordsMethodParams#2](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsMethodParams#2)]  
  
 ただし、一方のメソッドが `ref` 引数または `out` 引数を受け取り、もう一方のメソッドがどちらの引数も使用しない場合は、オーバーロードを実行できます。この例を次に示します。  
  
 [!CODE [csrefKeywordsMethodParams#3](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsMethodParams#3)]  
  
 プロパティは変数ではないので、`out` パラメーターとして渡すことができません。  
  
 配列を渡す方法については、「[ref と out を使用した配列の引き渡し](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)」を参照してください。  
  
 次の種類のメソッドに `ref` と `out` のキーワードを使用できません:  
  
-   [async](../../../visual-basic/language-reference/modifiers/async.md)、修飾子を使用して定義する単一のメソッド。  
  
-   [yield を返します。](../../../csharp/language-reference/keywords/yield.md) または `yield break` のステートメントを含む反復子のメソッド。  
  
## 使用例  
 `out` メソッドを宣言すると、メソッドが複数の値を返すようにする場合に便利です。  `out` を使用して、1 回のメソッド呼び出しで 3 つの変数を返す例を次に示します。  この例では、3 番目の引数に null が代入されます。  このようにして、メソッドからオプションで値を返すことができます。  
  
 [!CODE [csrefKeywordsMethodParams#4](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsMethodParams#4)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [メソッドのパラメーター](../../../csharp/language-reference/keywords/method-parameters.md)