---
title: "インデクサーの使用 (C# プログラミング ガイド) | Microsoft Docs"
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
  - "インデクサー [C#], インデクサーの概要"
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
caps.latest.revision: 30
caps.handback.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# インデクサーの使用 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

インデクサーは、構文を簡略化します。これを使用すると、[クラス](../../../csharp/language-reference/keywords/class.md)、[構造体](../../../csharp/language-reference/keywords/struct.md)、または [インターフェイス](../../../csharp/language-reference/keywords/interface.md)を作成できます。クライアント アプリケーションは配列と同じようにアクセスできます。  インデクサーは、内部コレクションまたは内部配列をカプセル化することが主な目的である型で最も多く実装されます。  たとえば、TempRecord という名前のクラスがあるとします。これは温度を華氏で表し、24 時間のうちに 10 回、異なる時刻に温度を記録します。  このクラスには float 型の "temps" という名前の配列が含まれており、これは温度を表します。また、<xref:System.DateTime> も含まれており、これは温度が記録された日付を表します。  このクラスにインデクサーを実装すると、クライアントは TempRecord インスタンスの温度に、`float temp = tr.temps[4]` ではなく `float temp = tr[4]` としてアクセスすることができます。  インデクサーはクライアント アプリケーションの構文を簡略化するだけでなく、クラスとその目的を、他の開発者たちにとって分かりやすい、より直感的なものとします。  
  
 クラスまたは構造体でインデクサーを宣言するには、次の例のように、[this](../../../csharp/language-reference/keywords/this.md) キーワードを使用します。  
  
```  
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
  
```  
  
## 解説  
 インデクサーの型とパラメーターの型は、少なくともインデクサー自体と同程度のアクセシビリティが必要です。  アクセシビリティのレベルの詳細については、「[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)」を参照してください。  
  
 インターフェイスでインデクサーを使用する方法の詳細については、「[インターフェイスのインデクサー \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)」を参照してください。  
  
 インデクサーのシグネチャは、番号と仮パラメーターの型で構成されています。  インデクサーの型または仮パラメーターの名前は含まれません。  同じクラスで複数のインデクサーを宣言する場合は、異なるシグネチャを指定する必要があります。  
  
 インデクサーの値は変数には分類されないので、インデクサーの値を [ref](../../../csharp/language-reference/keywords/ref.md) パラメーターまたは [out](../../../csharp/language-reference/keywords/out.md) パラメーターとして渡すことはできません。  
  
 インデクサーに他の言語で使用できる名前を指定するには、宣言に `name` 属性を使用します。  次に例を示します。  
  
```  
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this [int index]   // Indexer declaration  
{  
}  
```  
  
 このインデクサーの名前は `TheItem` になります。  name 属性を指定しないと、`Item` が既定の名前になります。  
  
## 例 1  
  
### Description  
 次の例は、プライベートな配列フィールド `temps` とインデクサーの宣言方法を示しています。  インデクサーを使うと、インスタンス `tempRecord[i]` に直接アクセスできます。  インデクサーを使わない場合は、配列を [public](../../../csharp/language-reference/keywords/public.md) メンバーとして宣言し、そのメンバー `tempRecord.temps[i]` に直接アクセスします。  
  
 `Console.Write` ステートメントなどでインデクサーのアクセスが評価されると、[get](../../../csharp/language-reference/keywords/get.md) アクセサーが呼び出されることに注意してください。  したがって、`get` アクセサーがない場合は、コンパイル エラーが発生します。  
  
### コード  
 [!code-cs[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## 他の値を使用したインデックス作成  
 C\# では、インデックスの型は整数に限定されません。  たとえば、文字列をインデクサーに使用することが有効なこともあります。  このようなインデクサーは、コレクション内の文字列を検索し、適切な値を返す場合に実装されることがあります。  アクセサーをオーバーロードできるため、文字列と整数のバージョンは共存できます。  
  
## 例 2  
  
### Description  
 この例では、曜日を格納するクラスが宣言されています。  `get` アクセサーは、曜日の名前を示す文字列を取得すると、対応する整数を返すように宣言されています。  たとえば、Sunday の場合は 0、Monday の場合は 1 などの値を返します。  
  
### コード  
 [!code-cs[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## 信頼性の高いプログラミング  
 インデクサーのセキュリティと信頼性を改善するには、主に 2 つの方法があります。  
  
-   クライアント コードが無効なインデックス値を渡してきても、それを処理できるように必ずエラー処理を組み込んでください。  このトピックの最初の例の TempRecord クラスには Length プロパティが用意されており、入力がインデクサーに渡される前にクライアント コードでの検証が行われるようになっています。  エラー処理コードをインデクサー自体の内部に置くこともできます。  インデクサーのアクセサー内部でスローされる例外はすべて、ユーザーのためにドキュメント化してください。  
  
-   `get` アクセサーと [set](../../../csharp/language-reference/keywords/set.md) アクセサーのアクセシビリティを設定し、適切な制限を指定します。  これは、`set` アクセサーの場合、特に重要です。  詳細については、「[アクセサーのアクセシビリティの制限](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)」を参照してください。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [インデクサー](../../../csharp/programming-guide/indexers/index.md)   
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)