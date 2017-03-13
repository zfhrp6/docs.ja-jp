---
title: "方法: 2 つのインターフェイスのメンバーを明示的に実装する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "継承 [C#], インターフェイス メンバーの明示的な実装"
  - "インターフェイス [C#], 継承による明示的な実装"
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# 方法: 2 つのインターフェイスのメンバーを明示的に実装する (C# プログラミング ガイド)
明示的な[インターフェイス](../../../csharp/language-reference/keywords/interface.md)実装では、メンバー名が同じ 2 つのインターフェイスを実装し、各インターフェイス メンバーに別々の実装を与えることもできます。  この例では、ボックスの大きさをメートル法とヤード ポンド法の両方の単位で表示します。  Box [クラス](../../../csharp/language-reference/keywords/class.md)は、異なる測定方式を表す IEnglishDimensions と IMetricDimensions の 2 つのインターフェイスを実装します。  両方のインターフェイスは、Length と Width という同じメンバー名を持ちます。  
  
## 使用例  
 [!code-cs[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## 信頼性の高いプログラミング  
 既定の測定値を英語単位系にする場合は、Length メソッドと Width メソッドを通常どおりに実装し、次のように IMetricDimensions インターフェイスから Length メソッドと Width メソッドを明示的に実装します。  
  
 [!code-cs[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 この場合、ヤード ポンド単位にはクラス インスタンスからアクセスでき、メートル単位にはインターフェイス インスタンスからアクセスできます。  
  
 [!code-cs[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [インターフェイス](../../../csharp/programming-guide/interfaces/index.md)   
 [方法: インターフェイス メンバーを明示的に実装する](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)