---
title: プロパティ (F#)
description: F# のプロパティはオブジェクトに関連付けられている値を表すメンバーについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 7aa71b1801b44fedcb420b824078004c6c240dc2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="properties"></a>プロパティ

*プロパティ*オブジェクトに関連付けられている値を表すメンバーであります。


## <a name="syntax"></a>構文

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a>コメント
プロパティは、"が、"オブジェクト インスタンスにして、または静的なプロパティを型と関連付けられているデータを表す、オブジェクト指向のプログラミングのリレーションシップ。

によっては、プロパティを基になる値 (バッキング ストアとも呼ばれます) を明示的に指定するかどうかや、コンパイラが自動的に生成するため、バッキング ストアを許可するかどうかは、次の 2 つの方法でプロパティを宣言することができます。 一般に、プロパティが値または変数の単純なラッパーだけの場合は、プロパティに重要な実装がある場合より明示的方法、および自動方法を使用します。 プロパティを明示的に宣言するを使用して、`member`キーワード。 この宣言の構文を指定する構文に続けて、`get`と`set`もという名前のメソッド*アクセサー*です。 読み取り/書き込み、書き込み専用、読み取り専用プロパティでは、さまざまな形式の「構文」セクションに示すように明示的な構文が使用されます。 読み取り専用のプロパティを定義するのみ、`get`メソッドです。 書き込み専用のプロパティの定義のみ、`set`メソッドです。 プロパティがある両方と`get`と`set`のアクセサーを別の構文を使用する属性とは、次のコードに示すように、アクセサーごとに異なるアクセシビリティ修飾子を指定します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

読み取り/書き込みプロパティで両方の`get`と`set`メソッドの順序`get`と`set`元に戻すことができます。 またはに示される構文を提供できます`get`だけに示される構文と`set`結合構文を使用する代わりにのみです。 これを簡単をコメント アウト個人`get`または`set`メソッド、何を行う必要がありますかである場合。 結合の構文を使用してこの代替手順は、次のコードに表示されます。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

プライベート値をその保留中のプロパティのデータと呼びます*バッキング ストア*です。 コンパイラのバッキング ストアを自動的に作成するのには、キーワードを使用して`member val`、自己の id を省略し、プロパティを初期化する式を指定します。 プロパティを変更可能である場合は、含める`with get, set`です。 たとえば、次のクラス型には、自動的に実装された 2 つのプロパティが含まれています。 `Property1` 読み取り専用とは、プライマリ コンス トラクターに渡される引数に初期化し、`Property2`は空の文字列に初期化される設定可能なプロパティ。

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

自動実装プロパティと同じように他のメンバー定義の前に含める必要がありますので、型の初期化の一部である`let`バインドと`do`種類の定義のバインディングです。 自動的に実装されたプロパティを初期化する式は初期化時に、およびプロパティがアクセスされるたびにないをのみ評価されることに注意してください。 この動作では、明示的に実装されたプロパティの動作とは対照的です。 どのような実質的には、これらのプロパティを初期化するコードは、クラスのコンス トラクターに追加されます。 この違いを表示する次のコードを考慮してください。

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

**出力**

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

AutoProperty の値変更されていないことと、繰り返し呼び出したときに、ExplicitProperty 呼び出されるたびに変更が上記のコードの出力を示しています。 これを示します自動的に実装されたプロパティの式では、毎回は評価されません明示的なプロパティの get アクセス操作子メソッドが格納されます。


>[!WARNING]
Entity Framework など、一部のライブラリがある (`System.Data.Entity`) 自動的に実装されたプロパティの初期化とうまく連携する基本クラス コンス トラクターのカスタム操作を実行します。 その場合は、明示的なプロパティを使用して、やり直してください。

プロパティは、クラス、構造体、判別共用体、レコード、インターフェイス、および型の拡張機能のメンバーであることができ、オブジェクト式で定義することもできます。

属性は、プロパティに適用できます。 プロパティに属性を適用するには、プロパティの前に別の行に属性を記述します。 詳細については、「[属性](../attributes.md)」を参照してください。

既定では、プロパティはパブリックです。 アクセシビリティ修飾子は、プロパティにも適用できます。 アクセシビリティ修飾子を適用するプロパティの名前の直前に場合追加両方に適用するものでは、`get`と`set`メソッドです追加する前に、`get`と`set`異なるアクセシビリティがある場合のキーワード。各アクセサーが必要です。 *アクセシビリティ修飾子*、次のいずれかになります: `public`、 `private`、`internal`です。 詳細については、「[Access Control](../access-control.md)」(アクセス制御) を参照してください。

プロパティの実装は、プロパティがアクセスされるたびに実行されます。


## <a name="static-and-instance-properties"></a>静的なインスタンスのプロパティと
プロパティでは、静的したり、プロパティをインスタンス化することができます。 静的プロパティは、インスタンスなしで呼び出すことができ、個々 のオブジェクトではなく、型に関連付けられている値に使用されます。 静的プロパティは、自己識別子を省略します。 自己識別子は、インスタンスのプロパティに必要です。

次の静的プロパティの定義がする必要がある静的フィールド シナリオに基づいて`myStaticValue`プロパティのバッキング ストアはします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

プロパティも指定できます配列に似たが呼び出された場合*インデックス付きプロパティ*です。 詳細については、次を参照してください。[インデックス付きプロパティ](indexed-properties.md)です。


## <a name="type-annotation-for-properties"></a>プロパティの型の注釈
多くの場合、コンパイラは、バッキング ストアの種類のプロパティの型を推論するのに十分な情報が型の注釈を追加することで、型を明示的に設定することができます。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>Set アクセサーのプロパティを使用します。
提供するプロパティを設定することができます`set`アクセサーを使用して、`<-`演算子。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

出力は**20**です。


## <a name="abstract-properties"></a>抽象プロパティ
プロパティは、抽象であることができます。 メソッドを使って、`abstract`だけプロパティに関連付けられている仮想ディスパッチがあることを意味します。 抽象プロパティ抽象化できるの本当は、同じクラスで定義されています。 このようなプロパティを含むクラスは抽象クラスではこのためです。 代わりに、抽象できますだけという意味では、定義が同じクラス内に存在する必要がありますの場合は、そのプロパティが、仮想です。 抽象プロパティをプライベートにすることはできません、1 つのアクセサーが抽象の場合は、他の必要がありますも抽象にすることに注意してください。 抽象クラスの詳細については、次を参照してください。[抽象クラス](../abstract-classes.md)です。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>関連項目
[メンバー](index.md)

[メソッド](methods.md)
