---
title: 制約 (F#)
description: ジェネリック型または関数の型引数の要件を指定してジェネリック型パラメーターに適用される f# 制約について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: f0722cafe27a4e2c38dfbf091973edb136cf5228
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562311"
---
# <a name="constraints"></a>制約

このトピックには、ジェネリックに適用可能な制約がについて説明します、ジェネリック型または関数の型引数の要件を指定するパラメータを入力します。


## <a name="syntax"></a>構文

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>コメント
これは、いくつかのさまざまな制約を適用すると、ジェネリック型に使用できる型を制限することができます。 次の表は、これらの制約の一覧です。

|制約|構文|説明|
|----------|------|-----------|
|型の制約|*型パラメーター* :&gt; *型*|指定された型は、指定した型から同じかまたは派生をする必要がありますか、型がインターフェイスの場合は、指定された型がインターフェイスを実装する必要があります。|
|Null の制約|*型パラメーター* : null|指定された型は、null リテラルをサポートする必要があります。 これには、すべて .NET オブジェクトの種類がない f# 一覧、タプル、関数、クラス、レコード、または共用体の型が含まれます。|
|明示的なメンバーの制約|[(]*型パラメーター* [または... または*型パラメーター*)]: (* メンバー シグネチャ *)|指定された型引数の少なくとも 1 つを指定の署名を持つメンバーがあります。一般的な用途のものでありません。 メンバー必要がありますか、明示的に定義する、明示的なメンバーの制約の有効なターゲットにするには、型または暗黙的な型の拡張機能の一部にできます。|
|コンス トラクターの制約|*型パラメーター* : (新しい: 単位 -&gt; ' を)|指定された型は、既定のコンス トラクターをいる必要があります。|
|値型の制約|: 構造体|指定された型は、.NET 値型である必要があります。|
|参照型の制約|: 構造体ではありません|指定された型は、.NET 参照型である必要があります。|
|列挙型の制約|: enum&lt;*基になる型*&gt;|指定された型を指定した基になる型を持つ列挙型である必要があります。一般的な用途のものでありません。|
|デリゲートの制約|: 委任&lt;*組パラメーター型*、*戻り値の型*&gt;|指定された型必要がありますを指定した引数を持つデリゲート型であるし、戻り値一般的な用途のものでありません。|
|比較の制約|: 比較|指定された型は、比較をサポートする必要があります。|
|等しいかどうかの制約|: 等しいかどうか|指定された型は、等しいかどうかをサポートする必要があります。|
|アンマネージの制約|: 管理されていません。|指定された型は、アンマネージ型にする必要があります。 アンマネージ型は、プリミティブ型 (`sbyte`、 `byte`、 `char`、 `nativeint`、 `unativeint`、 `float32`、 `float`、 `int16`、 `uint16`、 `int32`、 `uint32`、 `int64`、 `uint64`、または`decimal`)、列挙型、 `nativeptr&lt;_&gt;`、またはその結果、フィールドはすべてのアンマネージ型の非ジェネリック構造体。|
利用可能な制約の種類は型でない、一般に、機能を使用するコードがある場合は、制約を追加する必要があります。 たとえば、クラス型を指定する型の制約を使用する場合は、ジェネリック関数またはジェネリック型では、そのクラスのメソッドのいずれかを使用できます。

制約を指定する場合があります必要な型パラメーターを明示的に記述する場合、制約、コンパイラがあるないためを使用している機能が実行時の種類を指定する場合がある任意の型で使用できることを確認する方法パラメーター。

F# コードで使用する最も一般的な制約は、基底クラスまたはインターフェイスを指定する型の制約です。 その他の制約が f# ライブラリでの算術演算子のオーバー ロードする演算子を実装するために使用または主に f# をサポートするための完全な指定が明示的なメンバー制約などの特定の機能を実装するか、使用します。共通言語ランタイムでサポートされている制約のセット。

型の推論プロセス中にいくつかの制約は、コンパイラによって自動的に推論されます。 たとえば、使用する場合、`+`関数に演算子は、コンパイラは、明示的なメンバーの制約式で使用されている変数の型を推測します。

次のコードは、いくつか制約宣言を示しています。

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> = 
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with static member
type Class4<'T when 'T : (static member staticMethod1 : unit -> 'T) > =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a>関連項目
[ジェネリック](index.md)

[制約](constraints.md)
