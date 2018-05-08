---
title: クラス内の let 束縛 (F#)
description: クラスの定義で 'let' 束縛を使用してプライベート フィールドや F# でクラスのプライベート関数を定義する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 1c17fe0edec14c28c9bdde86d0a2acb7c886cdf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="let-bindings-in-classes"></a>クラス内の let 束縛

使用して、プライベート フィールドや F# でクラスのプライベート関数を定義することができます`let`クラス定義にバインドします。


## <a name="syntax"></a>構文

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>コメント
クラスの見出しと継承の宣言後、任意のメンバー定義の前に、前の構文が表示されます。 構文は次のようにです`let`クラスがクラスで定義した名前の外部でのバインドはクラスに限定されているスコープを設定します。 A`let`バインドによって、プライベート フィールドやデータを公開する関数または関数で公開されている、プロパティまたはメンバー メソッドを宣言します。

A`let`をバインドは静的なインスタンスと呼びます`let`バインドします。 インスタンス`let`バインディング オブジェクトの作成を実行します。 静的`let`バインディングは、型が最初に使用される前に実行することが保証されるクラスの静的初期化子の一部です。

インスタンス内のコード`let`バインディングは、プライマリ コンス トラクターのパラメーターを使用できます。

属性およびアクセシビリティ修飾子には使用できません`let`クラスにバインドします。

次のコード例がいくつかの種類を示す`let`クラスにバインドします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

出力は次のとおりです。

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>別の方法でフィールドを作成するには
使用することも、`val`プライベート フィールドを作成するキーワードです。 使用する場合、`val`キーワードが与えられていない値と、オブジェクトは作成されますが、既定値で初期化されます。 詳細については、次を参照してください。[明示的なフィールド: val キーワード](explicit-fields-the-val-keyword.md)です。

メンバー定義を使用して、キーワードを追加するクラスでプライベート フィールドを定義することも`private`を定義します。 これは、コードを書き直すことがなく、メンバーのアクセシビリティを変更する場合に役立ちます。 ことができます。 詳細については、「[Access Control](../access-control.md)」(アクセス制御) を参照してください。

## <a name="see-also"></a>関連項目
[メンバー](index.md)

[クラス内の `do` バインド](do-bindings-in-classes.md)

[`let` バインド](../functions/let-bindings.md)
