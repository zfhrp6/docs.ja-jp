---
title: "null 値 (F#)"
description: "F# のプログラミング言語で null 値を使用する方法について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 68ebd261-51cf-4582-b2dc-44c84d1c2500
ms.openlocfilehash: 01c14de00eb5efd0952145ffc8aabe69d65a3a48
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="null-values"></a>null 値

このトピックでは、f# では、null 値を使用する方法について説明します。


## <a name="null-value"></a>Null 値
Null 値は通常使用されません f# での値または変数。 ただし、特定の状況で異常値として null が表示されます。 しない限り、null がいない正規の値として許可型が f# で定義されている場合、 [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f)型に属性を適用します。 Null は使用可能な値型が他のいくつかの .NET 言語で定義されている場合と f# コードが null 値に生じるそのような型の相互運用するときにします。

F# で定義されているし、F# からにのみ使用の種類を直接 f# ライブラリを使用して null 値を作成する唯一の方法は使用する[Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977)または[Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)です。 ただし、f# の型の他の .NET 言語から使用されるまたは null 値が発生する可能性が f# など、.NET Framework で記述されたない API を使用してその型を使用している場合。

使用することができます、 `option` f# 可能な値が null の他の .NET 言語で参照変数を使用する状況での型。 Null の場合、f# ではなく`option`型、オプションの値を使用する`None`オブジェクトが存在しない場合。 オプションの値を使用する`Some(obj)`オブジェクト`obj`オブジェクトがある場合。 詳細については、次を参照してください。[オプション](../options.md)です。

`null`キーワードは f# 言語で有効なキーワードと .NET Framework Api または他の .NET 言語で記述されているその他の Api を使用するときに使用する必要があります。 Null 値が必要がある 2 つの状況は、.NET API を呼び出すし、null 値を引数として渡すときに、戻り値または .NET メソッドの呼び出しから出力パラメーターを解釈するときにします。

.NET メソッドに null 値を渡すを使用した、`null`呼び出し元のコードのキーワードです。 これを次のコード例に示します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

.NET メソッドから取得される null 値を解釈するには、するには、可能な場合に一致するパターンを使用します。 次のコード例は、パターン マッチを使用して、返される null 値を解釈する方法を示しています。`ReadLine`入力ストリームの末尾を越えて読み取ろうとしたときにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

F# の型の null 値を使用する場合など、他の方法で生成することも`Array.zeroCreate`、どの呼び出し`Unchecked.defaultof`です。 そのようなコードのカプセル化された null 値を保持するように注意する必要があります。 専用の f# ライブラリですべての関数で null 値を確認する必要はありません。 他の .NET 言語と相互運用ライブラリを作成している場合は null のチェックは、入力パラメーターと、スローを追加する必要が可能性があります、 `ArgumentNullException`c# または Visual Basic コードで行うのと同様、します。

次のコードを使用すると、任意の値が null を確認します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>関連項目
[値](index.md)

[match 式](../match-expressions.md)
