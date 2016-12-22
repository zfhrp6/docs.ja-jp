---
title: "数値演算関数 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "数値演算関数、Visual Basic"
  - "算術演算、数値演算関数"
  - "数値演算ルーチン"
  - "Atn 関数"
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 数値演算関数 (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

<xref:System.Math?displayProperty=fullName> クラスのメソッドは、三角、対数の、およびそのほかの数値演算関数が用意されています。  
  
## 解説  
 次の表は <xref:System.Math?displayProperty=fullName> クラスのメソッドを示します。  Visual Basic プログラムでこれらを使用できます。  
  
|.NET Framework メソッド|説明|  
|-------------------------|--------|  
|<xref:System.Math.Abs%2A>|指定された数値の絶対値を返します。|  
|<xref:System.Math.Acos%2A>|コサインが指定数となる角度を返します。|  
|<xref:System.Math.Asin%2A>|サインが指定数となる角度を返します。|  
|<xref:System.Math.Atan%2A>|タンジェントが指定数となる角度を返します。|  
|<xref:System.Math.Atan2%2A>|タンジェントが 2 つの指定された数の商である角度を返します。|  
|<xref:System.Math.BigMul%2A>|2 個の 32 ビットの数値の完全な製品を返します。|  
|<xref:System.Math.Ceiling%2A>|指定 `Decimal` か `Double`以上である最も小さい整数値を返します。|  
|<xref:System.Math.Cos%2A>|指定された角度のコサインを返します。|  
|<xref:System.Math.Cosh%2A>|指定された角度のハイパーボリック コサインを返します。|  
|<xref:System.Math.DivRem%2A>|32 ビット 2 または 64 ビット符号付き整数の商を返し、出力パラメーターの剰余を返します。|  
|<xref:System.Math.Exp%2A>|指定したに発生する e \(自然対数の底\) を返します。|  
|<xref:System.Math.Floor%2A>|`Double` 指定 `Decimal` 数以下である大きな整数を返します。|  
|<xref:System.Math.IEEERemainder%2A>|指定した別の数によってその結果、指定した数の部分から剰余を返します。|  
|<xref:System.Math.Log%2A>|指定された数値の e \(ベース\) の自然対数、または指定された底の指定された数値の対数を返します。|  
|<xref:System.Math.Log10%2A>|指定した数の底 10 の対数を返します。|  
|<xref:System.Math.Max%2A>|二つの数値に 2 を超える返します。|  
|<xref:System.Math.Min%2A>|2 つの数のうち、小さい方を返します。|  
|<xref:System.Math.Pow%2A>|指定の数値を指定した値で累乗した値を返します。|  
|<xref:System.Math.Round%2A>|丸めるために使用される最も近い整数値または小数部の指定した数に `Decimal` または `Double` の値を返します。|  
|<xref:System.Math.Sign%2A>|引数に指定された数式の符号を表す `Integer` の値を返します。|  
|<xref:System.Math.Sin%2A>|指定された角度のサインを返します。|  
|<xref:System.Math.Sinh%2A>|指定された角度のハイパーボリック サインを返します。|  
|<xref:System.Math.Sqrt%2A>|指定された数値の平方根を返します。|  
|<xref:System.Math.Tan%2A>|指定された角度のタンジェントを返します。|  
|<xref:System.Math.Tanh%2A>|指定された角度のハイパーボリック タンジェントを返します。|  
|<xref:System.Math.Truncate%2A>|`Double` 指定 `Decimal` または数の重要な部分を計算します。|  
  
 これらの関数を修飾子なしで使用するには、ソース ファイルの先頭に次のコードを追加して、プロジェクトに <xref:System.Math?displayProperty=fullName> の名前空間をインポートする:  
  
```  
Imports System.Math  
```  
  
## 使用例  
 この例では、<xref:System.Math> クラスの <xref:System.Math.Abs%2A> メソッドを使って、数値の絶対値を計算します。  
  
```  
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## 使用例  
 この例では、<xref:System.Math> クラスの <xref:System.Math.Atan%2A> メソッドを使って、πの値を計算します。  
  
```  
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## 使用例  
 この例では、<xref:System.Math> クラスの <xref:System.Math.Cos%2A> メソッドを使って、角度のコサインを返します。  
  
```  
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## 使用例  
 この例では、<xref:System.Math> クラスの <xref:System.Math.Exp%2A> メソッドを使って、指定した数値を指数とする e の累乗を返します。  
  
```  
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## 使用例  
 この例では、<xref:System.Math> クラスの <xref:System.Math.Log%2A> メソッドを使って、数値の自然対数を返します。  
  
```  
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## 使用例  
 この例では、<xref:System.Math> クラスの <xref:System.Math.Round%2A> メソッドを使って、数値を最も近い整数に丸めます。  
  
```  
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## 使用例  
 この例では、<xref:System.Math> クラスの <xref:System.Math.Sign%2A> メソッドを使って、数の符号を判定します。  
  
```  
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## 使用例  
 この例では、<xref:System.Math> クラスの <xref:System.Math.Sin%2A> メソッドを使って、角度のサイン値を返します。  
  
```  
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## 使用例  
 この例では、<xref:System.Math> クラスの <xref:System.Math.Sqrt%2A> メソッドを使って、数値の平方根を計算します。  
  
```  
' Returns 2.  
Dim MySqr1 As Double = Math.Sqrt(4)  
' Returns 4.79583152331272.  
Dim MySqr2 As Double = Math.Sqrt(23)  
' Returns 0.  
Dim MySqr3 As Double = Math.Sqrt(0)  
' Returns NaN (not a number).  
Dim MySqr4 As Double = Math.Sqrt(-4)  
```  
  
## 使用例  
 この例では、<xref:System.Math> クラスの <xref:System.Math.Tan%2A> メソッドを使って、角度のタンジェントを返します。  
  
```  
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## 要件  
 **クラス**: <xref:System.Math>  
  
 **名前空間**: <xref:System>  
  
 **アセンブリ:** mscorlib \(mscorlib.dll 内\)  
  
## 参照  
 <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>   
 <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>   
 <xref:System.Double.NaN>   
 [Derived Math Functions](../../../visual-basic/language-reference/keywords/derived-math-functions.md)   
 [Arithmetic Operators](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)