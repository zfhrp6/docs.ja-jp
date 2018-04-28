---
title: フレキシブル型 (F#)
description: F# で柔軟性のある型の注釈、パラメーター、変数、または値型である、指定した型と互換性があることを示します。 これを使用する方法を説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: bee2364a6c30b1fbdc09aa0aac2249e3f0c295e8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="flexible-types"></a>フレキシブル型

A*柔軟型の注釈*パラメーター、変数、または値型である、互換性のある種類を指定して互換性をクラスまたはインターフェイスのオブジェクト指向の階層内の位置を決定する場所を示します。 フレキシブル型は、型階層で上位の型への自動変換は発生しませんが、階層内の任意の型またはインターフェイスを実装する任意の型を使用するの機能を有効にする場合に特に便利です。

## <a name="syntax"></a>構文

```fsharp
#type
```

## <a name="remarks"></a>コメント

前の構文で*型*基本型またはインターフェイスを表します。

柔軟な型では、基本またはインターフェイス型と互換性がある型に許可されている型を制限する制約を持つジェネリック型に相当します。 つまり、次の 2 つのコード行は等価です。

```fsharp
#SomeType

'T when 'T :> SomeType
```

フレキシブル型は、さまざまな状況で役立ちます。 たとえば、高階関数 (関数を引数として受け取る関数) がある場合は、ときに、便利ですに柔軟な型を返す関数。 次の例ではシーケンス引数を持つ柔軟な型の使用で`iterate2`シーケンス、配列、リスト、およびその他の列挙可能な型を生成する関数を使用する、高階関数を有効にします。

次の 2 つ関数、柔軟な型を返しますが、その他のシーケンスを返すのいずれかを検討してください。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

別の例として、 [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712)ライブラリ関数。

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

次の列挙可能なシーケンスのいずれかは、この関数に渡すことができます。

- リストの一覧
- 配列の一覧
- リストの配列
- シーケンスの配列
- 列挙可能なシーケンスの他の任意の組み合わせ

次のコードでは`Seq.concat`柔軟な型を使用してサポートすることができます、シナリオを示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

出力は次のとおりです。

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

F# で他のオブジェクト指向言語と同様にはコンテキストを派生型またはインターフェイスを実装する型を自動的に変換する基本データ型またはインターフェイスの型。 これらの自動変換は、直接引数の場合は無効または型引数として関数の型の戻り値の型より複雑な型の一部として、下位の位置にその型が発生します。 したがって、柔軟な表記に適用する型がより複雑な型の一部である主に使用します。

## <a name="see-also"></a>関連項目

[F# 言語リファレンス](index.md)

[ジェネリック](generics/index.md)
