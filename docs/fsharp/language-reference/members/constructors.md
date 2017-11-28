---
title: "コンストラクター (F#)"
description: "F# でコンス トラクターを使用して作成し、クラスと構造のオブジェクトを初期化および定義する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e0da2250-29de-4145-a1be-e5faff080759
ms.openlocfilehash: 60ed93f1c1dc15e99465d969c9e4fd3e61c28ffa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="constructors"></a>コンストラクター

このトピックでは、定義して作成し、クラスと構造のオブジェクトを初期化するコンス トラクターを使用する方法について説明します。


## <a name="construction-of-class-objects"></a>クラスのオブジェクトの作成
クラス型のオブジェクトでは、コンス トラクターがあります。 2 つの種類のコンス トラクターがあります。 パラメーターが括弧で囲まれて、型名の直後に、プライマリ コンス トラクターは 1 つです。 使用して、他の省略可能な追加のコンス トラクターを指定する、`new`キーワード。 このような追加のコンス トラクターは、プライマリ コンス トラクターを呼び出す必要があります。

プライマリ コンス トラクターを含む`let`と`do`クラス定義の先頭にあるバインディング。 A`let`バインディング クラスのプライベート フィールドおよびメソッドの宣言、`do`バインディングはコードを実行します。 詳細については`let`クラスのコンス トラクター内のバインディングを参照してください[`let`クラス内のバインディング](let-bindings-in-classes.md)です。 詳細については`do`コンス トラクター内のバインディングを参照してください[`do`クラス内のバインディング](do-bindings-in-classes.md)です。

使用してオブジェクトを作成するかどうかを呼び出したいコンス トラクターは、プライマリ コンス トラクターまたは追加のコンス トラクターに関係なく、`new`式、または、省略可能なせず`new`キーワード。 コンマで区切ってと、かっこで囲まれた名前付き引数と値を使用して、かっこで囲むとコンス トラクターの引数、引数の順序で一覧表示するか、オブジェクトを初期化します。 設定することもプロパティがオブジェクトにオブジェクトの構築時にプロパティ名を使用して、コンス トラクターの引数をという名前を使用すると同様に、値を割り当てる.

次のコードでは、クラス コンス トラクターとさまざまなオブジェクトを作成する方法を示しています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

出力は次のとおりです。

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>構造体の構築
構造体では、クラスのすべての規則に従います。 したがって、プライマリ コンス トラクターを持つことができます提供し、追加のコンス トラクターを使用して`new`です。 ただし、構造体とクラスの 1 つの重要な違いがある: プライマリ コンス トラクターが定義されていない場合でも、構造体は既定のコンス トラクター (つまり、引数なしで 1 つ) を持つことができます。 既定のコンス トラクターでは、すべてのフィールドをゼロまたはそれと同等では通常、その型の既定値を初期化します。 コンス トラクターの構造を定義するには、既定のコンス トラクターと競合しないように、少なくとも 1 つの引数にすることが必要です。

また、構造体で多くの場合を使用して作成されたフィールドがある、`val`キーワード; クラスでは、これらのフィールドを持つこともできます。 構造体とクラスを使用して定義されているフィールドを持つ、`val`キーワード初期化することも追加のコンス トラクターでレコードの式を使用して、次のコードに示すようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

詳細については、次を参照してください。[明示的なフィールド:、`val`キーワード](explicit-fields-the-val-keyword.md)です。


## <a name="executing-side-effects-in-constructors"></a>コンス トラクターで実行中の副作用
クラスで、プライマリ コンス トラクター内のコードを実行できる、`do`バインドします。 ただし、ある場合はコードを実行する追加のコンス トラクター、せず、`do`バインドしますか? これを行うには、使用する、`then`キーワード。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

プライマリ コンス トラクターの副作用は引き続き実行します。 したがって、出力は次に示します。

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>コンス トラクター内の自己識別子
他のメンバーには、各メンバーの定義の現在のオブジェクトの名前を指定します。 使用して、クラス定義の最初の行で、自己識別子を配置することもできます、`as`キーワードの直後に次のコンス トラクターのパラメーターです。 次の例では、この構文を示します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

追加のコンス トラクターで定義することも自己識別子を設定することによって、`as`コンス トラクターのパラメーターの直後に句。 次の例では、この構文を示します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

完全に定義する前に、オブジェクトを使用しようとすると、問題が発生することができます。 により、自己識別子を使用できますと、コンパイラ警告が生成され、オブジェクトが初期化される前に、オブジェクトのメンバーがアクセスされないようにする追加のチェックを挿入します。 自己識別子のみを使用する必要があります、`do`または後に、プライマリ コンス トラクターのバインド、`then`追加のコンス トラクター内のキーワードです。

自己識別子の名前がある`this`です。 任意の有効な識別子があります。


## <a name="assigning-values-to-properties-at-initialization"></a>プロパティの初期化時に値を割り当てる
形式の代入の一覧を追加することによって初期化コードでクラスのオブジェクトのプロパティに値を割り当てることができます`property = value`コンス トラクターを引数リストにします。 これを次のコード例に示します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

上記のコードの次のバージョンは、通常の引数、省略可能な引数、および 1 つのコンス トラクターの呼び出しのプロパティの設定の組み合わせを示しています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]
    
## <a name="constructors-in-inherited-class"></a>継承クラスのコンス トラクター
コンス トラクターを持つ基本クラスから継承する、ときに、継承句でその引数を指定する必要があります。 詳細については、次を参照してください。[コンス トラクターと継承](../inheritance.md#constructors-and-inheritance)です。

## <a name="static-constructors-or-type-constructors"></a>静的コンス トラクターまたは型コンス トラクター
静的オブジェクトを作成するためのコードを指定するだけでなく`let`と`do`型レベルでの初期化を実行する型が最初に使用される前に実行するクラス型でバインディングを作成できます。 詳細については、次を参照してください。 [ `let`クラス内のバインディング](let-bindings-in-classes.md)と[`do`クラス内のバインディング](do-bindings-in-classes.md)です。

## <a name="see-also"></a>関連項目
[メンバー](index.md)
