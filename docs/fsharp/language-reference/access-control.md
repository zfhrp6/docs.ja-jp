---
title: "アクセス制御 (F#)"
description: "型、メソッド、および f# のプログラミング言語では、関数などのプログラミング要素へのアクセスを制御する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 955b06fe-d1cd-431d-8db6-93e83b697453
ms.openlocfilehash: a02e20a585a0456577901f2762a0eeb0e3ecd2f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="access-control"></a>アクセス制御

*アクセス制御*型、メソッド、および関数など、特定のプログラム要素を使用できるクライアントの宣言を参照します。


## <a name="basics-of-access-control"></a>アクセス制御の基礎
F# でのアクセス制御指定子`public`、 `internal`、および`private`モジュール、型、メソッド、値の定義、関数、プロパティ、および明示的なフィールドに適用できます。


- `public`すべての呼び出し元によってエンティティにアクセスできることを示します。

- `internal`エンティティを同じアセンブリからのみアクセスできることを示します。

- `private`外側の型またはモジュールからのみ、エンティティにアクセスできることを示します。


>[!NOTE] 
アクセス指定子`protected`が、許容可能な操作をサポートする言語で作成されたタイプを使用している場合、f# で使用されていない`protected`アクセスします。 そのため、保護されたメソッドをオーバーライドする場合、メソッドが、クラスとそのサブフォルダー内でのみアクセス可能なします。

場合を除き、エンティティの名前の前に、指定子を配置する一般に、`mutable`または`inline`指定子を使用すると、アクセス制御指定子の後に表示されます。

アクセス指定子を使用していない場合、既定値は`public`、除く`let`は常に、型のバインディング`private`型にします。

F# の署名は、f# のプログラム要素へのアクセスを制御するための別のメカニズムを提供します。 署名は、アクセス制御の必要はありません。 詳細については、「[シグネチャ](signatures.md)」を参照してください。


## <a name="rules-for-access-control"></a>アクセス制御のルール
アクセス制御では、次の規則に従います。


- 継承の宣言 (の使用は、`inherit`クラスの基本クラスを指定する)、インターフェイスの宣言 (つまりには、クラスがインターフェイスを実装することを指定する)、および抽象メンバーが常に外側の型と同じのアクセシビリティを持ちます。 そのため、これらのコンストラクトでアクセス制御指定子は使用できません。

- 判別共用体の個々 のケースは、共用体の型から別の独自のアクセス制御修飾子にはできません。

- レコード型の個々 のフィールドは、レコードの種類から別の独自のアクセス制御修飾子にはできません。


## <a name="example"></a>例
次のコードでは、アクセス制御指定子の使用を示します。 プロジェクトで、2 つのファイルがある`Module1.fs`と`Module2.fs`です。 各ファイルは、暗黙的にモジュールです。 そのため、2 つのモジュールがある`Module1`と`Module2`です。 プライベート型および内部の型がで定義されている`Module1`です。 プライベート型にアクセスできません`Module2`、内部の型のことができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]
    
次のコードで作成された型のアクセシビリティの確認`Module1.fs`です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]
    
## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[シグネチャ](signatures.md)
