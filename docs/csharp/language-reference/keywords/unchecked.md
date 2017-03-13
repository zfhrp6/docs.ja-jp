---
title: "unchecked (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "unchecked_CSharpKeyword"
  - "unchecked"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "unchecked キーワード [C#]"
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# unchecked (C# リファレンス)
`unchecked` キーワードは、整数型の算術演算および変換に対してオーバーフロー チェックを抑制するのに使用します。  
  
 unchecked コンテキストでは、式がチェック先の型の範囲外にある値を生成した場合、オーバーフローにはフラグが付きません。  たとえば、次の例では `unchecked` ブロックまたは式で計算が実行されるため、結果が整数に対して大きすぎることは無視され、`int1` に値 \-2,147,483,639 が代入されます。  
  
 [!code-cs[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 `unchecked` 環境を削除すると、コンパイル エラーが発生します。  式のすべての項が定数であるため、オーバーフローはコンパイル時に検出できます。  
  
 非定数項を含む式は、既定では、コンパイル時にも実行時にもチェックされません。  checked 環境の有効化については、「[checked](../../../csharp/language-reference/keywords/checked.md)」を参照してください。  
  
 オーバーフローのチェックには時間がかかるため、オーバーフローの危険がない状況で unchecked コードを使用するとパフォーマンスが向上する場合があります。  ただし、オーバーフローの可能性がある場合は checked 環境を使用してください。  
  
## 使用例  
 `unchecked` キーワードの使用方法を次の例に示します。  
  
 [!code-cs[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [Checked と Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)   
 [checked](../../../csharp/language-reference/keywords/checked.md)