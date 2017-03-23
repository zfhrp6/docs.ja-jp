---
title: "volatile (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "volatile_CSharpKeyword"
  - "volatile"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "volatile キーワード [C#]"
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
caps.latest.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 29
---
# volatile (C# リファレンス)
`volatile` キーワードは、同時に実行中の複数のスレッドによってフィールドが変更される可能性があることを示します。   `volatile` と宣言されているフィールドは、シングル スレッドによるアクセスを前提とする、コンパイラの最適化の対象にはなりません。  このため、フィールドには常に最新の値が含まれます。  
  
 `volatile` 修飾子は、通常、アクセスをシリアル化する [lock](../../../csharp/language-reference/keywords/lock-statement.md) ステートメントが使用されない場合に、複数のスレッドによりアクセスされるフィールドに対して使用します。  
  
 `volatile` キーワードは次の型のフィールドに使用できます。  
  
-   参照型  
  
-   ポインター型 \(unsafe コンテキスト内\)  ポインター自体は volatile にすることができますが、ポインターが指しているオブジェクトは volatile にすることができません。  つまり、"volatile を指すポインター" は宣言できません。  
  
-   sbyte、byte、short、ushort、int、uint、char、float、bool などの型  
  
-   基本型 byte、sbyte、short、ushort、int、または uint のいずれかを持つ列挙型  
  
-   参照型であることが判明しているジェネリック型パラメーター  
  
-   <xref:System.IntPtr> 型および <xref:System.UIntPtr> 型  
  
 volatile キーワードは、クラスまたは構造体のフィールドにのみ適用できます。  ローカル変数を `volatile` で宣言することはできません。  
  
## 使用例  
 次の例では、public のフィールド変数を `volatile` として宣言する方法を示します。  
  
 [!code-cs[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## 使用例  
 次の例では、補助スレッドつまりワーカー スレッドを作成および使用して、プライマリ スレッドとの並行処理を実行する方法を示します。  マルチスレッド処理の背景情報については、「[Threading](../Topic/Managed%20Threading.md)」および「[スレッド](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 [!code-cs[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)