---
title: .NET Framework における数値
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- SIMD
- System.Numerics.Vectors
- vectors
- scientific computing
- Complex
- numerics
- BigInteger
ms.assetid: dfebc18e-acde-4510-9fa7-9a0f4aa3bd11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2a795fb52c123840c1ba7b82f77d6745feba89b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588698"
---
# <a name="numerics-in-the-net-framework"></a>.NET Framework における数値
.NET Framework は、標準の数値整数と浮動小数点型のプリミティブをサポートしています。さらに、理論上の上限や下限のない整数型の <xref:System.Numerics.BigInteger>、複素数を表す型の <xref:System.Numerics.Complex>、<xref:System.Numerics> 名前空間の SIMD が有効なベクター型のセットもサポートしています。  
  
 さらに、ベクター型の SIMD 対応ライブラリ System.Numerics.Vectors は、NuGet パッケージとしてリリースされました。  
  
## <a name="integral-types"></a>整数型  
 .NET Framework は、1 バイトから 8 バイトの長さの、符号付き整数と符号なし整数の両方をサポートしています。 次の表では、整数型とそのサイズをリストし、符号付きか符号なしかを示し、その範囲を記述しています。 すべての整数は、値型です。  
  
|型|符号付き/符号なし|サイズ (バイト)|最小値|最大値|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|符号なし|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|符号付き|2|-32,768|32,767|  
|<xref:System.Int32?displayProperty=nameWithType>|符号付き|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=nameWithType>|符号付き|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=nameWithType>|符号付き|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|符号なし|2|0|65,535|  
|<xref:System.UInt32?displayProperty=nameWithType>|符号なし|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=nameWithType>|符号なし|8|0|18,446,744,073,709,551,615|  
  
 各整数型は、算術、比較、等価、明示的な変換、および暗黙的な変換の演算子の標準セットをサポートします。 各整数には、等価比較と相対比較、数値の文字列形式から整数への変換、および整数から文字列形式への変換を実行するメソッドも含まれています。 丸め処理や 2 つの整数のより小さいか大きい値の識別など、標準の演算子によって処理される上記以外の数値演算は、<xref:System.Math> クラスから使用可能です。 <xref:System.BitConverter> クラスを使用して、整数値の個々 のビットを操作することもできます。  
  
 符号なし整数型が CLS に準拠していないことに注意してください。 詳しくは、「[言語への非依存性、および言語非依存コンポーネント](../../docs/standard/language-independence-and-language-independent-components.md)」を参照してください。  
  
## <a name="floating-point-types"></a>浮動小数点型  
 .NET Framework には、次の表にリストされている 3 つプリミティブ浮動小数点型が含まれています。  
  
|型|サイズ (バイト単位)|最小要件|最大|  
|----------|-----------------------|-------------|-------------|  
|<xref:System.Double?displayProperty=nameWithType>|8|-1.79769313486232e308|1.79769313486232e308|  
|<xref:System.Single?displayProperty=nameWithType>|4|-3.402823e38|3.402823e38|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|-79,228,162,514,264,337,593,543,950,335|79,228,162,514,264,337,593,543,950,335|  
  
 各浮動小数点型は、算術、比較、等価、明示的な変換、および暗黙的な変換の演算子の標準セットをサポートします。 それぞれには、等価比較と相対比較、数値の文字列形式から浮動小数点数への変換、および浮動小数点数から文字列形式への変換を実行するメソッドも含まれています。 いくつかの追加の数学、代数、および三角関数の演算も、<xref:System.Math> クラスから使用可能です。 <xref:System.BitConverter> クラスを使用して、<xref:System.Double> および <xref:System.Single> の値の個々のビットを操作することもできます。 <xref:System.Decimal?displayProperty=nameWithType> 構造体には、10 進値の個々のビットを操作するための独自のメソッド (<xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> と <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>)、および追加の数学演算を実行するための独自のメソッド セットがあります。  
  
 <xref:System.Double> と <xref:System.Single> の型は、本来正確ではない値 (太陽系の 2 つの星の間の距離など)、および高い精度や小さな丸め誤差の検出が必要ではないアプリケーションでの使用が想定されています。 より高い精度が要求され、丸め誤差が許容されないケースでは、<xref:System.Decimal?displayProperty=nameWithType> の型を使用する必要があります。  
  
## <a name="biginteger"></a>BigInteger  
 <xref:System.Numerics.BigInteger?displayProperty=nameWithType> は、理論的には値に上限や下限がない、サイズの大きい任意の整数を表す不変の型です。 <xref:System.Numerics.BigInteger> 型のメソッドは、他の整数型のメソッドとかなり類似しています。  
  
## <a name="complex"></a>複合  
 <xref:System.Numerics.Complex> 型は、複素数つまり実数部と虚数部のある数を表します。 これは、算術、比較、等価、明示的な変換、および暗黙的な変換の演算子の標準セットをサポートします。さらに数学、代数、および三角関数のメソッドもサポートします。  
  
## <a name="simd-enabled-vector-types"></a>SIMD 対応ベクター型  
 <xref:System.Numerics> 名前空間には、.NET Framework 用の SIMD 対応ベクター型のセットが含まれています。 SIMD (Single Instruction Multiple Data operations) では、一部の操作をハードウェア レベルで並列に処理できます。その結果、ベクターに対して計算を実行する数値演算アプリ、科学系アプリ、グラフィックス アプリでは、パフォーマンスが大幅に向上します。  
  
 .NET Framework の SIMD 対応ベクター型には、次のものが含まれます。  さらに、System.Numerics.Vectors には、平面型と四元数型が含まれます。  
  
-   <xref:System.Numerics.Vector2> 型、<xref:System.Numerics.Vector3> 型、<xref:System.Numerics.Vector4> 型。それぞれ <xref:System.Single> 型の 2 次元ベクター、3 次元ベクター、4 次元ベクターです。  
  
-   2 つのマトリックス型。3x2 行列を表す <xref:System.Numerics.Matrix3x2> と、4x4 行列を表す <xref:System.Numerics.Matrix4x4> です。  
  
-   <xref:System.Numerics.Plane> 型と <xref:System.Numerics.Quaternion> 型。  
  
 SimD 対応のベクター型は IL に実装されているので、これを SimD 非対応のハードウェアや JIT コンパイラで使用できます。 SIMD 命令の利点を活用するために、64 ビットのアプリはマネージ コード用の新しい 64 ビット JIT コンパイラ (.NET Framework 4.6 に含まれる) でコンパイルする必要があります。これは、x64 プロセッサがターゲットの場合に SIMD のサポートを追加します。  
  
 SIMD は [NuGet パッケージ](https://www.nuget.org/packages/System.Numerics.Vectors)としてもダウンロードできます。  NuGET パッケージには、ジェネリック <xref:System.Numerics.Vector%601> 構造体も含まれています。この構造体を使用すると、任意のプリミティブな数値型のベクターを作成できます。 (プリミティブな数値型には、<xref:System.Decimal> を除く <xref:System> 名前空間のすべての数値型が含まれます。)さらに、<xref:System.Numerics.Vector%601> 構造体は、ベクターを使用しているときに呼び出すことのできる便利なメソッドのライブラリを提供します。  
  
## <a name="see-also"></a>参照  
 [アプリケーションの基本事項](../../docs/standard/application-essentials.md)
