---
title: "ローカル型の推論 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d753d1fbdc60f70dcf0513d809f28a112243c111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="local-type-inference-visual-basic"></a>ローカル型の推論 (Visual Basic)
Visual Basic コンパイラを使用して*型推論*なしで宣言されたローカル変数のデータ型を決定する、`As`句。 コンパイラは、初期化式の型から変数の型を推論します。 これにより、変数を宣言する型を明示的に指定せず、次の例に示すようにできます。 宣言の結果、両方とも`num1`と`num2`整数値として厳密に型指定します。  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]  
 
> [!NOTE]
>  たくない場合`num2`として型指定するのには、前の例で、`Integer`のような宣言を使用して別の型を指定することができます`Dim num3 As Object = 3`または`Dim num4 As Double = 3`です。  

> [!NOTE]
>  型の推論は非静的ローカル変数に対してのみ使用できます。クラスのフィールド、プロパティ、または関数の種類を決定する使用できません。
 
 プロシージャ レベルでローカル型推論が適用されます。 (クラス、構造体、モジュール、またはインターフェイス内にあるが、プロシージャまたはブロック)、モジュール レベルで変数を宣言する使用することはできません。 場合`num2`前の例は、プロシージャ内のローカル変数ではなくクラスのフィールド、ユーザーが、宣言でエラーが発生`Option Strict`、および分類は`num2`として、`Object`で`Option Strict`オフします。 同様に、ローカル型の推定には適用されませんプロシージャ レベルの変数として宣言されている`Static`です。  
  
## <a name="type-inference-vs-late-binding"></a>推論 vs を入力します。遅延バインディング  
 推論では、タイプをコードでは、遅延バインディングに依存するコードに似ています。 ただし、型の推論型を厳密に変数として残さず`Object`です。 コンパイラでは、変数の初期化子を使用して、事前バインディングされたコードを生成するために、コンパイル時に、変数の型を調べます。 前の例では、`num2`と同様、 `num1`、として型指定されて、`Integer`です。  
  
 事前バインディングされた変数の動作は、実行時にのみを型が認識されている、遅延バインディングされた変数の動作とは異なります。 型を事前に知ることにより、コンパイラを実行する前に問題を特定、正確には、メモリの割り当ておよびその他の最適化を実行できます。 事前バインディングでは、Visual Basic の統合開発環境 (IDE) オブジェクトのメンバーに関する IntelliSense のヘルプを提供することもできます。 事前バインディングは、パフォーマンスを優先もできます。 これは、遅延バインディングされた変数に格納されているすべてのデータは、種類としてラップする必要があるため`Object`、低速のプログラムは、実行時に、型のメンバーにアクセスするとします。  
  
## <a name="examples"></a>例  
 型の推論は発生せずにローカル変数が宣言されたときに、`As`句を初期化します。 コンパイラは、変数の型として割り当てられた初期値の型を使用します。 たとえば、次のコード行の各型の変数を宣言`String`です。  
  
 [!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]  
  
 次のコードでは、整数の配列を作成する 2 つの同等の方法を示します。  
  
 [!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]  
  
 ループ コントロール変数の種類を確認する型の推定を使用すると便利です。 次のコードでは、コンパイラが推論される`number`は、`Integer`ため`someNumbers2`前の例は、整数の配列。  
  
 [!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]  
  
 ローカル型推論を使用できる`Using`ステートメントを次の例に示すように、リソース名の型を確立します。  
  
 [!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]  
  
 変数の型は次の例で示すように、関数の戻り値から推論することができますも。 両方`pList1`と`pList2`プロセスの配列は、ため`Process.GetProcesses`プロセスの配列を返します。  
  
 [!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]  
  
## <a name="option-infer"></a>Option Infer  
 `Option Infer`ローカル型推論が、特定のファイルで許可されているかどうかを指定できます。 有効にするにまたは、このオプションをブロックするファイルの先頭に次のステートメントのいずれかを入力します。  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 値を指定しない場合`Option Infer`コンパイラの既定値は、コードで`Option Infer On`です。 アップグレードされたプロジェクトの[!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)]コンパイラの既定値は、以前、または`Option Infer Off`です。  
  
 ファイルの `Option Infer` に設定した値が IDE またはコマンド ラインに設定した値と競合した場合は、ファイルの値が優先されます。  
  
 詳細については、次を参照してください。 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)と[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)です。  
  
## <a name="see-also"></a>関連項目  
 [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [事前バインディングと遅延バインディング](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next ステートメント](../../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
