---
title: "方法 : 派生クラスから基本クラス イベントを発生させる (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "イベント [C#], 派生クラス"
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# 方法 : 派生クラスから基本クラス イベントを発生させる (C# プログラミング ガイド)
ここでは、単純な例を使用して、基本クラスで宣言したイベントを派生クラスから発生させる標準的な方法を説明します。  このパターンは、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] クラス ライブラリの Windows フォーム クラスで広く使用されています。  
  
 他のクラスの基本クラスとして使用できるクラスを作成するときは、イベントは宣言元のクラスからしか呼び出せない特別なデリゲートであることを考慮する必要があります。  派生クラスは、基本クラスの中で宣言されたイベントを直接呼び出せません。  常に基本クラスからイベントを発生させるようにしたい場合もありますが、ほとんどの場合、派生クラスから基本クラス イベントを発生させることができるようにします。  このためには、イベントをラップする基本クラス内に保護された呼び出しメソッドを作成します。  この起動メソッドを呼び出すかオーバーライドすることによって、派生クラスから間接的にイベントを呼び出せます。  
  
> [!NOTE]
>  基本クラスで仮想イベントを宣言したり、派生クラスでそれらをオーバーライドしたりしないでください。  C\# コンパイラはこれらを正しく処理できない派生し、イベントに対するサブスクライバーが基本クラスのイベントを実際にサブ スクライブするかどうかは予測できません。  
  
## 使用例  
 [!code-cs[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/csharp/how-to-raise-base-class-_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [イベント](../../../csharp/programming-guide/events/index.md)   
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)   
 [アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [Windows フォーム内でのイベント ハンドラーの作成](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)