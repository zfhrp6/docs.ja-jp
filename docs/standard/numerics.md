---
title: ".NET Core における数値"
description: ".NET Core における数値"
keywords: .NET, .NET Core
author: rpetrusha
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 6b8696be-55f5-4b66-98f3-69ff827c2c49
translationtype: Human Translation
ms.sourcegitcommit: d5c7a18af16b4f3416e84b6cf86f0f78f28948da
ms.openlocfilehash: 2930bf6879df3cd16cbd0221ae6dfcba9b41de2e

---

# <a name="numerics-in-net-core"></a>.NET Core における数値

.NET Core は、標準の数値整数と浮動小数点プリミティブをサポートしています。さらに、理論上の上限や下限のない整数型の [System.Numerics.BigInteger](https://docs.microsoft.com/dotnet/core/api/System.Numerics.BigInteger)、複素数を表す型の [System.Numerics.Complex](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Complex)、[System.Numerics](https://docs.microsoft.com/dotnet/core/api/System.Numerics) 名前空間の Single Instruction Multiple Data ([SIMD](https://en.wikipedia.org/wiki/SIMD)) 対応ベクター型のセットもサポートしています。 

## <a name="integral-types"></a>整数型

.NET Core は、1 バイトから 8 バイトの長さの、符号付き整数と符号なし整数の両方をサポートしています。 次の表では、整数型とそのサイズをリストし、符号付きか符号なしかを示し、その範囲を記述しています。 すべての整数は、値型です。 

型 | 符号付き/符号なし | サイズ (バイト) | 最小値 | 最大値
---- | --------------- | ------------ | ------------- | -------------
[System.Byte](https://docs.microsoft.com/dotnet/core/api/System.Byte) | 符号なし | 1 | 0 | 255
[System.Int16](https://docs.microsoft.com/dotnet/core/api/System.Int16) | 符号付き | 2 | -32,768 | 32,767
[System.Int32](https://docs.microsoft.com/dotnet/core/api/System.Int32) | 符号付き | 4 | -2,147,483,648 | 2,147,483,647
[System.Int64](https://docs.microsoft.com/dotnet/core/api/System.Int64) | 符号付き | 9 | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807
[System.SByte](https://docs.microsoft.com/dotnet/core/api/System.SByte) | 符号付き | 1 | -128 | 127
[System.UInt16](https://docs.microsoft.com/dotnet/core/api/System.UInt16) | 符号なし | 2 | 0 | 65,535
[System.UInt32](https://docs.microsoft.com/dotnet/core/api/System.UInt32) | 符号なし | 4 | 0 | 4,294,967,295
[System.UInt64](https://docs.microsoft.com/dotnet/core/api/System.UInt64) | 符号なし | 9 | 0 | 18,446,744,073,709,551,615

各整数型は、算術、比較、等価、明示的な変換、および暗黙的な変換の演算子の標準セットをサポートします。 各整数には、等価比較と相対比較、数値の文字列形式から整数への変換、および整数から文字列形式への変換を実行するメソッドも含まれています。 丸め処理や 2 つの整数のより小さいか大きい値の識別など、標準の演算子によって処理される上記以外の数値演算は、[System.Math](https://docs.microsoft.com/dotnet/core/api/System.Math) クラスから使用可能です。 [System.BitConverter](https://docs.microsoft.com/dotnet/core/api/System.BitConverter) クラスを使用して、整数値の個々のビットを操作することもできます。 
     
符号なし整数型が CLS に準拠していないことに注意してください。 詳細については、[.NET 共通型システムと共通言語仕様](common-type-system.md)に関するページを参照してください。

## <a name="floatingpoint-types"></a>浮動小数点型

.NET Core には、次の表に示す 3 つプリミティブ浮動小数点型が含まれています。 

型 | サイズ (バイト) | 最小値 | 最大値
---- | ------------ | ------------- | -------------
[System.Double](https://docs.microsoft.com/dotnet/core/api/System.Double) | 9 | -1.79769313486232e308 | 1.79769313486232e308
[System.Single](https://docs.microsoft.com/dotnet/core/api/System.Single) | 4 | -3.402823e38 | 3.402823e38
[System.Decimal](https://docs.microsoft.com/dotnet/core/api/System.Decimal) | 16 | -79,228,162,514,264,337,593,543,950,335 | 79,228,162,514,264,337,593,543,950,335
   
各浮動小数点型は、算術、比較、等価、明示的な変換、および暗黙的な変換の演算子の標準セットをサポートします。 それぞれには、等価比較と相対比較、数値の文字列形式から浮動小数点数への変換、および浮動小数点数から文字列形式への変換を実行するメソッドも含まれています。 いくつかの追加の数学、代数、および三角関数の演算も、`Math` クラスから使用可能です。 `BitConverter` クラスを使用して、`Double` および `Single` の値の個々のビットを操作することもできます。 `Decimal` 構造体には、10 進値の個々のビットを操作するための独自のメソッド (`Decimal.GetBits` と `Decimal.Decimal(Int32())`)、および追加の数学演算を実行するための独自のメソッド セットがあります。 

`Double` と `Single` の型は、本来正確ではない値 (太陽系の 2 つの星の間の距離など)、および高い精度や小さな丸め誤差の検出が必要ではないアプリケーションでの使用が想定されています。 より高い精度が要求され、丸め誤差が許容されないケースでは、`Decimal` 型を使用する必要があります。

## <a name="biginteger"></a>BigInteger

[System.Numerics.BigInteger](https://docs.microsoft.com/dotnet/core/api/System.Numerics.BigInteger) は、理論的には値に上限や下限がない、サイズの大きい任意の整数を表す不変の型です。 `BigInteger` 型のメソッドは、他の整数型のメソッドとかなり類似しています。  

## <a name="complex"></a>複合

[System.Numerics.Complex](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Complex) 型は、複素数つまり実数部と虚数部のある数を表します。 これは、算術、比較、等価、明示的な変換、および暗黙的な変換の演算子の標準セットをサポートします。さらに数学、代数、および三角関数のメソッドもサポートします。 

## <a name="simdenabled-vector-types"></a>SIMD 対応ベクター型

`System.Numerics` 名前空間には、.NET Core 用の SIMD 対応ベクター型のセットが含まれています。 SIMD では、一部の操作をハードウェア レベルで並列に処理できます。その結果、ベクターに対して計算を実行する数値演算アプリ、科学系アプリ、グラフィックス アプリでは、パフォーマンスが大幅に向上します。 

.NET Core の SIMD 対応ベクター型には、次のものが含まれます。 

* `Single` 型の 2、3、および 4 次元ベクターである [System.Numerics.Vector2](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector2)、[System.Numerics.Vector3](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector3)、および [System.Numerics.Vector4](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector4)。

* 任意のプリミティブな数値型のベクターを作成できる [Vector&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector-1) 構造体。 プリミティブな数値型には、Decimal を除く System 名前空間のすべての数値型が含まれます。

* 3 x 2 行列を表す [System.Numerics.Matrix3x2](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Matrix3x2) と、4 x 4 行列を表す [System.Numerics.Matrix4x4](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Matrix4x4) の 2 つのマトリックス型。 

* 3 次元平面を表す [System.Numerics.Plane](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Plane) 型と 3 次元物理回転をエンコードするために使用されるベクターを表す [System.Numerics.Quaternion](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Quaternion) 型。



<!--HONumber=Nov16_HO3-->


