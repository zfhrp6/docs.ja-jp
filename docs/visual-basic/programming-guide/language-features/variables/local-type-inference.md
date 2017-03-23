---
title: "ローカル型推論 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- local type inference
- vb.TypeInfer
dev_langs:
- VB
helpviewer_keywords:
- Option Infer statement
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
caps.latest.revision: 43
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 2bb673ce871b8e875f62c373404a849c139ab598
ms.lasthandoff: 03/13/2017

---
# <a name="local-type-inference-visual-basic"></a>ローカル型の推論 (Visual Basic)
Visual Basic コンパイラを使用して*型の推論*なしで宣言されたローカル変数のデータ型を決定する、`As`句。 コンパイラは、初期化式の型から変数の型を推論します。 これにより、次の例のように、型を明示的に指定せず変数を宣言することができます。 宣言の結果、両方とも`num1`と`num2`整数として厳密に型指定します。  
  
 [!code-vb[VbVbalrTypeInference&#1;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]  
  
> [!NOTE]
>  たくない場合`num2`として入力するのには、前の例で、`Integer`のような宣言を使用して別の種類を指定することができます`Dim num3 As Object = 3`または`Dim num4 As Double = 3`です。  
  
 プロシージャ レベルでローカル型推論が適用されます。 (クラス、構造体、モジュール、またはインターフェイス内では、プロシージャまたはブロック内ではなく)、モジュール レベルで変数を宣言する使用することはできません。 場合`num2`前の例では、プロシージャ内のローカル変数ではなくクラスのフィールドでエラーが発生すると、宣言`Option Strict`、および分類は`num2`として、`Object`と`Option Strict`オフします。 同様に、ローカル型の推論には当てはまりませんプロシージャ レベルの変数として宣言されている`Static`します。  
  
## <a name="type-inference-vs-late-binding"></a>型の推論と遅延バインディング  
 推論タイプをコードでは、遅延バインディングに依存するコードに似ています。 ただし、型の推論型を厳密として残さず変数`Object`します。 コンパイラでは、変数の初期化子を使用して、事前バインディングされたコードを作成するコンパイル時に、変数の型を調べます。 前の例で`num2`と同様に`num1`、として型指定された、`Integer`です。  
  
 事前バインディングされた変数の動作は、実行時にのみを型が認識されている、遅延バインディングされた変数の動作とは異なります。 型の早い段階により、コンパイラは、実行前に問題を識別するために理解していれば、正確には、メモリを割り当てし、その他の最適化を実行します。 事前バインディングでは、Visual Basic の統合開発環境 (IDE) のオブジェクトのメンバーについて IntelliSense のヘルプを提供することもできます。 事前バインディングもパフォーマンスの優先的に使用できます。 これは、遅延バインディングされた変数に格納されているすべてのデータは、型としてラップする必要があるために、 `Object`、低速のプログラムは、実行時に、型のメンバーにアクセスするとします。  
  
## <a name="examples"></a>例  
 型の推定が発生せず、ローカル変数が宣言されている場合、`As`句と初期化します。 コンパイラは、変数の型として割り当てられた初期値の型を使用します。 たとえば、次のコード行の各型の変数を宣言`String`します。  
  
 [!code-vb[VbVbalrTypeInference&#2;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]  
  
 次のコードでは、整数の配列を作成する&2; つの同等の方法を示します。  
  
 [!code-vb[VbVbalrTypeInference&#3;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]  
  
 型の推論を使用して、ループ制御変数の型を確認すると便利です。 次のコードに、コンパイラが推論される`number`は、`Integer`ため`someNumbers2`前の例は、整数の配列。  
  
 [!code-vb[VbVbalrTypeInference&4;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]  
  
 ローカル型推論を使用できる`Using`ステートメントを次の例に示すように、リソース名の型を設定します。  
  
 [!code-vb[VbVbalrTypeInference&#7;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]  
  
 次の例に示すように、変数の型を関数の戻り値から推論もことができます。 両方とも`pList1`と`pList2`ためのプロセスの配列である`Process.GetProcesses`プロセスの配列を返します。  
  
 [!code-vb[VbVbalrTypeInference&#5;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]  
  
## <a name="option-infer"></a>Option Infer します。  
 `Option Infer`特定のファイルでローカル型推論を許可するかどうかを指定できます。 有効にするか、オプションは、ファイルの先頭に次のステートメントのいずれかを入力します。  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 値が指定されていない場合`Option Infer`コンパイラの既定値は、コードでは、`Option Infer On`です。 アップグレードされたプロジェクトの[!INCLUDE[vb_orcas_long](../../../../visual-basic/misc/includes/vb_orcas_long_md.md)]コンパイラの既定値は、前の手順では、または`Option Infer Off`です。  
  
 ファイルの `Option Infer` に設定した値が IDE またはコマンド ラインに設定した値と競合した場合は、ファイルの値が優先されます。  
  
 詳細については、次を参照してください。 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)と[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)します。  
  
## <a name="restrictions"></a>制限事項  
 型の推論は、非静的ローカル変数に対してのみ使用できます。クラスのフィールド、プロパティ、または関数の種類を判断に使用できません。  
  
## <a name="see-also"></a>関連項目  
 [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [事前バインディングと遅延バインディング](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)   
 [各.次のステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [.次のステートメント](../../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
