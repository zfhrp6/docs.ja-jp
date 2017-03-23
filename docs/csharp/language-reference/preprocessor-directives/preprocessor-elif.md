---
title: "#elif (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#elif"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#elif ディレクティブ [C#]"
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# #elif (C# リファレンス)
`#elif` を使用すると、複合条件付きディレクティブを作成できます。  `#elif` 式が評価されるのは、先行するディレクティブ式 [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) および `#elif` \(オプション\) が `true` と評価されなかった場合です。  `#elif` 式が `true` と評価された場合は、`#elif` と次の条件付きディレクティブの間にあるすべてのコードが、コンパイラによって評価されます。  次のように記述します。  
  
```  
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 複数のシンボルを評価するときには、`==` \(等値\)、`!=` \(非等値\)、`&&` \(AND\)、および `||` \(OR\) の演算子を使用できます。  シンボルと演算子は、かっこを使用してグループ化できます。  
  
## 解説  
 `#elif` では、次のように記述した場合と同じ結果が得られます。  
  
```  
#else  
#if  
```  
  
 `#elif` を使用する方が簡単です。`#if` には対になる [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) が必要ですが、`#elif` では対応する `#endif` が不要なためです。  
  
 `#elif` の使用例については、「[\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)」を参照してください。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)