---
title: F# のツアー
description: F# のプログラミング言語のコード サンプルを使ってこのツアーでの主な機能のいくつかを確認します。
ms.date: 02/28/2018
ms.openlocfilehash: 2ce251b90d5c202996e0b1673e8f7f378a38af5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="tour-of-f"></a>F# のツアー #

F# について学習する最善の方法では、f# コードを読み書きします。  この記事は、f# 言語の主な機能の一部の機能を確認として機能し、コンピューターに対して実行できます。 一部のコード スニペットでわかります。  詳細については、開発環境をセットアップして、チェック アウト[作業の開始](tutorials/getting-started/index.md)です。

F# である 2 つの主要な概念: 関数と型。  このツアーはこれら 2 つの概念には、言語の機能を強調します。

## <a name="functions-and-modules"></a>関数とモジュール

任意の f# プログラムの最も基本的な部分が***関数***に編成***モジュール***です。  [関数](language-reference/functions/index.md)の入力、出力を生成するために作業を実行し、下では、編成された[モジュール](language-reference/modules.md)、f# で作業をグループ化する主要な手段であります。  使用して定義されている、 [ `let`バインディング](language-reference/functions/let-bindings.md)関数の名前し、その引数を定義します。

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

`let` バインドも値を他の言語での変数のような名前にバインドする方法です。  `let` バインディングは***不変***既定では、値または関数が名前にバインドされると、それを変更できないことを意味するインプレースでします。  これは、他の言語は、変数とは対照的***変更可能な***時間で任意の時点でその値の意味を変更できます。  変更可能なバインディングを必要とする場合を使用できます`let mutable ...`構文です。

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>数値、ブール値、および文字列

.NET 言語として f# をサポートしている同じ基になる[プリミティブ型](language-reference/primitive-types.md).NET 内に存在します。

F# でさまざまな数値型の表現を次に示します。

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

ここでは、どのようなブール値と次のように基本的な条件付きロジックを実行します。

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

ここではどのような basic[文字列](language-reference/strings.md)次のように操作します。

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>タプル

[組](language-reference/tuples.md)f# では大きな問題は、します。  これらは、名前のない、順序付きの値は、特定の値として扱うことのグループです。  これらの集計される、その他の値からの値として考えます。  判別しやすいように、関数から複数の値を返すまたはアドホック利便性の値をグループ化など、数多くの用途があります。

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

F# 4.1、時点で作成することも`struct`組。  これらと相互運用も完全にも C# 7 または Visual Basic の 15 の組`struct`組。

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

ことに注意することが重要`struct`組が値型、タプルを参照する暗黙的に変換することはできませんまたはその逆です。  参照と構造体の組の間で明示的に変換する必要があります。

## <a name="pipelines-and-composition"></a>パイプラインおよびコンポジション

パイプ演算子 (`|>`、 `<|`、 `||>`、 `<||`、 `|||>`、 `<|||`) と合成演算子 (`>>`と`<<`) の使用頻度が f# でのデータを処理するときにします。  これらの演算子は、柔軟な方法で「パイプライン」関数を確立するために使用できる関数です。  次の例は、どのようにこれらの演算子のパイプラインを構築する単純な機能の利点がかかる場合があります手順について説明します。

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L300)]

行われた上記のサンプルの f#、リストの処理機能、ファースト クラスの関数を含む多数の機能の使用と[部分適用](language-reference/functions/index.md#partial-application-of-arguments)です。  これらの概念のそれぞれの深い理解がやや高度なことができますになる、ことがありますクリア関数を使用して、パイプラインを構築するときに、データを処理する方法に簡単にします。

## <a name="lists-arrays-and-sequences"></a>リスト、配列、およびシーケンス

リスト、配列、およびシーケンスは、f# コア ライブラリの次の 3 つの主なコレクション型です。

[一覧表示](language-reference/lists.md)は同じ型の要素の順序付けられ、変更できないコレクションです。  シングル リンク リスト、大規模な場合、列挙がランダム アクセスと連結に適さないのために用意されていることを意味します。  これは通常のリストを表すシングル リンク リストを使用しないでください、人気のある他の言語のリストとは対照的です。

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

[配列](language-reference/arrays.md)が固定サイズ、*変更可能な*同じ型の要素のコレクション。  要素の高速なランダム アクセスをサポートし、F# では単に連続するメモリ ブロックのためのリストよりも高速です。

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

