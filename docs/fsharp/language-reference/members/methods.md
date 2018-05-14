---
title: メソッド (F#)
description: F# メソッドは公開し、オブジェクトと型の動作と機能の実装に使用される型に関連付けられている関数、方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 6e0b0789d97a9671425fb08c56c84ba1f66dfbe6
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2018
---
# <a name="methods"></a>メソッド

A*メソッド*型に関連付けられている関数です。 オブジェクト指向プログラミングで公開し、オブジェクトと型の動作と機能を実装するメソッドを使用します。


## <a name="syntax"></a>構文

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-nameparameter-list [ : return-type ]=
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member self-identifier.method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member [inline] self-identifier.method-name : type-signature
[ attributes ]
default [inline] self-identifier.method-nameparameter-list[ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue([ default-value ])>] input) [ : return-type ]
```

## <a name="remarks"></a>コメント
前の構文では、メソッドの宣言と定義のさまざまなフォームを表示できます。 長いメソッド本体では、改行されるように、等号 (=) と、メソッド本体の全体がインデントされます。

属性は、メソッド宣言に適用できます。 メソッド定義の構文の前に、通常別々 の行に一覧表示されます。 詳細については、「[属性](../attributes.md)」を参照してください。

メソッドをマークする`inline`です。 `inline` の詳細については、「[Inline Functions](../functions/inline-functions.md)」(インライン関数) を参照してください。

非インライン メソッドは、型内で再帰的に使用できます。明示的に使用する必要はありません、`rec`キーワード。


## <a name="instance-methods"></a>インスタンス メソッド
インスタンス メソッドを宣言すると、`member`キーワードと*自己識別子*、その後にピリオド (.) とメソッド名とパラメーター。 場合と同様`let`、バインド、*パラメーター リスト*パターンを指定できます。 通常、他の .NET Framework 言語で作成されるときに、f# で方法は、組の形式でのかっこ内のパラメーターの表示方法を囲みます。 ただし、カリー化されたフォーム (パラメーターはスペースで区切られた) は一般的でも、その他のパターンもサポートされます。

次の例は、定義とインスタンスの非抽象メソッドの使用方法を示しています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

インスタンス メソッド内で使用すると、バインディングを使用して定義されているフィールドにアクセスする、自己識別子を使用しないでください。 その他のメンバーとプロパティにアクセスするときに、自己識別子を使用します。


## <a name="static-methods"></a>静的メソッド
キーワード`static`なしインスタンス メソッドで呼び出されることを指定するために使用して、オブジェクトのインスタンスに関連付けられていません。 それ以外の場合、メソッドは、インスタンス メソッドです。

次のセクションの例で宣言したフィールドを示しています、`let`キーワードで宣言されたプロパティのメンバー、`member`キーワード、および静的メソッドで宣言された、`static`キーワード。

次の例では、定義と静的メソッドの使用方法を示します。 これらのメソッドの定義であると仮定、`SomeType`前のセクション内のクラスです。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>抽象メソッドと仮想メソッド
キーワード`abstract`メソッドが仮想ディスパッチ スロットを持つクラスの定義がないことを示します。 A*仮想ディスパッチ スロット*はオブジェクト指向の種類での仮想関数を検索する実行時に使用される関数の内部で維持されるテーブルのエントリの呼び出しです。 この仮想ディスパッチ メカニズムを実装するメカニズム*ポリモーフィズム*、オブジェクト指向プログラミングの重要な機能です。 定義のない 1 つ以上の抽象メソッドを持つクラスは、*抽象クラス*、つまり、そのクラスのインスタンスを作成できないことができます。 抽象クラスの詳細については、次を参照してください。[抽象クラス](../abstract-classes.md)です。

抽象メソッドの宣言は、メソッド本体を含めないでください。 代わりに、メソッドの名前は後にコロン (:) と、メソッドの型のシグネチャ。 メソッドの型署名は、一時停止する、マウス ポインター、Visual Studio コード エディターで、メソッド名の上を除くパラメーターの名前のないときに、IntelliSense によって表示と同じです。 型のシグネチャは、対話形式で作業している場合に、インタープリター fsi.exe によって表示されます。 メソッドの型署名は、戻り値の型の適切な区切り記号の後に、パラメーターの型を一覧することにより形成されます。 カリー化されたパラメーターを指定する`->`組パラメーターを指定して`*`です。 戻り値は、引数から分離常に、`->`シンボル。 関数の型が、パラメーターの場合など、複雑なパラメーターをグループ化するかを示す 2 つのパラメーターではなく、単一のパラメーターとしてに組を処理するときに、かっこを使用できます。

付けることも抽象メソッド default 定義をクラスに定義を追加し、使用して、`default`キーワード、構文のブロックをこのトピックで示すようにします。 同じクラスの定義を持つ抽象メソッドは、他の .NET Framework 言語で、仮想メソッドと同じです。 定義が存在するかどうか、`abstract`キーワードがクラスの仮想関数テーブルに新しいディスパッチ スロットを作成します。

かどうかを基本クラスでは、その抽象メソッドを実装に関係なく、派生クラスは抽象メソッドの実装を提供できます。 派生クラスで抽象メソッドを実装するを使用する以外、派生クラスで、同じ名前およびシグネチャを持つメソッドを定義、`override`または`default`キーワード、メソッド本体を指定します。 キーワード`override`と`default`まったく同じことを意味します。 使用して`override`新しいメソッドが、基本クラス実装をオーバーライドする場合を使用して`default`元の抽象宣言と同じクラスの実装を作成するとします。 使用しないで、`abstract`抽象基本クラスで宣言されたメソッドを実装するメソッドではキーワードです。

次の例は、抽象メソッドを示しています。`Rotate`を持つ既定の実装では、.NET Framework の仮想メソッドに相当します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

次の例では、基底クラス メソッドをオーバーライドする派生クラスを示します。 この場合、オーバーライドでは、何も実行されるように動作が変わります。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>オーバーロードされたメソッド
オーバー ロードされたメソッドは、メソッドと同じ名前で、指定された型が異なる引数を持つことです。 F# で省略可能な引数は通常、オーバー ロードされたメソッドの代わりに使用します。 ただし、オーバー ロードされたメソッドは、する引数はタプル形式、いないカリー化されたフォームが言語で許可されます。

## <a name="optional-arguments"></a>省略可能な引数

4.1 以降では f#、メソッドでパラメーターの既定値と省略可能な引数もができます。  これは、c# コードとの相互運用を容易にするためです。  次の例では、構文を示しています。

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

渡された値を`DefaultParameterValue`入力の型が一致する必要があります。  上記のサンプルでは、`int`です。  整数以外の値を渡そうと`DefaultParameterValue`コンパイル エラーになります。

## <a name="example-properties-and-methods"></a>例: プロパティとメソッド
次の例には、フィールド、プライベート関数、プロパティ、および静的メソッドの例を含む型が含まれています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>関連項目
[メンバー](index.md)
