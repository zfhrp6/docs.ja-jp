---
title: "abstract (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "abstract"
  - "abstract_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "abstract キーワード [C#]"
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# abstract (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`abstract` 修飾子は、修飾対象に実装が不足しているか、不完全な実装があることを示します。  abstract 修飾子は、クラス、メソッド、プロパティ、インデクサー、およびイベントで使用できます。  クラスの宣言に `abstract` 修飾子を使用した場合、クラスは他のクラスの基本クラスとなることだけを目的とします。  抽象としてマークされているメンバー、または抽象クラスのメンバーは、抽象クラスから派生したクラスを使用して実装する必要があります。  
  
## 使用例  
 この例では、`Square` クラスは `ShapesClass` から派生したクラスであるので、このクラスにより `Area` が実装されます。  
  
 [!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]  
  
 抽象クラスには、以下に示す特徴があります。  
  
-   抽象クラスはインスタンス化できません。  
  
-   抽象クラスは、抽象メソッドおよび抽象アクセサーを含む可能性があります。  
  
-   抽象クラスを [sealed](../../../csharp/language-reference/keywords/sealed.md) 修飾子で修飾することはできません。これは、2 つの修飾子が正反対の意味を持つためです。  `sealed` 修飾子はクラスの継承を禁止し、`abstract` 修飾子はクラスの継承を要求します。  
  
-   抽象クラスから派生される非抽象クラスは、継承される抽象メソッドおよび抽象アクセサーの実際の実装をすべて含んでいる必要があります。  
  
 `abstract` 修飾子をメソッド宣言またはプロパティ宣言に使用すると、メソッドまたはプロパティに実装を含まないことを示します。  
  
 抽象メソッドには、以下に示す特徴があります。  
  
-   抽象メソッドは、暗黙的に virtual なメソッド \(仮想メソッド\) です。  
  
-   抽象メソッドの宣言は、抽象クラス内でだけ許可されます。  
  
-   抽象メソッドの宣言では実際の実装は用意されないので、メソッドの本体はなく、メソッドの宣言は単にセミコロンで終わり、シグネチャに続く中かっこ \({ }\) はありません。  次に例を示します。  
  
    ```  
    public abstract void MyMethod();  
    ```  
  
     メソッドの実装は、非抽象クラスのメンバーとしてオーバーライドされたメソッド \([オーバーライド](../../../csharp/language-reference/keywords/override.md)\) によって提供されます。  
  
-   抽象メソッドの宣言で [static](../../../csharp/language-reference/keywords/static.md) 修飾子または [virtual](../../../csharp/language-reference/keywords/virtual.md) 修飾子を使用するとエラーになります。  
  
 抽象プロパティは抽象メソッドと同様に動作しますが、宣言の構文および呼び出しの構文に相違があります。  
  
-   静的プロパティで `abstract` 修飾子を使用するのはエラーです。  
  
-   継承された抽象プロパティを派生クラス内でオーバーライドできます。オーバーライドするには、[override](../../../csharp/language-reference/keywords/override.md) 修飾子を使用するプロパティ宣言を含めます。  
  
 抽象クラスの詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。  
  
 抽象クラスは、すべてのインターフェイス メンバーの実装を用意する必要があります。  
  
 インターフェイスを実装する抽象クラスは、抽象メソッドにインターフェイス メソッドを割り当てることもあります。  次に例を示します。  
  
 [!code-cs[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]  
  
## 使用例  
 この例では、`DerivedClass` クラスは抽象クラス `BaseClass` の派生クラスです。  この抽象クラスには `AbstractMethod` という抽象メソッドと、`X` および `Y` という 2 つの抽象プロパティがあります。  
  
 [!code-cs[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]  
  
 上の例で、次に示すようなステートメントを使用して抽象クラスのインスタンスの作成を試みるとします。  
  
```  
BaseClass bc = new BaseClass();   // Error  
```  
  
 コンパイラが 'BaseClass' 抽象クラスのインスタンスを作成できないことを知らせるエラーが表示されます。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)   
 [virtual](../../../csharp/language-reference/keywords/virtual.md)   
 [オーバーライド](../../../csharp/language-reference/keywords/override.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)