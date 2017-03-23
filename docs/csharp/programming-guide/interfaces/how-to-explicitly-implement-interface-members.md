---
title: "方法: インターフェイス メンバーを明示的に実装する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "インターフェイス [C#], 明示的に実装"
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# 方法: インターフェイス メンバーを明示的に実装する (C# プログラミング ガイド)
この例では、`IDimensions` [インターフェイス](../../../csharp/language-reference/keywords/interface.md)と `Box` クラスが宣言されています。このクラスは、`getLength` と `getWidth` の各インターフェイス メンバーを明示的に実装しています。  メンバーには、`dimensions` インターフェイス インスタンスを使ってアクセスします。  
  
## 使用例  
 [!code-cs[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## 信頼性の高いプログラミング  
  
-   `Main` メソッド内の次の行は、コンパイル エラーを生じるため、コメント アウトされます。  明示的に実装されるインターフェイス メンバーには、[クラス](../../../csharp/language-reference/keywords/class.md) インスタンスからはアクセスできません。  
  
     [!code-cs[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   `Main` メソッドの以下の行では、メソッドがインターフェイスのインスタンスから呼び出されるため、ボックスの寸法を正常に出力できます。  
  
     [!code-cs[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [インターフェイス](../../../csharp/programming-guide/interfaces/index.md)   
 [方法: 2 つのインターフェイスのメンバーを明示的に実装する](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)