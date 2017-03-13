---
title: "方法 : C# で定数を定義する | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, 定数"
  - "定数 [C#]"
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
caps.latest.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 7
---
# 方法 : C# で定数を定義する
定数とは、コンパイル時に値が設定され、変更されることのないフィールドです。  定数を使用して、特殊な値の数値リテラル \("マジック番号"\) の代わりにわかりやすい名前を提供します。  
  
> [!NOTE]
>  C\# では、C および C\+\+ で一般的な [\#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) プロセッサ ディレクティブを使用する方法で定数は定義できません。  
  
 整数型 \(`int`、`byte` など\) の定数値を定義するには、列挙型を使用します。  詳細については、「[enum](../../../csharp/language-reference/keywords/enum.md)」を参照してください。  
  
 整数型以外の定数を定義する 1 つの方法としては、`Constants` という名前の 1 つの静的クラスにそれらをグループ化します。  これを行うには、次の例に示すように、クラス名の前に定数へのすべての参照を付ける必要があります。  
  
## 使用例  
 [!code-cs[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 クラス名修飾子を使用すると、定数を使用するユーザーは、それが定数であり変更できないことがわかります。  
  
## 参照  
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)