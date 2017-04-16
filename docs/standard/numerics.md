---
title: ".NET Framework における数値 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SIMD"
  - "System.Numerics.Vectors"
  - "ベクター"
  - "指数計算"
  - "複合"
  - "数値"
  - "BigInteger"
ms.assetid: dfebc18e-acde-4510-9fa7-9a0f4aa3bd11
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# .NET Framework における数値
.NET Framework が、標準数値整数と浮動小数点型のプリミティブをサポートしているだけでなく<xref:System.Numerics.BigInteger>、整数型の理論上の上限や下限のない<xref:System.Numerics.Complex>、複素数を表す型およびの SIMD が有効なベクター型のセット、 <xref:System.Numerics>名前空間。  
  
 さらに、System.Numerics.Vectors vectory 型の SIMD が有効なライブラリは、NuGet パッケージとしてリリースされました。  
  
## <a name="integral-types"></a>整数型  
 .NET Framework は、1 バイトから&8; バイトの長さの、符号付き整数と符号なし整数の両方をサポートしています。 次の表では、整数型とそのサイズをリストし、符号付きか符号なしかを示し、その範囲を記述しています。 すべての整数は、値型です。  
  
|型|符号付き/符号なし|サイズ (バイト)|最小値|最大値|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=fullName>|符号なし|1|0|255|  
|<xref:System.Int16?displayProperty=fullName>|符号付き|2|-32,768|32,767|  
|<xref:System.Int32?displayProperty=fullName>|符号付き|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=fullName>|符号付き|9|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=fullName>|符号付き|1|-128|127|  
|<xref:System.UInt16?displayProperty=fullName>|符号なし|2|0|65,535|  
|<xref:System.UInt32?displayProperty=fullName>|符号なし|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=fullName>|符号なし|9|0|18,446,744,073,709,551,615|  
  
 各整数型は、算術、比較、等価、明示的な変換、および暗黙的な変換の演算子の標準セットをサポートします。 各整数には、等価比較と相対比較、数値の文字列形式から整数への変換、および整数から文字列形式への変換を実行するメソッドも含まれています。 以外の数値演算など処理される標準の演算子によって丸め処理や&2; つの整数のより小さいか大きい値の識別はから利用可能な<xref:System.Math>クラスです。 使用して個々 のビット整数の値も扱える、 <xref:System.BitConverter>クラスです。  
  
 符号なし整数型が CLS に準拠していないことに注意してください。 詳細については、次を参照してください。[言語非依存および言語非依存コンポーネント](../../docs/standard/language-independence-and-language-independent-components.md)します。  
  
## <a name="floating-point-types"></a>浮動小数点型  
 .NET Framework には、次の表にリストされている&3; つプリミティブ浮動小数点型が含まれています。  
  
|型|サイズ (バイト単位)|最小要件|最大|  
|----------|-----------------------|-------------|-------------|  
|<xref:System.Double?displayProperty=fullName>|9|-1.79769313486232e308|1.79769313486232e308|  
|<xref:System.Single?displayProperty=fullName>|4|-3.402823e38|3.402823e38|  
|<xref:System.Decimal?displayProperty=fullName>|16|-79,228,162,514,264,337,593,543,950,335|79,228,162,514,264,337,593,543,950,335|  
  
 各浮動小数点型は、算術、比較、等価、明示的な変換、および暗黙的な変換の演算子の標準セットをサポートします。 それぞれには、等価比較と相対比較、数値の文字列形式から浮動小数点数への変換、および浮動小数点数から文字列形式への変換を実行するメソッドも含まれています。 いくつかの追加の数学、代数、および三角関数演算もから利用可能な<xref:System.Math>クラスです。 また、個別のビットを使用することができます<xref:System.Double>と<xref:System.Single>を使用して値、 <xref:System.BitConverter>クラスです。 <xref:System.Decimal?displayProperty=fullName>構造体には独自のメソッド<xref:System.Decimal.GetBits%2A?displayProperty=fullName>と[Decimal.Decimal (Int32\<xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=fullName>、10 進数の値を扱っての個々 のビット単位だけでなく、独自の数値演算を実行するためのメソッドのセットです。  
  
 <xref:System.Double>と<xref:System.Single>性質がない値 (太陽系の&2; つの星の間の距離) などの正確なおよびを高い精度や小さな丸め誤差の不要なアプリケーションを使用する型が想定されています。 使用する必要があります、 <xref:System.Decimal?displayProperty=fullName>より高い内のケースの型は、精度が要求され、エラーの丸め処理を行うには、  
  
## <a name="biginteger"></a>BigInteger  
 <xref:System.Numerics.BigInteger?displayProperty=fullName> は、理論的には値に上限や下限がない、サイズの大きい任意の整数を表す不変の型です。 メソッド、 <xref:System.Numerics.BigInteger>型とかなり類似して、他の整数型。  
  
## <a name="complex"></a>複合  
 <xref:System.Numerics.Complex>型は、複素数つまり実数部と虚数部で番号を表します。 これは、算術、比較、等価、明示的な変換、および暗黙的な変換の演算子の標準セットをサポートします。さらに数学、代数、および三角関数のメソッドもサポートします。  
  
## <a name="simd-enabled-vector-types"></a>SIMD 対応ベクター型  
 <xref:System.Numerics>名前空間には、.NET Framework 用の SIMD が有効なベクター型のセットが含まれています。 SIMD (Single Instruction Multiple Data operations) では、一部の操作をハードウェア レベルで並列に処理できます。その結果、ベクターに対して計算を実行する数値演算アプリ、科学系アプリ、グラフィックス アプリでは、パフォーマンスが大幅に向上します。  
  
 .NET Framework の SIMD 対応ベクター型には、次のものが含まれます。  さらに、System.Numerics.Vectors には、平面型と四元数型が含まれます。  
  
-   <xref:System.Numerics.Vector2>、 <xref:System.Numerics.Vector3>、および<xref:System.Numerics.Vector4> 2、3、および型の 4 次元ベクトルである型<xref:System.Single>します。  
  
-   2 つのマトリックス型<xref:System.Numerics.Matrix3x2>、3 × 2 行列を表すと<xref:System.Numerics.Matrix4x4>、4 × 4 行列を表します。  
  
-   <xref:System.Numerics.Plane>と<xref:System.Numerics.Quaternion>型です。  
  
 SimD 対応のベクター型は IL に実装されているので、これを SimD 非対応のハードウェアや JIT コンパイラで使用できます。 SIMD 命令の利点を活用するために、64 ビットのアプリはマネージ コード用の新しい 64 ビット JIT コンパイラ (.NET Framework 4.6 に含まれる) でコンパイルする必要があります。これは、x64 プロセッサがターゲットの場合に SIMD のサポートを追加します。  
  
 として SIMD をダウンロードすることも、 [NuGet パッケージ](http://www.nuget.org/packages/System.Numerics.Vectors)します。  NuGET パッケージは、ジェネリック型も含まれています。<xref:System.Numerics.Vector%601>構造体の任意のプリミティブ数値型のベクターを作成することができます。 (プリミティブ数値型のすべての数値型を含む、<xref:System>以外の名前空間<xref:System.Decimal>)。さらに、<xref:System.Numerics.Vector%601>構造体には、ベクターを使用する場合に呼び出すことのできる便利なメソッドのライブラリが用意されています。  
  
## <a name="see-also"></a>関連項目  
 [アプリケーションの基本事項](../../docs/standard/application-essentials.md)