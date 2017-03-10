---
title: "定数 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, 定数"
  - "定数 [C#]"
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# 定数 (C# プログラミング ガイド)
定数とは、コンパイル時に既知であり、プログラムの実行期間を通じて変更されない値です。  定数を宣言するには、[const](../../../csharp/language-reference/keywords/const.md) 修飾子を使用します。  `const` として宣言できるのは、C\# 組み込み型 \(<xref:System.Object?displayProperty=fullName> を除く\) だけです。  組み込み型の一覧については、「[組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)」を参照してください。  クラス、構造体、配列などのユーザー定義型を `const` にすることはできません。  実行時に \(コンストラクターなどで\) 一度だけ初期化され、その後は変更できないクラス、構造体、または配列を作成するには、[readonly](../../../csharp/language-reference/keywords/readonly.md) 修飾子を使用します。  
  
 C\# は、`const` のメソッド、プロパティ、イベントをサポートしません。  
  
 列挙型を使用すると、組み込みの整数型 \(`int`、`uint`、`long` など\) の名前付き定数を定義できます。  詳細については、「[enum](../../../csharp/language-reference/keywords/enum.md)」を参照してください。  
  
 定数は、宣言するときに初期化する必要があります。  次に例を示します。  
  
 [!code-cs[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/constants_1.cs)]  
  
 この例では、定数 `months` は常に 12 になり、クラス自体によっても変更できません。  実際、コンパイラが C\# ソース コードで定数の識別子 \(この場合は `months`\) を検出すると、コンパイラが生成する IL \(Intermediate Language\) コードには、識別子の代わりにリテラル値が直接出力されます。  実行時に定数に関連付けられる変数アドレスが存在しないため、`const` フィールドは、参照渡しすることも、式の左辺値として指定することもできません。  
  
> [!NOTE]
>  DLL などの他のコードに定義されている定数値を参照するときは、注意が必要です。  新しいバージョンの DLL で定数の新しい値を定義しても、その新バージョンを対象にプログラムを再コンパイルするまで、プログラムには古いリテラル値が保持されたままになります。  
  
 同じ型の複数の定数を、次のように同時に宣言できます。  
  
 [!code-cs[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/constants_2.cs)]  
  
 定数の初期化に使用する式は、循環参照を形成しない限り別の定数を参照できます。  次に例を示します。  
  
 [!code-cs[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/constants_3.cs)]  
  
 定数は、[public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、または `protected` `internal` とマークできます。  これらのアクセス修飾子によって、クラスのユーザーが定数にアクセスする方法が定義されます。  詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
 定数の値は型のすべてのインスタンスで同じであるため、定数は[静的](../../../csharp/language-reference/keywords/static.md)フィールドのようにアクセスされます。  定数の宣言に `static` キーワードは使用しません。  定数を定義しているクラスに含まれていない式で定数を使用する場合は、クラス名、ピリオド、および定数の名前を使用する必要があります。  次に例を示します。  
  
 [!code-cs[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/constants_4.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [型](../../../csharp/programming-guide/types/index.md)   
 [readonly](../../../csharp/language-reference/keywords/readonly.md)   
 [Immutability in C\# Part One: Kinds of Immutability \(C\# の不変性パート 1: 不変性の種類\)](http://go.microsoft.com/fwlink/?LinkId=112379)