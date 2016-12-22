---
title: "プロパティ (C# プログラミング ガイド) | Microsoft Docs"
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
  - "cs.properties"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, プロパティ"
  - "プロパティ [C#]"
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
caps.latest.revision: 38
caps.handback.revision: 38
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# プロパティ (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

プロパティは、プライベート フィールドの値の読み取り、書き込み、または計算を行う、柔軟な機構が用意されたメンバーです。  プロパティは、パブリック データのメンバーと同様に使用できますが、実際は*アクセサー*という特殊なメソッドです。  メソッドの安全性と柔軟性を高めながら、簡単にデータにアクセスできます。  
  
 この例では、`TimePeriod` クラスに期間が格納されています。  このクラスには、内部的に秒単位で期間が格納されていますが、時間単位で期間を指定できる `Hours` という名前のプロパティも用意されています。  `Hours` プロパティのアクセサーでは、時間と秒の変換が実行されます。  
  
## 使用例  
 [!code-cs[csProgGuideProperties#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/properties_1.cs)]  
  
## 式の本文の定義  
 一般的には、単純に式の結果をすぐに返すプロパティを指定します。  `=>` を使用してこれらのプロパティを定義するための構文ショートカットがあります。  
  
```c#  
public string Name => First + " " + Last;   
```  
  
 プロパティは読み取り専用でなければならないので、`get` アクセサー キーワードは使用しません。  
  
## プロパティの概要  
  
-   プロパティを使えば、実装や検査コードを隠したままで、値の取得と設定についてパブリックな方法をクラスが公開できます。  
  
-   [get](../../../csharp/language-reference/keywords/get.md) プロパティ アクセサーを使用するとプロパティ値が返され、[set](../../../csharp/language-reference/keywords/set.md) アクセサーを使用すると、新しい値が割り当てられます。  これらのアクセサーには異なるアクセス レベルを指定できます。  詳細については、「[アクセサーのアクセシビリティの制限](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)」を参照してください。  
  
-   [value](../../../csharp/language-reference/keywords/value.md) キーワードを使用して、`set` アクセサーによって割り当てられる値を定義します。  
  
-   `set` アクセサーを実装しないプロパティは読み取り専用です。  
  
-   カスタムのアクセサー コードを必要としない単純なプロパティの場合、自動実装するプロパティを使用するオプションを検討します。  詳細については、「[自動実装プロパティ](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)」を参照してください。  
  
## 関連項目  
  
-   [プロパティの使用](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [インターフェイスのプロパティ](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [プロパティとインデクサーの比較](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [アクセサーのアクセシビリティの制限](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
-   [自動実装プロパティ](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [プロパティの使用](../../../csharp/programming-guide/classes-and-structs/using-properties.md)   
 [インデクサー](../../../csharp/programming-guide/indexers/index.md)