---
title: 構造体 (F#)
description: F# の構造について、多くの場合は、コンパクトなオブジェクト タイプ学習の少量のデータと単純な動作の種類のクラスよりも効率的です。
ms.date: 05/16/2016
ms.openlocfilehash: 57c4148aec1d6a19237d74aa99824ef475c3632e
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="structures"></a>構造体

A*構造*はコンパクトなオブジェクト型であり、少量のデータと動作が単純な型のクラスよりも効率的です。

## <a name="syntax"></a>構文

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements-and-members
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements-and-members
```

## <a name="remarks"></a>コメント
構造体は*値の型*、つまりスタック上で直接、または、として使用されている場合、それらが保存されるフィールドまたは配列要素の場合、親のインラインを入力します。 クラスやレコードとは異なり、構造体のセマンティクスは値渡しです。 これは、主にアクセスおよびコピーが頻繁に行われるデータの小規模な集約に有用であることを意味します。

上記の構文では、2 つの形式が示されています。 1 番目のものは軽量構文ではないものの、頻繁に使用されます。これは、`struct` キーワードと `end` キーワードを使用する場合に、2 番目のものに出現する `StructAttribute` 属性を省略できるためです。 `StructAttribute` は省略して単に `Struct` とすることができます。

*型定義で要素-と-メンバー*前の構文でメンバーの宣言と定義を表します。 構造体にはコンス トラクター、可変フィールド、および不変フィールドを含めることができ、メンバーとインターフェイス実装を宣言できます。 詳細については、次を参照してください。[メンバー](members/index.md)です。

構造体は、継承に参加することも、`let` または `do` バインディングを含めることも、それ自身の型のフィールドを再帰的に含めることもできません (ただし、それ自身の型を参照する参照セルを含めることができます)。

構造体では `let` バインディングは使用できないため、`val` キーワードを使用して構造体のフィールドを宣言する必要があります。 `val` キーワードではフィールドとその型が定義されますが、初期化は実行できません。 代わりに、`val` 宣言がゼロまたは null に初期化されます。 このため、暗黙のコンストラクター (宣言で構造体名の直後に指定されるパラメーター) を含む構造体では、`val` 宣言に `DefaultValue` 属性で注釈を付ける必要があります。 定義されたコンストラクターを含む構造体でも、ゼロ初期化がサポートされます。 したがって、`DefaultValue` 属性は、このようなゼロ値がフィールドに対して有効であることの宣言になります。 構造体の暗黙的なコンストラクターでは動作は実行されません。これは、`let` バインディングと `do` バインディングがその型では許可されていないためですが、渡された暗黙のコンストラクターのパラメーター値はプライベート フィールドとして使用できます。

明示的なコンストラクターにフィールド値の初期化が含まれる場合があります。 明示的なコンストラクターを含む構造体がある場合も、ゼロ初期化がサポートされます。ただし、明示的なコンストラクターと競合するため、`DefaultValue` 宣言では `val` 属性を使用しません。 詳細については`val`宣言を参照してください[明示的なフィールド:`val`キーワード](members/explicit-fields-the-val-keyword.md)です。

構造体では属性およびアクセシビリティ修飾子が許可されており、その他の型と同じ規則に従います。 詳細については、次を参照してください。[属性](attributes.md)と[アクセス制御](access-control.md)です。

次のコード例は構造体の定義を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a>構造体のレコード、判別共用体

4.1 以降では f# で表すことができます[レコード](records.md)と[判別共用体](discriminated-unions.md)と構造体として、`[<Struct>]`属性。  詳細については、各記事を参照してください。
    
## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[クラス](classes.md)

[レコード](records.md)

[メンバー](members/index.md)
