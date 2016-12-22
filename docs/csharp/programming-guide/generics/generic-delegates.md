---
title: "汎用デリゲート (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "デリゲート [C#], 汎用"
  - "ジェネリック [C#], デリゲート"
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 汎用デリゲート (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[delegate \(C\# リファレンス\)](../../../csharp/language-reference/keywords/delegate.md)は、独自に型パラメーターを定義できます。  汎用デリゲートを参照するコードでは、型の引数を指定して、クローズ構築型を作成できます。ジェネリック クラスをインスタンス化するときや、ジェネリック メソッドを呼び出すときと同様です。次に例を示します。  
  
 [!code-cs[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 C\# Version 2.0 には、メソッド グループの変換という新機能があります。この機能は、汎用デリゲート型と同様に具象にも適用されるため、前述のコード行を次の簡単な構文で記述できます。  
  
 [!code-cs[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 ジェネリック クラス内で定義されるデリゲートでは、クラスのメソッドと同様に、ジェネリック クラスの型パラメーターを使用できます。  
  
 [!code-cs[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 デリゲートを参照するコードでは、次のように、含まれるクラスの型の引数を指定する必要があります。  
  
 [!code-cs[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 汎用デリゲートが特に有効であるのは、標準的なデザイン パターンに基づいてイベントを定義する場合です。送信元の引数は厳密に型指定され、<xref:System.Object> との間でキャストを実行する必要がなくなるためです。  
  
 [!code-cs[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## 参照  
 <xref:System.Collections.Generic>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [ジェネリック メソッド](../../../csharp/programming-guide/generics/generic-methods.md)   
 [ジェネリック クラス](../../../csharp/programming-guide/generics/generic-classes.md)   
 [ジェネリック インターフェイス](../../../csharp/programming-guide/generics/generic-interfaces.md)   
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)   
 [ジェネリック](../Topic/Generics%20in%20the%20.NET%20Framework.md)