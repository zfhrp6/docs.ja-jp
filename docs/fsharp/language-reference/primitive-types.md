---
title: "プリミティブ型 (F#)"
description: "F# 言語で使用される基本的なプリミティブ型を検出します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f23d98b-551b-4fd2-9f4f-0fd7254288ed
ms.openlocfilehash: b493cdf7116d94f66940d03b86e584bcecbbb0f1
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2017
---
# <a name="primitive-types"></a>プリミティブ型

このトピックでは、f# 言語で使用される基本的なプリミティブ型を示します。 また、対応する .NET 型と各型の最小値と最大値も示します。

## <a name="summary-of-primitive-types"></a>プリミティブ型の概要
次の表では、プリミティブの f# 型のプロパティをまとめたものです。

|型|.NET 型|説明|
|----|---------|-----------|
|`bool`|`System.Boolean`|有効な値は、`true` と `false` です。|
|`byte`|`System.Byte`|0 から 255 の値です。|
|`sbyte`|`System.SByte`|-128 から 127 の値です。|
|`int16`|`System.Int16`|-32768 から 32767 の値です。|
|`uint16`|`System.UInt16`|0 から 65535 の値です。|
|`int`|`System.Int32`|-2,147, 483,648 から 2,147, 483,647 の値です。|
|`uint32`|`System.UInt32`|0 から 4,294,967,295 の値です。|
|`int64`|`System.Int64`|9,223,372,036,854,775,807-9,223,372,036,854,775,808 から値です。|
|`uint64`|`System.UInt64`|0 から 18,446,744,073,709,551,615 の値です。|
|`nativeint`|`System.IntPtr`|符号付き整数としてのネイティブ ポインターです。|
|`unativeint`|`System.UIntPtr`|符号なし整数としてのネイティブ ポインターです。|
|`char`|`System.Char`|Unicode 文字の値。|
|`string`|`System.String`|Unicode テキストです。|
|`decimal`|`System.Decimal`|浮動小数点には少なくとも 28 の有効桁数を持つデータ型です。|
|`unit`|該当なし|実際の値が存在しないことを示します。 型が示される 1 つだけの仮引数の値を持つ`()`します。 単位の値、 `()`、ここで値が必要が、実際の値が使用可能なまたは意味をなさなくプレース ホルダーとして使用されます。|
|`void`|`System.Void`|ないことを示します型または値。|
|`float32, single`|`System.Single`|32 ビット浮動小数点型です。|
|`float, double`|`System.Double`|64 ビット浮動小数点型です。|

>[!NOTE]
使用して、64 ビット整数型に対して大きすぎる整数を使用して計算を行うことができます、 [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa)型です。 `bigint`プリミティブ型であるとは見なされません省略形は`System.Numerics.BigInteger`します。

## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)
