---
title: "プロパティの使用 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "get アクセサー [C#]"
  - "プロパティ [C#], プロパティの概要"
  - "set アクセサー [C#]"
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# プロパティの使用 (C# プログラミング ガイド)
プロパティは、フィールドとメソッドの両方の側面を兼ね備えています。  オブジェクトを使用する側から見ると、プロパティはフィールドのように見えます。プロパティへのアクセス方法はフィールドと同じです。  クラスを実装する側から見ると、プロパティは、[get](../../../csharp/language-reference/keywords/get.md) アクセサーと [set](../../../csharp/language-reference/keywords/set.md) アクセサーのいずれか、または両方を表すコード ブロックです。  `get` アクセサーのコード ブロックは、プロパティが読み込まれたときに実行されます。`set` アクセサーのコード ブロックは、プロパティに新しい値が割り当てられたときに実行されます。  `set` アクセサーなしのプロパティは、読み取り専用と見なされます。  `get` アクセサーなしのプロパティは、書き込み専用と見なされます。  両方のアクセサーを持つプロパティは、読み書きが可能です。  
  
 フィールドとは異なり、プロパティは変数には分類されません。  したがって、プロパティを [ref](../../../csharp/language-reference/keywords/ref.md) パラメーターまたは [out](../../../csharp/language-reference/keywords/out.md) パラメーターとして渡すことはできません。  
  
 プロパティの用途はさまざまです。たとえば、変更を許可する前にデータを検証できます。データベースなど、他のソースからクラス上のデータが取得されている場合、そのデータを透過的に公開できます。データが変更されたときに、イベントを発行したり他のフィールド値を変更したりするなど、アクションを実行できます。  
  
 クラス ブロック内でプロパティを宣言するには、フィールドのアクセス レベル、プロパティの種類、プロパティの名前の順に宣言し、その後に `get` アクセサーと `set` アクセサーのいずれかまたは両方を宣言するコード ブロックが続きます。  次に例を示します。  
  
 [!code-cs[csProgGuideProperties#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_1.cs)]  
  
 この例では、`Month` がプロパティとして宣言されています。これは、`set` アクセサーで `Month` の値が 1 ～ 12 の間に設定されるようにするためです。  `Month` プロパティでは、プライベート フィールドを使用して実際の値を追跡します。  プロパティ データの実際の位置は、プロパティの "バッキング ストア" と呼ばれます。プロパティでは、プライベート フィールドをバッキング ストアとして使用することは一般的です。  プロパティの呼び出しによってのみフィールドを変更できるように、フィールドはプライベートとマークされます。  パブリック アクセスとプライベート アクセスの制約の詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
 自動実装するプロパティは、単純なプロパティ宣言に簡略化した構文を提供します。  詳細については、「[自動実装プロパティ](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)」を参照してください。  
  
## get アクセサー  
 `get` アクセサーの本体は、メソッドの本体と似ています。  アクセサーは、プロパティの型の値を返す必要があります。  `get` アクセサーを実行することは、フィールドの値を読み取ることに相当します。  たとえば、`get` アクセサーからプライベート値が戻ったときに最適化が有効な場合、`get` アクセサー メソッドの呼び出しは、コンパイルでインライン展開されます。そのため、メソッド呼び出しのオーバーヘッドはありません。  ただし、仮想 `get` アクセサー メソッドは、インライン展開できません。これは、コンパイル時点では、実行時に実際に呼び出されるメソッドをコンパイラで判断できないためです。  次に示すのは、プライベート フィールド `name` の値を返す `get` アクセサーです。  
  
 [!code-cs[csProgGuideProperties#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_2.cs)]  
  
 代入の対象になる場合を除き、プロパティを参照すると、プロパティの値を読み取るために `get` アクセサーが呼び出されます。  次に例を示します。  
  
 [!code-cs[csProgGuideProperties#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_3.cs)]  
  
 `get` アクセサーは [return](../../../csharp/language-reference/keywords/return.md) ステートメントまたは [throw](../../../csharp/language-reference/keywords/throw.md) ステートメントで終了する必要があり、さらに、制御がアクセサーの本体から離れないようにします。  
  
 `get` アクセサーを使ってオブジェクトの状態を変更するのは、不適切なプログラミング スタイルです。  たとえば、次のアクセサーには、`number` フィールドにアクセスするたびにオブジェクトの状態が変化するという副作用があります。  
  
 [!code-cs[csProgGuideProperties#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_4.cs)]  
  
 `get` アクセサーを使えば、フィールドの値を返したり、フィールドの値を計算して返したりできます。  次に例を示します。  
  
 [!code-cs[csProgGuideProperties#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_5.cs)]  
  
 前のコード例では、`Name` プロパティに値を代入しないと、NA という値を返します。  
  
## set アクセサー  
 `set` アクセサーは、戻り値が [void](../../../csharp/language-reference/keywords/void.md) のメソッドと似ています。  プロパティの型の `value` という名前の暗黙のパラメーターを使用します。  次の例では、`set` アクセサーを `Name` プロパティに追加しています。  
  
 [!code-cs[csProgGuideProperties#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_6.cs)]  
  
 プロパティに値を代入すると、新しい値を渡す引数を指定して `set` アクセサーが呼び出されます。  次に例を示します。  
  
 [!code-cs[csProgGuideProperties#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_7.cs)]  
  
 `set` アクセサーでローカル変数の宣言に暗黙のパラメーター名 \(`value`\) を使用するとエラーになります。  
  
## 解説  
 プロパティは、`public`、`private`、`protected`、`internal`、または `protected internal` とマークできます。  これらのアクセス修飾子により、クラスのユーザーがプロパティにどのようにアクセスできるかが定義されます。  同じプロパティでも、`get` アクセサーと `set` アクセサーとでアクセス修飾子が異なることがあります。  たとえば、`get` は、その型の外部からは読み取り専用アクセスのみを許可する `public` で、`set` は `private` または `protected` のことがあります。  詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
 プロパティは、`static` キーワードを使用して静的プロパティと宣言することもできます。  このように宣言すると、クラスのインスタンスが存在しない場合でも、呼び出し元がいつでもプロパティにアクセスできます。  詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  
  
 プロパティは、[virtual](../../../csharp/language-reference/keywords/virtual.md) キーワードを使用して仮想プロパティとマークすることもできます。  この場合、派生クラスでは、[override](../../../csharp/language-reference/keywords/override.md) キーワードを使用して、プロパティの動作をオーバーライドできます。  これらのオプションの詳細については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。  
  
 仮想プロパティをオーバーライドするプロパティは、[sealed](../../../csharp/language-reference/keywords/sealed.md) にすることもできます。この場合、派生クラスでは、プロパティが仮想でなくなります。  最後に、プロパティは [abstract](../../../csharp/language-reference/keywords/abstract.md) と宣言できます。  この場合、クラスには実装が存在しないので、派生クラスで独自の実装を記述する必要があります。  これらのオプションの詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。  
  
> [!NOTE]
>  [静的](../../../csharp/language-reference/keywords/static.md)プロパティのアクセサーで [virtual](../../../csharp/language-reference/keywords/virtual.md)、[abstract](../../../csharp/language-reference/keywords/abstract.md)、または [オーバーライド](../../../csharp/language-reference/keywords/override.md) のいずれかの修飾子を使うと、エラーになります。  
  
## 使用例  
 次の例では、インスタンス プロパティ、静的プロパティ、および読み取り専用プロパティが使われています。  キーボードから入力された従業員の名前を受け取り、`NumberOfEmployees` の値を 1 だけインクリメントし、従業員の名前と番号を表示します。  
  
 [!code-cs[csProgGuideProperties#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_8.cs)]  
  
## 使用例  
 基本クラスのプロパティは、派生クラスにある同じ名前の別のプロパティによって隠ぺいされています。次の例は、この基本クラスのプロパティにアクセスする方法を示しています。  
  
 [!code-cs[csProgGuideProperties#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_9.cs)]  
  
 上記の例で重要な点は次のとおりです。  
  
-   派生クラスのプロパティ `Name` は、基本クラスのプロパティ `Name` を隠ぺいしています。  この場合、派生クラスのプロパティの宣言では `new` 修飾子が使われます。  
  
     [!code-cs[csProgGuideProperties#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_10.cs)]  
  
-   基本クラスの隠ぺいされたプロパティにアクセスするには、キャスト `(Employee)` を使用します。  
  
     [!code-cs[csProgGuideProperties#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_11.cs)]  
  
     メンバーを隠ぺいする方法の詳細については、「[new 修飾子](../../../csharp/language-reference/keywords/new-modifier.md)」を参照してください。  
  
## 使用例  
 次の例では、2 つのクラス `Cube` と `Square` が抽象クラス `Shape` を実装しており、その抽象プロパティ `Area` をオーバーライドしています。  プロパティに対する [override](../../../csharp/language-reference/keywords/override.md) 修飾子の使用に注意してください。  プログラムは、入力として 1 辺の長さ \(side\) を受け取り、正方形の面積 \(square\) と立方体の表面積 \(cube\) を計算します。  また、入力として面積を受け取り、正方形の 1 辺の長さと立方体の 1 辺の長さを計算することもできます。  
  
 [!code-cs[csProgGuideProperties#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-properties_12.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [インターフェイスのプロパティ](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)   
 [自動実装プロパティ](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)