---
title: "Local Type Inference (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "local type inference"
  - "vb.TypeInfer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Option Infer statement"
  - "local type inference [Visual Basic]"
  - "implicitly-typed local variables [Visual Basic]"
  - "variables [Visual Basic], type inference"
  - "inference [Visual Basic]"
  - "type inference [Visual Basic]"
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
caps.latest.revision: 43
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 43
---
# Local Type Inference (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Visual Basic のコンパイラでは、*型の推定*を使用して、`As` 句なしで宣言されているローカル変数のデータ型を決定します。  コンパイラは、初期化式の型から変数の型を推測します。  これにより、次の例で示すように、型を明示的に示さずに変数を宣言できます。この宣言の結果、`num1` と `num2` はどちらも整数として厳密に型指定されます。  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]  
  
> [!NOTE]
>  前の例の `num2` を `Integer` として型指定できない場合は、`Dim num3 As Object = 3` や `Dim num4 As Double = 3` のような宣言を使用して、別の型を指定できます。  
  
 ローカル型の推定は、プロシージャ レベルで適用されます。  モジュール レベル \(同じクラス、構造体、モジュール、インターフェイス内にあるが、プロシージャやブロックは異なる\) での変数の宣言には使用できません。  前の例の `num2` がプロシージャのローカル変数ではなくクラスのフィールドである場合は、`Option Strict` がオンのときは宣言がエラーになり、`Option Strict` がオフのときは `num2` は `Object` として分類されます。  同様に、ローカル型推論は、`Static` として宣言されたプロシージャ レベルの変数には適用されません。  
  
## 型の推論と遅延バインディング  
 型の推論を使用するコードは、遅延バインディングに依存するコードと似ています。  ただし、型の推論は、変数を `Object` のままにするのではなく、変数の型を厳密に指定します。  コンパイラは、変数の初期化子を使用してコンパイル時に変数の型を決定し、事前バインディングされたコードを生成します。  前の例では、`num2` は、`num1` と同様に `Integer` として型指定されます。  
  
 事前バインディングされた変数の動作は、実行時でないと型がわからない遅延バインディングされた変数の動作とは異なります。  事前に型がわかっていると、コンパイラは、実行前に問題を識別し、メモリを正確に割り当て、他の最適化を実行することができます。  また、事前バインディングを使用すると、Visual Basic の統合開発環境 \(IDE: Integrated Development Environment\) は、オブジェクトのメンバーに関する IntelliSense ヘルプを提供できます。  事前バインディングには、パフォーマンスの点でもメリットがあります。  これは、遅延バインディングされた変数に格納されるデータはすべて `Object` 型としてラップされる必要があり、実行時には型のメンバーにアクセスするので、プログラムが遅くなるためです。  
  
## 例  
 型の推論は、`As` 句なしで宣言されたローカル変数が初期化される場合に行われます。  コンパイラは、変数の型として、代入された初期値の型を使用します。  たとえば、次の各コード行は、`String` 型の変数を宣言しています。  
  
 [!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]  
  
 次のコードは、整数の配列を作成する 2 種類の同等の方法を示します。  
  
 [!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]  
  
 型の推論を使用すると、ループ制御変数の型を決定する場合に便利です。  次のコードでは、前の例の `someNumbers2` が整数の配列なので、コンパイラは `number` が `Integer` であると推論します。  
  
 [!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]  
  
 次の例で示すように、ローカル型の推論を `Using` ステートメントで使用して、リソース名の型を設定できます。  
  
 [!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]  
  
 次の例で示すように、関数の戻り値から変数の型を推論することもできます。  `Process.GetProcesses` はプロセスの配列を返すため、`pList1` と `pList2` はどちらもプロセスの配列です。  
  
 [!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]  
  
## Option Infer  
 ローカル型の推論が特定のファイルで許可されているかどうか `Option Infer` を指定します。  このオプションを有効または無効にするには、次のいずれかのステートメントをファイルの先頭に追加します。  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 コード内で `Option Infer` の値を指定しなければ、コンパイラは既定で `Option Infer On` になります。  [!INCLUDE[vb_orcas_long](../../../../visual-basic/misc/includes/vb-orcas-long-md.md)] 以前からアップグレードされたプロジェクトの場合、コンパイラは既定で `Option Infer Off` になります。  
  
 ファイル内の `Option Infer` の設定値が、IDE またはコマンド ラインでの設定値と競合する場合は、ファイル内の値が優先します。  
  
 詳細については、「[Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)」および「[\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)」を参照してください。  
  
## 制約  
 型の推論は、静的ではないローカル変数に対してのみ使用できます。クラスのフィールド、プロパティ、または関数の型を決定するためには使用できません。  
  
## 参照  
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)   
 [For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [For...Next ステートメント](../../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [\/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)