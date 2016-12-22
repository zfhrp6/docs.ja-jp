---
title: "方法: COM 相互運用機能を使用したプログラミングでインデックス付きプロパティを使用する (C# プログラミング ガイド) | Microsoft Docs"
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
  - "インデックス付きプロパティ [C#]"
  - "Office プログラミング [C++], インデックス付きプロパティ"
  - "プロパティ [C#], インデックス付き"
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法: COM 相互運用機能を使用したプログラミングでインデックス付きプロパティを使用する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

*インデックス付きプロパティ*によって、パラメーターを持つ COM プロパティを C\# プログラミングで使用する方法が改善されます。  インデックス付きプロパティは、[名前付き引数と省略可能な引数](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)、新しい型 \([dynamic](../../../csharp/language-reference/keywords/dynamic.md)\)、[埋め込み型情報](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)など、Visual C\# 2010 で導入された他の機能と連携して動作します。これにより、Microsoft Office プログラミングが強化されます。  
  
 以前のバージョンの C\# では、プロパティとしてメソッドにアクセスできるのは、`get` メソッドがパラメーターを持たず、`set` が値パラメーターを 1 つだけ持っている場合に限られていました。  しかし、すべての COM プロパティがその制限に適合しているわけではありません。  たとえば、Excel の [Range プロパティ](http://go.microsoft.com/fwlink/?LinkId=166053)には、範囲の名前のパラメーターが必要な `get` アクセサーがあります。  以前は、`Range` プロパティに直接アクセスできなかったため、次の例に示すように、このプロパティの代わりに `get_Range` メソッドを使用する必要がありました。  
  
 [!code-cs[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 インデックス付きプロパティを使用すると、次のように記述することができます。  
  
 [!code-cs[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  上記の例では、Visual C\# 2010 で導入された[省略可能な引数](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)機能を使用することもできます。この機能を使用すると、`Type.Missing` を省略できます。  
  
 同様に、Visual C\# 2008 以前で、[Range](http://go.microsoft.com/fwlink/?LinkId=179211) オブジェクトの `Value` プロパティの値を設定するには、2 つの引数が必要です。  1 つは、範囲値の型を指定する省略可能なパラメーターの引数です。  もう 1 つは、`Value` プロパティの値を指定します。  Visual C\# 2010 より前の C\# では、引数を 1 つしか指定できませんでした。  このため、通常の set メソッドを使用するのではなく、`set_Value` メソッドかまたは別のプロパティ \([Value2](http://go.microsoft.com/fwlink/?LinkId=166050)\) を使用する必要がありました。  これらの方法について、次の例で説明します。  どちらの場合も、セル A1 の値が `Name` に設定されます。  
  
 [!code-cs[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 インデックス付きプロパティを使用すると、代わりに次のようなコードを記述できます。  
  
 [!code-cs[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 独自のインデックス付きプロパティを作成することはできません。  この機能でサポートされているのは、既存のインデックス付きプロパティの使用だけです。  
  
## 使用例  
 コード例全体を次に示します。  Office API にアクセスするプロジェクトの設定方法の詳細については、「[方法: Visual C\# の機能を使用して Office 相互運用オブジェクトにアクセスする](../Topic/How%20to:%20Access%20Office%20Interop%20Objects%20by%20Using%20Visual%20C%23%20Features%20\(C%23%20Programming%20Guide\).md)」を参照してください。  
  
 [!code-cs[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## 参照  
 [名前付き引数と省略可能な引数](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)   
 [動的](../../../csharp/language-reference/keywords/dynamic.md)   
 [dynamic 型の使用](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [方法: Office プログラミングで名前付き引数と省略可能な引数を使用する](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)   
 [方法: Visual C\# の機能を使用して Office 相互運用オブジェクトにアクセスする](../Topic/How%20to:%20Access%20Office%20Interop%20Objects%20by%20Using%20Visual%20C%23%20Features%20\(C%23%20Programming%20Guide\).md)   
 [チュートリアル: Office のプログラミング](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)