---
title: "Option Infer Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.OptionInfer"
  - "vb.Infer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], declaring"
  - "Option Infer statement"
  - "Infer keyword"
  - "declaring variables, inferred"
  - "inferred variable declaration"
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
caps.latest.revision: 72
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 72
---
# Option Infer Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数の宣言でローカル型推論を使用できるようにします。  
  
## 構文  
  
```  
Option Infer { On | Off }  
```  
  
## 指定項目  
  
|||  
|-|-|  
|用語|定義|  
|`On`|省略可能です。  ローカル型推論を有効にします。|  
|`Off`|省略可能です。  ローカル型推論を無効にします。|  
  
## 解説  
 ファイルに `Option Infer` を設定するには、ファイルの先頭に他のソース コードよりも前に `Option Infer On` または `Option Infer Off` を入力します。  ファイルの `Option Infer` に設定した値が IDE またはコマンド ラインに設定した値と競合した場合は、ファイルの値が優先されます。  
  
 `Option Infer` を `On` に設定すると、データ型を明示的に指定せずにローカル変数を宣言できます。  コンパイラは、初期化式の型から変数のデータ型を推測します。  
  
 次の図では、`Option Infer` がオンになっています。  宣言 `Dim someVar = 2` 内の変数は、型の推定によって整数として宣言されています。  
  
 ![宣言の IntelliSense ビュー。](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")  
Option Infer がオンのときの IntelliSense  
  
 次の図では、`Option Infer` がオフになっています。  宣言 `Dim someVar = 2` 内の変数は、型の推定によって `Object` として宣言されています。  この例では、**Option Strict** 設定は [\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) で **Off** に設定されています。  
  
 ![宣言の IntelliSense ビュー。](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")  
Option Infer がオフのときの IntelliSense  
  
> [!NOTE]
>  変数を `Object` として宣言すると、プログラムの実行中にランタイム型が変更される場合があります。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、*ボックス化*と*ボックス化解除*という操作を実行して `Object` と値型との間で変換を行いますが、このために実行速度が低下します。  ボックス化とボックス化解除については、「[Visual Basic Language Specification](../../../visual-basic/reference/language-specification.md)」を参照してください。  
  
 型の推定は、プロシージャ レベルで適用され、クラス、構造体、モジュール、またはインターフェイスのプロシージャの外側には適用されません。  
  
 詳細については、「[Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」を参照してください。  
  
## Option Infer ステートメントが指定されていない場合  
 ソース コードに `Option Infer` ステートメントが含まれていない場合は、[\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) の **Option Infer** 設定が使用されます。  コマンド ライン コンパイラを使用した場合は、[\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) コンパイラ オプションが使用されます。  
  
#### IDE の Option Infer を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/ja-jp/983f3c18-832f-4666-afec-74b716ff3e0e)」を参照してください。  
  
2.  **\[コンパイル\]** タブをクリックします。  
  
3.  **\[Option infer\]** ボックスに値を設定します。  
  
 新しいプロジェクトを作成すると、**\[コンパイル\]** タブの **\[Option Infer\]** 設定が **\[VISUAL BASIC の既定値\]** ダイアログ ボックスの **\[Option Infer\]** 設定に設定されます。  **\[VISUAL BASIC の既定値\]** ダイアログ ボックスにアクセスするには、**\[ツール\]** メニューで **\[オプション\]** をクリックします。  **\[オプション\]** ダイアログ ボックスの **\[プロジェクトおよびソリューション\]** を展開し、**\[VISUAL BASIC の既定値\]** をクリックします。  **\[VISUAL BASIC の既定値\]** の初期の既定値は `On` です。  
  
#### コマンド ラインで Option Infer を設定するには  
  
-   **vbc** コマンドに [\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) コンパイラ オプションを含めます。  
  
## 既定のデータ型と値  
 次の表では、`Dim` ステートメントのデータ型と初期化子を指定するさまざまな組み合わせの結果を示します。  
  
|||||  
|-|-|-|-|  
|データ型が指定されているか|初期化子が指定されているか|例|結果|  
|Ｘ|Ｘ|`Dim qty`|`Option Strict` がオフ \(既定値\) の場合、変数は `Nothing` に設定されます。<br /><br /> `Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|Ｘ|○|`Dim qty = 5`|`Option Infer` がオン \(既定値\) の場合、変数は初期化子のデータ型になります。  「[Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」を参照してください。<br /><br /> `Option Infer` がオフで、`Option Strict` がオフの場合、変数は `Object` のデータ型になります。<br /><br /> `Option Infer` がオフで、`Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|○|Ｘ|`Dim qty As Integer`|変数は、データ型の既定値に初期化されます。  詳細については、「[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)」を参照してください。|  
|○|○|`Dim qty  As Integer = 5`|初期化子のデータ型を指定したデータ型に変換できない場合は、コンパイル時エラーが発生します。|  
  
## 使用例  
 次の例では、`Option Infer` ステートメントがローカル型推論をどのように有効にするかを示します。  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/option-infer-statement_1.vb)]  
  
## 使用例  
 次の例では、変数が `Object` として識別されたときに、ランタイム型が異なる場合があることを示します。  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/option-infer-statement_2.vb)]  
  
## 参照  
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [\[Visual Basic の既定値\] \(\[オプション\] ダイアログ ボックス \- \[プロジェクト\]\)](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)   
 [\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [ボックス化とボックス化解除](../../../csharp/programming-guide/types/boxing-and-unboxing.md)