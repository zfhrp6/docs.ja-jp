---
title: "extern エイリアス (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "alias_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "エイリアス [C#], extern キーワード"
  - "エイリアス, extern キーワード"
  - "extern エイリアス キーワード [C#]"
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# extern エイリアス (C# リファレンス)
同じ完全修飾型名を持つアセンブリの 2 つのバージョンを参照することが必要になる場合があります。  たとえば、1 つのアプリケーションでアセンブリの複数のバージョンを使用する必要がある場合などが挙げられます。  外部アセンブリのエイリアスを使用すると、エイリアスで指定されるルート レベルの名前空間内に各アセンブリの名前空間をラップできます。これにより、これらの名前空間を 1 つのファイルで使用できます。  
  
> [!NOTE]
>  [extern](../../../csharp/language-reference/keywords/extern.md) キーワードは、メソッドがアンマネージ コードで作成されていることを宣言する場合に、メソッドの修飾子として使用されます。  
  
 同じ完全修飾型名を持つ 2 つのアセンブリを参照するには、コマンド プロンプトで次のようにエイリアスを指定します。  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 外部エイリアス `GridV1` と `GridV2` が作成されます。  プログラム内からこれらのエイリアスを使用するには、`extern` キーワードを使用してエイリアスを参照します。  次に例を示します。  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 それぞれの extern エイリアス宣言により追加されるルートレベルの名前空間は、グローバル名前空間と並列になりますが、グローバル名前空間内には位置しません。  したがって、各アセンブリの型を参照するときに、適切な名前空間エイリアスをルートとする型の完全修飾名を使用することで、あいまいさのない状態で参照できます。  
  
 前の例では、`GridV1::Grid` は `grid.dll` のグリッド コントロールであり、`GridV2::Grid` は `grid20.dll` のグリッド コントロールです。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [:: 演算子](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)   
 [\/reference \(Import Metadata\)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)