[シーケンス](language-reference/sequences.md)要素は、すべて同じ型の一連の論理がします。  これらは、リストや配列、任意の論理一連の要素に、"view"することのできるよりもより一般的な型です。  目立つことができるので***レイジー***、つまり、必要な場合にのみ要素を計算することができます。

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>再帰関数

コレクションまたは要素のシーケンスの処理は、普通で[再帰](language-reference/functions/index.md#recursive-functions)f# でします。  F# がループと命令型プログラミングのサポートがありますが、再帰が優先正確性を保証する方が簡単です。

>[!NOTE]
次の例を使用してパターン マッチを利用、`match`式。  この基本的な構造は、この記事で後述について説明します。

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

F# でも末尾呼び出しの最適化で完全にサポートされるされてがループ構造と同じ速度で単なるように、再帰呼び出しを最適化する方法です。

## <a name="record-and-discriminated-union-types"></a>レコードと判別された共用体型

レコードと、共用体の型は f# コードで使用される 2 つの基本的なデータ型、f# のプログラムでデータを表現する最善の方法では、通常  このため、クラスのような他の言語で、構造の等値セマンティクスがあることの主な相違点の 1 つです。  つまり、「ネイティブ」比較が等しいかどうかは簡単です - 1 つが、互いに等しいかどうかはチェックします。

[レコード](language-reference/records.md)は省略可能なメンバー (メソッド) などで、名前付きの値の集計です。  C# や Java に慣れている場合、これら必要がありますと思われるした poco からまたは Pojo - と同様に構造の等価と手続きだけです。

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

F# 4.1、時点では、レコードとしても表すことができる`struct`s。  これは、`[<Struct>]`属性。

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

[判別共用体 (Du)](language-reference/discriminated-unions.md)名前付きのフォームまたはケースの数を生じる可能性がある値が格納されています。  型に格納されたデータには、個別の値をいくつかのいずれかを指定できます。

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

として Du を使用することもできます。*単一ケースの判別共用体*、プリミティブ型をモデリングするドメインを支援します。  多くの場合、文字列およびその他のプリミティブ型、何かを表すために使用し、特定の意味を指定されたためです。  ただし、データのプリミティブ形式のみを使用する可能性が誤って正しくない値を割り当てるときに!  個別の単一ケース共用体の情報の各型を表すと、このシナリオでは、正しいかどうかを適用できます。

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

単一ケース判別共用体、基になる値を取得する、上記のサンプルに示すように明示的に unwrap する必要があります。

さらに、Du もサポートして再帰的な定義ツリーと本質的に再帰型データを簡単に記述することができます。  たとえば、ここでは方法でのバイナリ検索ツリーを表すことができる`exists`と`insert`関数。

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

Du を使用すると、データ型にツリーを再帰的な構造を表すできますが、この再帰的な構造で動作している単純ではいて正確性を保証します。  次のようにも、パターン マッチでサポートされます。

さらに、として Du を表すことができる`struct`で秒、`[<Struct>]`属性。

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

ただし、これを実施する際に注意する 2 つの主な操作があります。

1. DU 構造体は、再帰的に定義することはできません。
2. DU 構造体には、そのケースのそれぞれに一意の名前が必要です。

上記に従わないと、コンパイル エラーが発生します。

## <a name="pattern-matching"></a>パターン マッチ

[パターン マッチ](language-reference/pattern-matching.md)f# の型に対する操作のための正確性をできる f# 言語機能します。  上記のサンプルからもわかるように相当量の`match x with ...`構文です。  このコンストラクトは、コンパイラは、排他的なパターン一致としてを介して、既知のデータ型を使用する場合は、可能なすべてのケースのアカウントを強制するには、データ型の"shape"を理解することができます。  これは正しいかどうか、非常に強力であり、コンパイル時にランタイム問題になる新機能は通常「リフト」に適切に使用できます。

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L739)]

短縮形を使用することもできます`function`のまま続行する関数を使用して作成する場合に有用なパターンに一致させるためのコンストラクト[部分適用](language-reference/functions/index.md#partial-application-of-arguments):。

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L741-L759)]

