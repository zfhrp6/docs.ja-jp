---
title: unit 型 (F#)
description: ここで、値が必要、言語構文によって値はありませんが必要なまたは必要なときに、場所を保持するために f# 'unit' の型を使用する多くの場合について説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 1a8c8f74e31c5426a9fb6a7143e9d2ac9a7104c0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="unit-type"></a>Unit 型

`unit`型は、型がない場合、特定の値を示す、`unit`の種類が単一の値のみ、その他の値はありませんが存在するか、必要なときに、プレース ホルダーとして機能します。


## <a name="syntax"></a>構文

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>コメント
すべての f# 式は、値に評価される必要があります。 型の値、関心のある値を生成しない式の`unit`を使用します。 `unit`型に似ています、 `void` c# および C++ などの言語を入力します。

`unit`型には、単一の値とその値は、トークンで示される`()`です。

値、`unit`型が f# の値はありませんが必要なまたは必要な場合は、言語の構文では、値が必要な場所を保持するためにプログラミングでよく使用されています。 たとえば場合の戻り値があります、`printf`関数。 の重要な操作、`printf`操作が、関数で発生する、関数が、実際の値を返す必要はありません。 このため、戻り値は型`unit`です。

一部のコンストラクトが想定して、`unit`値。 たとえば、`do`バインドまたはモジュールの最上位レベルに任意のコードを評価する必要が、`unit`値。 コンパイラ警告を報告するときに、`do`バインドまたはモジュールの最上位レベルにコード以外の場合、結果を生成、`unit`使用されていない、次の例で示すように値。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

この警告は、;、関数型プログラミングの特性その他の .NET プログラミング言語ではありません。 副作用は関数がない、純粋関数型のプログラムでは、最終的な戻り値は、関数呼び出しの結果だけがします。 したがって、結果を無視すると、潜在的なプログラミング エラーを勧めします。 F# ではありませんが、純粋関数型プログラミング言語は、機能のプログラミング スタイル可能な場合に従うことをお勧めします。

## <a name="see-also"></a>関連項目
[プリミティブ](primitive-types.md)

[F# 言語リファレンス](index.md)
