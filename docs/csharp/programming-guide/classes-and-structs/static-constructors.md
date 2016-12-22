---
title: "静的コンストラクター (C# プログラミング ガイド) | Microsoft Docs"
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
  - "コンストラクター [C#], static"
  - "静的コンストラクター [C#]"
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 静的コンストラクター (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

静的コンストラクターは、[静的](../../../csharp/language-reference/keywords/static.md)データの初期化、または 1 回だけ実行する必要がある特定の処理の実行に使用されます。  静的コンストラクターは、最初のインスタンスを作成する前、または静的メンバーが参照される前に自動的に呼び出されます。  
  
 [!code-cs[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 静的コンストラクターには、次のような特徴があります。  
  
-   静的コンストラクターはアクセス修飾子をとらず、パラメーターはありません。  
  
-   最初のインスタンスが作成される前、または静的メンバーが参照される前に、静的コンストラクターが自動的に呼び出されて[クラス](../../../csharp/language-reference/keywords/class.md)を初期化します。  
  
-   静的コンストラクターを直接呼び出すことはできません。  
  
-   プログラム内で静的コンストラクターが実行されるタイミングを制御することはできません。  
  
-   静的コンストラクターは、通常、クラスがログ ファイルを使用しているときに使われ、このファイルにエントリを書き込みます。  
  
-   静的コンストラクターは、アンマネージ コードのラッパー クラスを作成するときにも役立ちます。その際、静的コンストラクターは、`LoadLibrary` メソッドを呼び出すことができます。  
  
-   静的コンストラクターが例外をスローした場合、ランタイムがもう一度そのコンストラクターを呼び出すことはありません。その型は、プログラムが実行されているアプリケーション ドメインの有効期間にわたって、初期化されていない状態のまま残ります。  
  
## 使用例  
 この例では、`Bus` クラスには静的コンストラクターがあります。  `Bus` の最初のインスタンスを作成すると \(`bus1`\)、クラスを初期化するために静的コンストラクターが呼び出されます。  `Bus` のインスタンスを 2 つ作成しても、静的コンストラクターは 1 回だけ、インスタンス コンストラクターの前に実行されることが、次のサンプル出力からわかります。  
  
 [!code-cs[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [デストラクター](../../../csharp/programming-guide/classes-and-structs/destructors.md)