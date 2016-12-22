---
title: "インデクサー (C# プログラミング ガイド) | Microsoft Docs"
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
  - "cs.indexers"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, インデクサー"
  - "インデクサー [C#]"
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# インデクサー (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

インデクサーを使用すると、配列と同じようにクラスまたは構造体のインスタンスにインデックスを作成することができます。  インデクサーは[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)と似ていますが、そのアクセサーがパラメーターを受け取る点が異なります。  
  
 次の例では、ジェネリック クラスが定義され、値の割り当てと取得の手段として単純な [get](../../../csharp/language-reference/keywords/get.md) と [set](../../../csharp/language-reference/keywords/set.md) のアクセサー メソッドが提供されます。  `Program` クラスは、文字列の格納用にこのクラスのインスタンスを作成します。  
  
 [!code-cs[csProgGuideIndexers#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/index_1.cs)]  
  
> [!NOTE]
>  その他の例については、「[関連項目](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections)」を参照してください。  
  
## 式の本文の定義  
 インデクサーでは、単純に式の結果をすぐに返すのが一般的です。  `=>` を使用してこれらのインデクサーを定義するための構文ショートカットがあります。  
  
```c#  
public Customer this[long id] => store.LookupCustomer(id);  
  
```  
  
 インデクサーは読み取り専用である必要があるため、`get` アクセサー キーワードは使用しません。  
  
## インデクサーの概要  
  
-   インデクサーを使用すると、配列と同じようにオブジェクトにインデックスを作成することができます。  
  
-   `get` アクセサーは値を返します。  `set` アクセサーは値を割り当てます。  
  
-   [this](../../../csharp/language-reference/keywords/this.md) キーワードは、インデクサーの定義に使用されます。  
  
-   [value](../../../csharp/language-reference/keywords/value.md) キーワードは、`set` インデクサーによって割り当てられる値の定義に使用されます。  
  
-   インデクサーは、整数値でインデックスを指定する必要はありません。個々の検索メカニズムの定義方法によります。  
  
-   インデクサーはオーバーロードすることができます。  
  
-   インデクサーには、2 次元配列にアクセスする場合など、複数の仮パラメーターを指定できます。  
  
##  <a name="BKMK_RelatedSections"></a> 関連項目  
  
-   [インデクサーの使用](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [インターフェイスのインデクサー](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [プロパティとインデクサーの比較](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [アクセサーのアクセシビリティの制限](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)