使用に問題がありますが、`_`パターン。  これと呼ばれますが、[ワイルドカード パターン](language-reference/pattern-matching.md#wildcard-pattern)、「関係ない何かが」という方法であります。  、は便利ですが排他的なパターン マッチを誤ってバイパスおよび不要になったコンパイル時の実施恩恵を使用して注意が必要でない場合`_`です。  分解された型の特定部分を考慮しない場合に最も使用される照合、または最後の句のパターン マッチ式内のすべての意味のあるケースを列挙したときとパターンします。

[アクティブ パターン](language-reference/active-patterns.md)パターン マッチで使用する別の強力な構造は、します。  パターン一致の呼び出しサイトでそれらを分解する、カスタムのフォームに入力データを分割できます。  パラメーター化できる、ため、関数として、パーティションを定義することができます。  アクティブ パターンをサポートするために、前の例を展開する次のようになります。

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L761-L783)]

## <a name="optional-types"></a>省略可能な型

判別共用体の型の 1 つの特殊なケースは、オプション型、これは、f# コア ライブラリの一部であるために便利です。

[オプションの種類](language-reference/options.md)は 2 つのケースのいずれかを表す型です: 値、またはまったく何も行われません。  値が可能性がありますか、特定の操作からされないことがあるシナリオでも使用されます。  これによって強制すると、アカウントのどちらの場合も、実行時の問題ではなく、コンパイル時の問題になります。  Api でよく使用されます、`null`について心配する必要があるのでを代わりに、"nothing"を表すため`NullReferenceException`多くの場合。

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L791-L811)]

## <a name="units-of-measure"></a>測定単位

# の型システムの固有の機能の 1 つは、メジャーの単位を数値リテラルのコンテキストを提供する機能です。

[測定単位](language-reference/units-of-measure.md)メートルなどの単位に数値型を関連付けること許可し、関数作業を実行数値リテラルではなく、単位にします。  これにより、コンパイラに渡された数値リテラルの種類を特定のコンテキストでなします、その作業の種類に関連付けられている実行時エラーがなくなることを確認できます。

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L818-L839)]

F# コア ライブラリは、多くの SI 単位の種類と単位の変換を定義します。  詳細については、チェック アウト、 [Microsoft.FSharp.Data.UnitSystems.SI Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d)です。

## <a name="classes-and-interfaces"></a>クラスとインターフェイス

F# でも、.NET クラスの完全なサポート[インターフェイス](language-reference/interfaces.md)、[抽象クラス](language-reference/abstract-classes.md)、[継承](language-reference/inheritance.md)のようにします。

[クラス](language-reference/classes.md).NET オブジェクトを表す型が持つことができるプロパティ、メソッド、およびイベントとしてその[メンバー](language-reference/members/index.md)です。

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L848-L877)]

ジェネリック クラスの定義も非常に単純です。

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L884-L905)]

インターフェイスを実装する、いずれかを使用できる`interface ... with`構文または[オブジェクト式](language-reference/object-expressions.md)です。

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L912-L931)]

## <a name="which-types-to-use"></a>使用する型

クラス、レコード、判別共用体、および組の存在は、重要な質問につながりますこれを使用しますか?。  ほとんどの環境で、すべてのように、応答は、状況に依存します。

組は、関数から複数の値を返すと自体を値として、アドホック集計値の集計を使用するのに適しています。

レコードは、"からのステップ アップ"組、ラベルと省略可能なメンバーのサポートを持つという名前です。  データ転送中のプログラムの実行の低手続き表現に最適です。  構造の等価性があるため、比較が簡単に使用されます。

判別共用体多く、用途がありますが、主要な利点は、すべての可能な「図形」データを持つことができるアカウントに一致するパターンと組み合わせて利用することができます。  

クラスは、情報を表すしても機能するには、その情報を関連付ける必要がある場合などの理由の数が膨大に最適です。  原則として、としては、概念的には、一部のデータに関連付けられている機能がある場合は大きな利点にはクラスとオブジェクト指向プログラミングの原則を使用してます。  クラスも推奨されるデータ型 c# と Visual Basic の相互運用時にこれらの言語は、ほぼすべてのクラスを使用。

## <a name="next-steps"></a>次の手順

これで、言語の主な機能の一部を説明しました、する必要があります、最初の f# プログラムを作成する準備完了!  チェック アウト[作業の開始](tutorials/getting-started/index.md)を開発環境を設定して、コードを記述する方法を参照してください。

お好きなよう、さらに詳しく学習の次の手順を指定できますが、ことをお勧め[ファースト クラス値として機能](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming in F#](introduction-to-functional-programming/index.md)-->コア関数型プログラミングの概念には慣れてを取得します。  これらは、f# で堅牢なアプリケーションの構築に不可欠なされます。

また、チェック アウト、 [f# 言語リファレンス](language-reference/index.md)を f# の包括的な概念説明のコレクションを参照してください。
