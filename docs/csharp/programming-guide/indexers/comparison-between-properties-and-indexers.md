---
title: "プロパティとインデクサーの比較 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "インデクサー [C#], およびプロパティ"
  - "プロパティ [C#], およびインデクサー"
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# プロパティとインデクサーの比較 (C# プログラミング ガイド)
インデクサーはプロパティと似ています。  次の表で示す相違点を除けば、プロパティのアクセサーに対して定義されているすべての規則が、インデクサーのアクセサーにも同じように適用されます。  
  
|プロパティ|インデクサー|  
|-----------|------------|  
|メソッドをパブリック データ メンバーのように呼び出すことができます。|オブジェクト自体に配列表記を使用して、オブジェクトの内部コレクションの要素にアクセスすることができます。|  
|簡易名でアクセスされます。|インデックスでアクセスされます。|  
|静的メンバーまたはインスタンス メンバーになることができます。|インスタンス メンバーである必要があります。|  
|プロパティの [get](../../../csharp/language-reference/keywords/get.md) アクセサーにはパラメーターがありません。|インデクサーの `get` アクセサーには、インデクサーと同じ仮パラメーター リストがあります。|  
|プロパティの [set](../../../csharp/language-reference/keywords/set.md) アクセサーには、暗黙の `value` パラメーターがあります。|インデクサーの `set` アクセサーには、[value](../../../csharp/language-reference/keywords/value.md) パラメーターの他に、インデクサーと同じ仮パラメーター リストがあります。|  
|[自動実装プロパティ](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) を持つ簡略化された構文をサポートします。|簡略化された構文をサポートしません。|  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [インデクサー](../../../csharp/programming-guide/indexers/index.md)   
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)