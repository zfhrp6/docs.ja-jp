---
title: 遅延計算 (F#)
description: F# で遅延の計算が、アプリとライブラリのパフォーマンスを向上する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 1c4eb6ab247c44a04a9d145185e2de7ec01b8e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563933"
---
# <a name="lazy-computations"></a>遅延計算

*遅延計算*されるは、すぐに評価されませんが、結果が必要なときに評価される代わりを計算します。 これは、コードのパフォーマンスを向上させるために役立ちます。

## <a name="syntax"></a>構文

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>コメント

前の構文で*式*結果が、必要な場合にのみ評価されるコードと*識別子*結果を格納する値です。 値の型は[ `Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489)ここで、実際の型のために使用`'T`式の結果から決定されます。

遅延計算を使用すると、結果が必要とされる状況のみを計算の実行を制限することでパフォーマンスを向上させることができます。

メソッドを呼び出す、計算を実行するのには、`Force`です。 `Force` 1 回だけ実行する実行をします。 後続の呼び出し`Force`戻り、同じ結果を任意のコードを実行しないでください。

次のコードは、限定的な計算を使用しての使用を示しています。`Force`です。 このコードの種類で`result`は`Lazy<int>`、および`Force`メソッドを返します、`int`です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

レイジー評価は、ではなく、`Lazy`入力、シーケンスにも使用します。 詳細については、次を参照してください。[シーケンス](sequences.md)です。

## <a name="see-also"></a>関連項目

[F# 言語リファレンス](index.md)

[LazyExtensions モジュール](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
