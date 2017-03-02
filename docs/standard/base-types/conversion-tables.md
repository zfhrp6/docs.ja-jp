---
title: "型変換の表"
description: "型変換の表"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: d602f260-e7cf-49c8-a37f-731f40e4a538
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: a27f78bc3c0753a7c5bc752bb6391839bfc21e75
ms.lasthandoff: 03/02/2017

---

# <a name="type-conversion-tables"></a>型変換の表

拡大変換は、1 つの型の値が、サイズが同じかそれ以上の別の型に変換されるときに発生します。 縮小変換は、1 つの型の値が、サイズがより小さい別の型の値に変換されるときに発生します。 このトピックの表は、両方の種類の変換の動作を示しています。

## <a name="widening-conversions"></a>拡大変換

型 | データ損失なしに次の型に変換可能
---- | -------------------------------------
[Byte](xref:System.Byte) | [UInt16](xref:System.UInt16)、[Int16](xref:System.Int16)、[UInt32](xref:System.UInt32)、[Int32](xref:System.Int32)、[UInt64](xref:System.UInt64)、[Int64](xref:System.Int64)、[Single](xref:System.Single)、[Double](xref:System.Double)、[Decimal](xref:System.Decimal)
[SByte](xref:System.SByte) | [Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[Single](xref:System.Single)、[Double](xref:System.Double)、[Decimal](xref:System.Decimal)
[Int16](xref:System.Int16) | [Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[Single](xref:System.Single)、[Double](xref:System.Double)、[Decimal](xref:System.Decimal)
[UInt16](xref:System.UInt16) | [UInt32](xref:System.UInt32)、[Int32](xref:System.Int32)、[UInt64](xref:System.UInt64)、[Int64](xref:System.Int64)、[Single](xref:System.Single)、[Double](xref:System.Double)、[Decimal](xref:System.Decimal)
[Char](xref:System.Char) | [UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[Int32](xref:System.Int32)、[UInt64](xref:System.UInt64)、[Int64](xref:System.Int64)、[Single](xref:System.Single)、[Double](xref:System.Double)、[Decimal](xref:System.Decimal)
[Int32](xref:System.Int32) | [Int64](xref:System.Int64)、[Double](xref:System.Double)、[Decimal](xref:System.Decimal)
[UInt32](xref:System.UInt32) | [Int64](xref:System.Int64)、[UInt64](xref:System.UInt64)、[Double](xref:System.Double)、[Decimal](xref:System.Decimal)
[Int64](xref:System.Int64) | [Decimal](xref:System.Decimal)
[UInt64](xref:System.UInt64) | [Decimal](xref:System.Decimal)
[Single](xref:System.Single) | [Double](xref:System.Double)

一部の [Single](xref:System.Single) または [Double](xref:System.Double) への拡大変換では、精度が損なわれる可能性があります。 次の表は、情報が失われる可能性のある拡大変換を示しています。

型 | 次の型に変換可能
---- | -------------------
[Int32](xref:System.Int32) | [Single](xref:System.Single)
[UInt32](xref:System.UInt32) | [Single](xref:System.Single)
[Int64](xref:System.Int64) | [Single](xref:System.Single)、[Double](xref:System.Double)
[UInt64](xref:System.UInt64) | [Single](xref:System.Single)、[Double](xref:System.Double)
[Decimal](xref:System.Decimal) | [Single](xref:System.Single)、[Double](xref:System.Double)

## <a name="narrowing-conversions"></a>縮小変換

[Single](xref:System.Single) または [Double](xref:System.Double) への縮小変換では、情報が失われる可能性があります。 ターゲット型がソースの大きさを正確に表現できない場合、結果の型は定数 `PositiveInfinity` または `NegativeInfinity` に設定されます。 `PositiveInfinity` は、正の数を&0; で除算した結果であり、[Single](xref:System.Single) または [Double](xref:System.Double) の値が `MaxValue` フィールドの値を超える場合にも返されます。 `NegativeInfinity` は、負の数を&0; で除算した結果であり、[Single](xref:System.Single) または [Double](xref:System.Double) の値が `MinValue` フィールドの値を下回る場合にも返されます。 [Double](xref:System.Double) から [Single](xref:System.Single) への変換は、`PositiveInfinity` または `NegativeInfinity` になる場合があります。

その他のデータ型についても、縮小変換によって情報が失われる可能性があります。 ただし、変換される型の値が、ターゲット型の `MaxValue` フィールドと `MinValue` フィールドで指定された範囲外にある場合は、[OverflowException](xref:System.OverflowException) がスローされます。また、ターゲット型の値がその `MaxValue` または `MinValue` を超えないことを確認するために、ランタイムによって変換がチェックされます。 [System.Convert](xref:System.Convert) クラスを使用して実行される変換は、常にこの方法でチェックされます。

次の表は、[System.Convert](xref:System.Convert) を使用して [OverflowException](xref:System.OverflowException) をスローする変換、または、変換される型の値が結果の型の定義済みの範囲外にあるかどうかのチェックを行うすべての変換を示しています。

型 | 次の型に変換可能
---- | -------------------
[Byte](xref:System.Byte) | [SByte](xref:System.SByte)
[SByte](xref:System.SByte) | [Byte](xref:System.Byte)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64)
[Int16](xref:System.Int16) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[UInt16](xref:System.UInt16)
[UInt16](xref:System.UInt16) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)
[Int32](xref:System.Int32) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)
[UInt32](xref:System.UInt32) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[UInt16](xref:System.UInt16)、[Int32](xref:System.Int32)
[Int64](xref:System.Int64) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[UInt16](xref:System.UInt16)、[Int32](xref:System.Int32)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64)
[UInt64](xref:System.UInt64) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[UInt16](xref:System.UInt16)、[Int32](xref:System.Int32)、[UInt32](xref:System.UInt32)、[Int64](xref:System.Int64)
[Decimal](xref:System.Decimal) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[UInt16](xref:System.UInt16)、[Int32](xref:System.Int32)、[UInt32](xref:System.UInt32)、[Int64](xref:System.Int64)、[UInt64](xref:System.UInt64)
[Single](xref:System.Single) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[UInt16](xref:System.UInt16)、[Int32](xref:System.Int32)、[UInt32](xref:System.UInt32)、[Int64](xref:System.Int64)、[UInt64](xref:System.UInt64)
[Double](xref:System.Double) | [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[UInt16](xref:System.UInt16)、[Int32](xref:System.Int32)、[UInt32](xref:System.UInt32)、[Int64](xref:System.Int64)、[UInt64](xref:System.UInt64)

## <a name="see-also"></a>関連項目

[System.Convert](xref:System.Convert)

[型変換](type-conversion.md)


