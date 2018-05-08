---
title: do 束縛 (F#)
description: 使用方法を学習、f# のバインドを ' do' は関数または値を定義することがなくコードを実行します。
ms.date: 05/16/2016
ms.openlocfilehash: 6fd084090a204beab0da1c2deb5b5ae2a86281c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="do-bindings"></a>do 束縛

A`do`バインディングを使用して、関数、または値を定義することがなくコードを実行します。 、はバインドすることもクラスで使用される、を参照してください[`do`クラス内のバインディング](../members/do-bindings-in-classes.md)です。


## <a name="syntax"></a>構文

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>コメント
使用して、`do`関数、または値の定義とは無関係にコードを実行するときにバインディングします。 内の式、`do`バインドを返す必要があります`unit`です。 最上位のコード`do`モジュールが初期化されるときにバインディングを実行します。 キーワード`do`は省略可能です。

属性は、最上位レベルに適用できる`do`バインドします。 たとえば、プログラムでは、COM 相互運用機能を使用する場合を適用する、`STAThread`属性をプログラムにします。 こうことで、属性を使用して、`do`バインド、次のコードに示すようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a>関連項目
[F# 言語リファレンス](../index.md)

[関数](index.md)

