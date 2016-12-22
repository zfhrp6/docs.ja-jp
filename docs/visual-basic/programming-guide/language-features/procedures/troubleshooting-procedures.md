---
title: "Troubleshooting Procedures (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "troubleshooting Visual Basic, procedures"
  - "procedures, troubleshooting"
  - "Visual Basic code, procedures"
  - "troubleshooting procedures"
  - "procedures, about procedures"
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Troubleshooting Procedures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

ここでは、プロシージャを使用する際に起きる一般的な問題についていくつか説明します。  
  
## Function プロシージャから配列型を返す  
 `Function` プロシージャが配列型を返す場合は、`Function` 名を使って配列の各要素に値を格納することはできません。  格納しようとすると、コンパイラによって `Function` の呼び出しと解釈されます。  たとえば、次のコードはコンパイル エラーになります。  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 `allOnes(i) = 1` ステートメントは、間違った型の引数 \(`Integer` 配列ではなく単一の `Integer`\) を指定して `allOnes` を呼び出していると解釈されるため、ここでコンパイル エラーが発生します。  `Return allOnes()` ステートメントはコンパイル エラーを発生します。引数を指定せずに `allOnes` を呼び出していると解釈されるからです。  
  
 **正しい方法:** 返される配列の要素を変更できるようにするには、内部配列をローカル変数として定義します。  次の例はコンパイル エラーが発生しません。  
  
 [!code-vb[VbVbcnProcedures#66](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]  
  
## 引数がプロシージャ呼び出しによって変更されない  
 呼び出しコードの引数の基になるプログラミング要素を、プロシージャで変更できるようにする場合は、参照渡しで渡す必要があります。  ただし、値渡しで渡した場合でも、プロシージャはその参照型の引数の要素にアクセスできます。  
  
-   **基になる変数** 基になる変数の要素の値そのものをプロシージャで変更できるようにするには、プロシージャのパラメーターを [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) で宣言する必要があります。  また、呼び出しコードで引数をかっこで囲んで記述しないでください。こうすると、`ByRef` で引数を渡す機能がオーバーライドされるからです。  
  
-   **型参照要素** パラメーターを [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) で宣言すると、基になる変数要素そのものをプロシージャで変更できなくなります。  しかし、引数が参照型であれば、プロシージャは変数の値を置き換えることはできませんが、引数が指すオブジェクトのメンバーを変更できます。  たとえば、引数が配列変数であった場合、プロシージャは新しい配列を代入することはできませんが、その 1 つ以上の要素を変更できます。  変更した要素は、呼び出し元のコードの基の配列変数に反映されます。  
  
 次の例には、配列変数を値渡しで受け取ってその要素を操作する 2 つのプロシージャが定義されています。  `increase` プロシージャは、各要素に単純に 1 を加算します。  `replace` プロシージャは、パラメーター `a()` に新しい配列を代入してから各要素に 1 を加算します。  ただし、この新しい配列の代入は、呼び出し元のコードの基の配列変数には反映されません。なぜなら、`a()` が `ByVal` で宣言されているからです。  
  
 [!code-vb[VbVbcnProcedures#35](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]  
  
 次に、`increase` と `replace` を呼び出す例を示します。  
  
 [!code-vb[VbVbcnProcedures#37](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]  
  
 最初の `MsgBox` の呼び出しでは、"After increase\(n\): 11, 21, 31, 41" と表示されます。  `n` が参照型なので、`ByVal` で渡されていても `increase` はそのメンバーを変更できます。  
  
 2 番目の `MsgBox` の呼び出しでは、"After replace\(n\): 11, 21, 31, 41" と表示されます。  `n` が `ByVal` で渡されたため、`replace` は変数 `n` を、新しい配列を代入するという方法で変更できません。  `replace` が新しい配列インスタンス `k` を作成し、そこにローカル変数 `a` を代入すると、呼び出しコードによって渡された `n` への参照が失われます。  `a` のメンバーをインクリメントすると、ローカル変数 `k` だけに反映されます。  
  
 **正しい方法:** 基になる変数要素そのものを変更可能にするには、参照渡しで渡します。  `replace` の宣言を変更し、呼び出しコードで配列を別の配列に置き換えることができるようにする例を次に示します。  
  
 [!code-vb[VbVbcnProcedures#64](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]  
  
## オーバーロードを定義できない  
 プロシージャのオーバーロードを定義する場合は、名前を同じにしてシグネチャを変える必要があります。  シグネチャが同じで、コンパイラがプロシージャ宣言をオーバーロードと区別できない場合は、エラーが発生します。  
  
 プロシージャの*シグネチャ*は、プロシージャ名とパラメーター リストによって決まります。  各オーバーロードは名前がすべて同じである必要がありますが、シグネチャのその他のコンポーネントについては、少なくとも 1 つが他のいずれとも同じでないことが必要です。  詳細については、「[Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)」を参照してください。  
  
 次の項目は、パラメーター リストに記述されますが、プロシージャのシグネチャのコンポーネントには含まれません。  
  
-   `Public`、`Shared`、`Static` などのプロシージャ修飾子キーワード  
  
-   パラメーター名  
  
-   `ByRef` や `Optional` などのパラメーター修飾子キーワード  
  
-   戻り値のデータ型 \(変換演算子以外\)  
  
 これらの項目を変更するだけでは、プロシージャをオーバーロードすることはできません。  
  
 **正しい方法:** プロシージャのオーバーロードを定義するには、シグネチャを変える必要があります。  名前は同じでなくてはならないため、パラメーターの数、順序、またはデータ型を変えることが必要です。  ジェネリック プロシージャの場合は、型パラメーターの数を変更できます。  変換演算子 \([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)\) の場合は、戻り値の型を変更できます。  
  
### 省略可能な引数やパラメーター配列の引数を持つオーバーロードの解決  
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) パラメーターまたは [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) パラメーターを持つプロシージャをオーバーロードする場合は、*暗黙のオーバーロード*を重複させないよう注意する必要があります。  詳細については、「[Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)」を参照してください。  
  
## オーバーロードされたプロシージャのうち、正しい形式を呼び出すことができない  
 プロシージャが複数の形式でオーバーロードされている場合は、それらすべてのパラメーター リストをよく確認することと、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] が複数のオーバーロードの中からどのように呼び出しを解決するかを理解することが必要です。  そうしないと、意図した形式と異なるオーバーロードを呼び出す可能性があります。  
  
 どのオーバーロードを呼び出すか決定したら、次の規則に注意して従ってください。  
  
-   正しい数の引数を、正しい順序で指定する。  
  
-   最も望ましいのは、引数の型が対応するパラメーターの型とまったく同じであることです。  そうでない場合でも、各引数のデータ型は対応するパラメーターの型よりも小さいことが必要です。  これは [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) に `Off` が設定されている場合でも同じです。  オーバーロードが引数リストによって縮小変換する必要が生じれば、そのオーバーロードは呼び出しの対象から外されます。  
  
-   拡大変換を必要とする引数を指定する場合は、対応するパラメーターにデータ型をできるだけ近づけるようにしてください。  引数のデータ型を許容するオーバーロードが 2 つ以上ある場合、コンパイラは拡大変換の量が最も少ないオーバーロードに呼び出しを解決します。  
  
 引数を指定するとき、変換キーワード [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md) を使用すると、データ型の不一致の可能性を減らすことができます。  
  
### オーバーロードの解決エラー  
 オーバーロードされたプロシージャを呼び出すと、コンパイラは 1 つを除くすべてのオーバーロードの除外を試みます。  うまく除外できれば、呼び出しをそのオーバーロードに解決します。  すべてのオーバーロードが除外された場合、またはオーバーロードの候補を 1 つに絞ることができない場合は、エラーが発生します。  
  
 次の例は、オーバーロード解決のプロセスを示しています。  
  
 [!code-vb[VbVbcnProcedures#62](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]  
  
 1 回目の呼び出しでは、コンパイラは最初のオーバーロードを除外します。1 つ目の引数の型 \(`Short`\) が、対応するパラメーターの型 \(`Byte`\) よりも大きいからです。  次に、3 番目のオーバーロードを除去します。2 番目のオーバーロードの各引数型 \(`Short` と `Single`\) よりも、3 番目のオーバーロードで対応する引数型 \(`Integer` と `Single`\) の方が大きいからです。  2 番目のオーバーロードの方が拡大変換が少なくて済むため、コンパイラは 2 番目を使用して呼び出します。  
  
 2 回目の呼び出しでは、コンパイラは引数の型が大きすぎるという理由でオーバーロードを除外できません。  3 番目のオーバーロードは、1 回目の呼び出しのときと同じ理由で除外されます。2 番目のオーバーロードを呼び出した方が引数の型の拡大変換が少なくて済むからです。  しかし、コンパイラは 1 番目と 2 番目のオーバーロードのいずれかに解決できません。  どちらにも、対応する型に拡大変換されるパラメーター型が 1 つ定義されています \(`Byte` から `Short`、そして `Single` から `Double`\)。  このため、オーバーロード解決エラーが生成されます。  
  
 **正しい方法:** オーバーロードされたプロシージャを明確に呼び出すには、[CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md) を使用して引数のデータ型をパラメーターの型に一致させます。  次の例で呼び出される `z` は、必ず 2 番目のオーバーロードに解決します。  
  
 [!code-vb[VbVbcnProcedures#65](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]  
  
### 省略可能な引数やパラメーター配列の引数を持つオーバーロードの解決  
 プロシージャの 2 つのオーバーロードのシグネチャが同じで、唯一の違いが最後のパラメーターの宣言 \(一方が [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) で、他方は [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)\) である場合、コンパイラはそのプロシージャの呼び出しを、より厳密に一致している方に解決します。  詳細については、「[Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)」を参照してください。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)