---
title: コード クォート (F#)
description: F# コード クォートを生成して f# のコード式をプログラムで使用することができます、言語の機能を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: a6fab0364cadef1f45276267a59c694140b24a9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564535"
---
# <a name="code-quotations"></a>コード クォート

> [!NOTE]
API リファレンスのリンクをクリックすると MSDN に移動します。  docs.microsoft.com API リファレンスは完全ではありません。

このトピックについて説明*コード クォート*言語の機能を生成し、f# のコード式をプログラムで使用することができます。 この機能では、f# コードを表す抽象構文ツリーを生成できます。 抽象構文ツリーを走査し、アプリケーションのニーズに合わせて処理します。 たとえば、ツリーを使用して、f# コードを生成するか他の言語でコードを生成することができます。


## <a name="quoted-expressions"></a>引用符で囲まれた式
A*式を引用符で囲まれた*は、プログラムの一部としてコンパイルされていない方法で区切られますが、代わりに、f# の式を表すオブジェクトにコンパイルされるコードで f# 式です。 2 つの方法のいずれかで、引用符で囲まれた式をマークすることができます。 型情報または型情報がない場合。 記号を使用する型情報を含める場合は、`<@`と`@>`を引用符で囲まれた式を区切るためにします。 記号を使用する場合は、型情報を使用する必要はありません、`<@@`と`@@>`です。 次のコードでは、型指定された、型指定されていないクォートを示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

大規模な式ツリーを走査するは、高速は、型情報が含まれていない場合です。 型指定されたシンボルを含む引用符で囲まれた式の結果として得られる型は`Expr<'T>`、型パラメーターが、f# コンパイラの型推論アルゴリズムによって決定される式の型。 型情報がないコード クォートを使用する場合、引用符で囲まれた式の型は非ジェネリック型に[Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65)です。 呼び出すことができます、 [Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2)プロパティを型指定された`Expr`させることが、型指定されていないクラス`Expr`オブジェクト。

さまざまなオブジェクトを生成する f# 式プログラム的に処理する静的メソッドがある、`Expr`クラスを使用せずには、式が引用符で囲まれています。

コード クォートが完全な式を含める必要がありますに注意してください。 `let`バインド、たとえば、する必要がありますバインドの名前と、バインディングを使用する追加の式の両方の定義。 冗語構文は、これは依存する式、`in`キーワード。 トップ レベルで、モジュールで、これは、モジュールでは、次の式のみが、引用符内で明示的に必要なします。

したがって、次の式が正しくありません。

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

次の式は無効です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

コード クォートを使用するのには、インポート宣言を追加する必要があります (を使用して、`open`キーワード) を開く、 [Microsoft.FSharp.Quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2)名前空間。

F# PowerPack は、評価および f# 式オブジェクトを実行するためのサポートを提供します。


## <a name="expr-type"></a>Expr 型
インスタンス、`Expr`型が f# の式を表します。 ジェネリックと非ジェネリック`Expr`型が f# ライブラリのドキュメントに記載されています。 詳細については、次を参照してください。 [Microsoft.FSharp.Quotations Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d)と[Quotations.Expr クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d)です。


## <a name="splicing-operators"></a>スプライス演算子
中にスプライスするには、プログラムから、または別のコード クォートから作成した式を持つリテラル コード クォートを結合することができます。 `%`と`%%`演算子を使用すると、コード クォートに f# の式のオブジェクトを追加します。 使用する、`%`型指定された引用符に型指定された式のオブジェクトを挿入する演算子です。 使用する、`%%`演算子は型指定されていないクォートに式の型指定されていないオブジェクトを挿入します。 両方の演算子は、単項プレフィックス演算子です。 したがって場合`expr`型指定されていない式のデータ型は、 `Expr`、次のコードは無効です。

```fsharp
<@@ 1 + %%expr @@>
```

場合`expr`型の型指定された引用符は、 `Expr<int>`、次のコードは無効です。

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>例

### <a name="description"></a>説明
次の例では、式オブジェクトに f# コードを配置し、式を表す f# コードを印刷するコード クォートの使用を示します。 関数`println`が定義されている再帰関数を含む`print`f# の式のオブジェクトを表示する (型の`Expr`) わかりやすい形式でします。 複数のアクティブなパターンがある、 [Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4)と[Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd)モジュール式のオブジェクトを分析するために使用できます。 この例では、f# の式で表示されるすべての可能なパターンは含まれません。 パターン トリガー ワイルドカードのパターンに一致するいずれかの認識できない (`_`) を使用して表示されると、`ToString`メソッドでありで、`Expr`入力と、一致する式を追加するアクティブ パターンを確認できます。


### <a name="code"></a>コード
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet601.fs)]
    
### <a name="output"></a>出力

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>例

### <a name="description"></a>説明
次の 3 つのアクティブなパターンを使用することも、 [ExprShape モジュール](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de)少ないアクティブ パターンの式ツリーを走査します。 これらのアクティブ パターンは、ツリーを走査したいが、ほとんどのノード内のすべての情報が必要ない場合に役に立ちます。 これらのパターンを使用する場合は次の 3 つのパターンのいずれかの任意の f# 式と一致する:`ShapeVar`式が、変数の場合`ShapeLambda`場合は、式は、ラムダ式、または`ShapeCombination`式がそれ以外の場合。 前のコード例のようにアクティブ パターンを使用して式ツリーを走査する場合はすべて可能な f# の式の型を処理する多数の複数のパターンを使用する必要し、コードが複雑になります。 詳細については、次を参照してください。 [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination アクティブ パターン](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d)です。

次のコード例より複雑な走査の基礎として使用できます。 このコードを関数呼び出しを含む式を式ツリーを作成`add`です。 [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d)アクティブ パターンが任意の呼び出しを検出するために使用される`add`式ツリーでします。 このアクティブ パターンへの呼び出しの引数の代入、`exprList`値。 ここでは、ある 2 つだけこれらが引き出されているため、関数の呼び出しの引数に対して再帰的にします。 呼び出しを表すコード クォートに結果が挿入されます`mul`スプライス演算子を使用して (`%%`)。 `println`前の例の関数を使用して、結果を表示します。

その他のアクティブ パターンの分岐で、コードだけを再生成は同じ式ツリーのため結果の式でのみ変更がから変更`add`に`mul`です。


### <a name="code"></a>コード
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]
    
### <a name="output"></a>出力

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

