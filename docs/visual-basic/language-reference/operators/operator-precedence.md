---
title: "Visual Basic の演算子の優先順位 |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- arithmetic operators, precedence
- operator precedence
- logical operators, precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators
- operators [Visual Basic], precedence
- precedence, of operators
- comparison operators, precedence
- math operators
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6532fc0c26db3b736c863be075571570a3d25eef
ms.lasthandoff: 03/13/2017

---
# <a name="operator-precedence-in-visual-basic"></a>Visual Basic における演算子の優先順位
各部分が評価されと呼ばれる指定された順序で解決されるいくつかの操作は、式の中で発生した場合、*演算子の優先順位*します。  
  
## <a name="precedence-rules"></a>優先順位の規則  
 式に複数のカテゴリから、演算子が含まれている場合は、次の規則に従って評価されます。  
  
-   算術演算と文字列連結演算子の優先順位が次のセクションで説明したが、比較、論理、ほど、優先順位とビット処理演算子。  
  
-   すべての比較演算子は、同じ優先順位と必要なは、ビットごとの論理演算子より優先順位の高いが、算術演算と文字列連結演算子よりも優先順位の低いがあります。  
  
-   論理/ビット処理演算子の優先順位が次のセクションで説明しますが、算術演算子、文字列連結演算子、および比較演算子より優先されます。  
  
-   左から右に優先順位の等しい演算子は評価式での出現順序で。  
  
## <a name="precedence-order"></a>優先順位  
 演算子は優先順位の次の順序で評価されます。  
  
### <a name="await-operator"></a>Await 演算子  
 Await   
  
### <a name="arithmetic-and-concatenation-operators"></a>算術演算や文字列連結演算子  
 指数演算 (`^`)  
  
 単項の id と否定 (`+`、 `–`)  
  
 乗算と除算の浮動小数点 (`*`、 `/`)  
  
 整数除算 (`\`)  
  
 剰余演算 (`Mod`)  
  
 加算と減算 (`+`、 `–`)  
  
 文字列連結 (`&`)  
  
 算術ビット シフト (`<<`、 `>>`)  
  
### <a name="comparison-operators"></a>比較演算子  
 All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)  
  
### <a name="logical-and-bitwise-operators"></a>論理/ビット処理演算子  
 否定 (`Not`)  
  
 連携 (`And`、 `AndAlso`)  
  
 包括的論理和 (`Or`、 `OrElse`)  
  
 排他的論理和 (`Xor`)  
  
### <a name="comments"></a>コメント  
 `=`演算子は等値比較演算子のみ、代入演算子ではありません。  
  
 文字列連結演算子 (`&`)、算術演算子ではありませんが、算術演算子を使用して同じ優先順位。  
  
 `Is`と`IsNot`演算子は、オブジェクト参照の比較演算子です。 2 つのオブジェクトの値を比較しないでこれらは、2 つのオブジェクト変数が同じオブジェクト インスタンスを参照しているかどうかのみを確認します。  
  
## <a name="associativity"></a>結合規則  
 乗算と除算、たとえば、式に同じ優先順位の演算子を並べてを検出すると、左から右に、コンパイラは各操作を評価します。 次に例を示します。  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 1 番目の式では、除算 96/8 (これは、結果は 12) し、除算 12/4 で、結果は 3 です。 コンパイラは、操作を評価するため`n1`左から右から、評価は、同じ順がに対して明示的に指定された場合`n2`します。 両方とも`n1`と`n2`3 つの結果になります。 これに対し、`n3`かっこコンパイラは 8 の評価を強制するため、48 の結果がある/4 最初です。  
  
 この動作のために演算子があると考え*結合関係が左*で[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。  
  
## <a name="overriding-precedence-and-associativity"></a>優先順位と結合規則をオーバーライドします。  
 かっこを使用して、他のユーザーの前に評価される式の一部を強制することができます。 これは、優先順位の順序と左の結合規則の両方に上書きすることができます。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]常に外部の前にかっこで囲まれた操作を実行します。 一方、かっこ内で保持通常の優先順位と結合規則、かっこの中でかっこを使用していない場合。 次に例を示します。  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## <a name="see-also"></a>関連項目  
 [= 演算子](../../../visual-basic/language-reference/operators/assignment-operator.md)   
 [Is 演算子](../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot 演算子](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Like 演算子](../../../visual-basic/language-reference/operators/like-operator.md)   
 [TypeOf 演算子](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [Await 演算子](../../../visual-basic/language-reference/operators/await-operator.md)   
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
