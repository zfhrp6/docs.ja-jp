---
title: let 束縛 (F#)
description: F# の 'let' 束縛で、値または関数関連付け識別子を使用する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: bcdf01747c2a1d0ba9a894188dae1d42acdf9104
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="let-bindings"></a>let 束縛

A*バインディング*を値または関数識別子を関連付けます。 使用する、`let`値または関数に名前をバインドするキーワードです。

## <a name="syntax"></a>構文

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>コメント

`let`バインディング値または関数名の値を 1 つまたは複数定義する式でキーワードを使用します。 最も単純な形式、`let`式に名前をバインド単純な値では、次のようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

新しい行を使用して、識別子から式を分離する場合は、次のコードのように、式の各行をインデントする必要があります。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

名前だけではなく名前を含むパターンを指定できますが、たとえば、組、次のコードに示すようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

*式本体*名前を使用する式です。 最初の文字と正確に一致を行にインデント、独自の行に式の本体が表示されます、`let`キーワード。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

A`let`バインディング表示できる、クラス型の定義またはローカルのスコープで、モジュール レベルで関数定義のようです。 A`let`最上位レベルのモジュール内、またはクラス型のバインディングは、式の本体がある必要はありませんが、他のスコープ レベルで式の本体が必要です。 バインドされる名前を使用する前に、任意の時点ではなくが、定義の時点より後、`let`バインディングが表示されたら、次のコードに示すようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]
    
## <a name="function-bindings"></a>関数のバインディング

関数バインドは、次のコードに示すように関数名とパラメーターを関数バインドが含まれる点を除いて値のバインディングの規則を適用します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

一般に、パラメーターは、タプル パターンなどのパターンです。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

A`let`最後の式の値に評価される式をバインドします。 そのため、次のコード例の値では`result`から計算された`100 * function3 (1, 2)`に評価される`300`です。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

詳細については、「[関数](index.md)」を参照してください。

## <a name="type-annotations"></a>型の注釈

続けてかっこで囲まれたすべての種類名、コロン (:) を含めることによって、型パラメーターを指定できます。 最後のパラメーターの後にコロンと型を追加することによって、戻り値の型を指定することもできます。 完全な型の注釈に`function1`パラメーター型として整数となる次のようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

明示的な型パラメーターがない場合は、型の推論は関数のパラメーターの種類の決定に使用されます。 これは、ジェネリックにするパラメーターの型を自動的に一般化するとを含めることができます。

詳細については、次を参照してください。[自動ジェネリック化](../generics/automatic-generalization.md)と[型の推論](../type-inference.md)です。

## <a name="let-bindings-in-classes"></a>クラス内の let 束縛

A`let`バインディングは、構造体またはレコードの種類ではなく、クラス型でに表示されることができます。 Let クラス型のバインディングを使用するのには、プライマリ コンス トラクターがクラスにあります。 コンス トラクターのパラメーターは、クラス定義の型名の後に必要です。 A`let`クラス型でのバインディングは、プライベート フィールドとそのクラスの種類と、と共にメンバーを定義します。`do`型、バインド フォームのコードの種類のプライマリ コンス トラクターをします。 次のコード例は、クラスを表示する`MyClass`プライベート フィールドを持つ`field1`と`field2`です。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

スコープ`field1`と`field2`は宣言されている型に制限されます。 詳細については、次を参照してください。 [ `let`クラス内のバインディング](../members/let-bindings-in-classes.md)と[クラス](../classes.md)です。

## <a name="type-parameters-in-let-bindings"></a>型パラメーターの let 束縛

A`let`型、またはコンピュテーション式で、モジュール レベルでのバインディングは、明示的な型パラメーターを持つことができます。 Let 関数定義内でようにバインディングを式では、型パラメーターを持つことはできません。 詳細については、「[ジェネリック](../generics/index.md)」を参照してください。

## <a name="attributes-on-let-bindings"></a>属性の let 束縛

属性は、最上位レベルに適用できる`let`モジュールの場合、次のコードに示すようにバインドします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]
    
## <a name="scope-and-accessibility-of-let-bindings"></a>スコープと使用すると、バインドのユーザー補助機能

使用すると、バインドで宣言されたエンティティのスコープを含むの部分に制限されます (など、関数、モジュール、ファイルまたはクラス) スコープの後、バインドが表示されます。 そのため、そのことが言えますを使用すると、バインドで名前をスコープ。 モジュールでの let-bound 値または関数は、モジュールのクライアントからアクセス モジュールで使用すると、バインディングは、モジュールのパブリックの関数にコンパイルされるため、モジュールにアクセスできる限りです。 これに対し、クラスで使用すると、バインディングは、クラスにプライベートです。

通常、モジュール内の関数は、クライアント コードで使用する場合、モジュールの名前で修飾する必要があります。 たとえば、モジュール`Module1`関数`function1`、ユーザーは指定`Module1.function1`関数を参照します。

モジュールのユーザーは、インポート宣言を使用して、モジュール名によって修飾されることがなくそのモジュール内の関数を使用できるようにすることがあります。 説明した例では、モジュールのユーザー開くことができる場合は、モジュールのインポート宣言開くを使用して、`Module1`し、その後を参照してください`function1`直接です。

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

モジュールの一部が属性を持つ[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)、つまり、モジュールの名前、公開された関数を修飾する必要があります。 たとえば、f# List モジュールには、この属性があります。

モジュールとアクセス制御の詳細については、次を参照してください。[モジュール](../modules.md)と[アクセス制御](../access-control.md)です。

## <a name="see-also"></a>関連項目

[関数](index.md)

[クラス内の `let` バインド](../members/let-bindings-in-classes.md)
