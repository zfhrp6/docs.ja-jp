---
title: "式形式のメンバー (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d12f9f3af9a57e142311f6d1676b5f97e8b60d19
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="expression-bodied-members-c-programming-guide"></a>式形式のメンバー (C# プログラミング ガイド)
式本体の定義を使用すると、簡潔でわかりやすい形式でメンバーの実装を指定できます。 サポートされる任意のメンバー (メソッドやプロパティなど) に関するロジックが単一の式で構成される場合は、常に式本体の定義を使用できます。 式本体の定義には、次の一般的な構文があります。

```csharp
member => expression;
```

この *expression* には有効な式を指定します。 

式本体の定義のサポートは、メソッドとプロパティの get アクセサーのために C# 6 で導入され、C# 7 で拡張されました。 式本体の定義は、次の表の方メンバーで使用できます。 

|メンバー  |サポートが開始されたバージョン |
|---------|---------|
|[メソッド](#methods)  |C# 6 |
|[コンストラクター](#constructors)   |C# 7 |
|[ファイナライザー](#finalizers)     |C# 7 |
|[プロパティの取得](#property-get-statements)  |C# 6 |
|[プロパティの設定](#property-set-statements)  |C# 7 |
|[インデクサー](#indexers)       |C# 7 |

## <a name="methods"></a>メソッド

式形式のメソッドは、型がメソッドの戻り値の型と一致する値を返す単一の式、または、`void` を返すメソッドの場合は何らかの処理を実行する単一の式で構成されます。 たとえば、一般的に、<xref:System.Object.ToString%2A> メソッドをオーバーライドする型には、現在のオブジェクトの文字列形式を返す単一の式が含まれています。 

次の例では、式本体の定義を使用して <xref:System.Object.ToString%2A> メソッドをオーバーライドする `Person` クラスを定義します。 また、名前をコンソールに表示する `Show` メソッドも定義します。 `ToString` 式本体の定義に `return` キーワードが使用されていない点に注意してください。

[!code-cs[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

詳細については、「[メソッド (C# プログラミング ガイド)](../classes-and-structs/methods.md)」を参照してください。
 
## <a name="constructors"></a>コンストラクター

一般的に、コンストラクターの式本体の定義は、コンストラクターの引数を処理したり、インスタンスの状態を初期化したりする単一の代入式またはメソッド呼び出しから構成されます。 

次の例では、コンストラクターに *name* という名前の文字列パラメーターが 1 つある `Location` クラスが定義されています。 式の本体の定義により `Name` プロパティに引数が割り当てられます。

[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

詳細については、「[コンストラクター (C# プログラミング ガイド)](../classes-and-structs/constructors.md)」を参照してください。

## <a name="finalizers"></a>ファイナライザー

一般的に、ファイナライザーの式本体の定義には、アンマネージ リソースをリリースするステートメントなどのクリーンアップ ステートメントが含まれています。

次の例では、式本体の定義を使用して、ファイナライザーが呼び出されたことを示すファイナライザーを定義します。

[!code-cs[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

詳細については、「[ファイナライザー (C# プログラミング ガイド)](../classes-and-structs/destructors.md)」を参照してください。

## <a name="property-get-statements"></a>プロパティの get ステートメント

プロパティの get アクセサーを自分で実装する場合、プロパティの値を返すだけの単一の式に式本体の定義を使用できます。 `return` ステートメントは使用されません。

次の例では、`Location.Name` プロパティを定義します。このプロパティの get アクセサーは、プロパティをバックするプライベート `locationName` フィールドの値を返します。 

[!code-cs[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

式本体の定義を使用する読み取り専用のプロパティは、明示的な `set` ステートメントなしで実装できます。 構文は次のとおりです。

```csharp
PropertyName => returnValue;
```

次の例では、プライベート `locationName` フィールドの値を返す式本体の定義として読み取り専用の `Name` プロパティを実装する `Location` クラスを定義します。

[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

詳細については、「[プロパティ (C# プログラミング ガイド)](../classes-and-structs/properties.md)」を参照してください。

## <a name="property-set-statements"></a>プロパティの set ステートメント

プロパティの set アクセサーを自分で実装する場合、プロパティをバックするフィールドに値を代入する単一行の式に式本体の定義を使用できます。

次の例では、`Location.Name` プロパティを定義します。このプロパティの set ステートメントで、プロパティをバックするプライベート `locationName` フィールドにその入力引数を代入します。

[!code-cs[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

詳細については、「[プロパティ (C# プログラミング ガイド)](../classes-and-structs/properties.md)」を参照してください。

## <a name="indexers"></a>インデクサー

プロパティと同様に、get アクセサーが値を返す単一のステートメントで構成される場合、または set アクセサーが単純な代入を実行する場合、インデクサーの get と set アクセサーは、式本体の定義で構成されます。

次の例では、`Sports` というクラスを定義します。このクラスには、複数のスポーツ名を含む内部 <xref:System.String> 配列があります。 インデクサーの get および set アクセサーはいずれも、式本体の定義として実装されます。

[!code-cs[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

詳細については、「[インデクサー (C# プログラミング ガイド)](../indexers/index.md)」を参照してください。


