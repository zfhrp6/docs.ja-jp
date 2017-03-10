---
title: "Option Strict Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Strict"
  - "vb.OptionStrict"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Strict keyword"
  - "Option Strict statement"
  - "conversions, implicit"
  - "late binding"
  - "implicit conversions"
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
caps.latest.revision: 49
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 49
---
# Option Strict Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

暗黙的なデータ型変換を拡大変換だけに制限し、遅延バインディングを禁止し、`Object` 型になる暗黙の型指定を禁止します。  
  
## 構文  
  
```  
Option Strict { On | Off }  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`On`|省略可能です。  `Option Strict` チェックを有効にします。|  
|`Off`|省略可能です。  `Option Strict` チェックを無効にします。|  
  
## 解説  
 `Option Strict On` または `Option Strict` がファイル内にあるとき、次の条件によってコンパイル時のエラーが発生します。  
  
-   暗黙の縮小変換  
  
-   遅延バインディング  
  
-   `Object` 型になる暗黙的な型指定  
  
> [!NOTE]
>  [\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) で設定できる警告の構成には、コンパイル時のエラーの原因となる 3 つの条件に対応する設定があります。  これらの設定の使用方法については、このトピックの後半の「[IDE で警告の構成を設定するには](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions)」を参照してください。  
  
 `Option Strict Off` ステートメントは、3 つの条件すべてで \(関連する IDE 設定でエラーまたは警告がオンになっている場合でも\) エラーと警告のチェックをオフにします。  `Option Strict On` ステートメントは、これらのエラーまたは警告を無効にする関連の IDE 設定を指定して、 3 つすべての条件をチェックするエラーと警告をオンにします。  
  
 `Option Strict` ステートメントを使用する場合は、ファイル内の他のどのコード ステートメントよりも前に記述する必要があります。  
  
 `On`に `Option Strict` を設定すると、 Visual Basic はデータ型はすべてのプログラミング要素に指定されていることを確認します。  データ型を明示的に指定されるか、またはローカル型の推論を使用して指定できます。  すべてのプログラミング要素のデータ型を指定するには、次の原因にお勧めします:  
  
-   変数に対する IntelliSense サポートが有効になります。  これにより、コードの入力時に、プロパティや他のメンバーを表示できます。  
  
-   コンパイラで型チェックを実行できます。  型チェックによって、型変換のエラーによって実行時にエラーになるステートメントを見つけることができます。  また、それらのメソッドをサポートしていないオブジェクトでのメソッドの呼び出しも識別します。  
  
-   これはコードの実行時間を短縮できます。  このの 1 種類の原因は、プログラミング要素のデータ型を指定しない場合、 Visual Basic コンパイラはそれを `Object` 型を割り当てることです。  パフォーマンスが低下するコンパイルされたコードは `Object` と、他のデータ型の間で双方向の変換が必要になる場合があります。  
  
## 暗黙の縮小変換エラー  
 暗黙的なデータ型変換が縮小変換である場合、暗黙の縮小変換エラーが発生します。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、多くのデータ型と他のデータ型との間の変換を行います。  変換元のデータ型より変換先のデータ型の方が精度が低い場合、または容量が小さい場合は、データが失われる可能性があります。  このような縮小変換が失敗した場合は、実行時エラーが発生します。  `Option Strict` を使用すると、実行時エラーを回避できるように、このような縮小変換に対してコンパイル時に通知が出されます。  詳細については、「[Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)」および「[Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
 エラーの原因になる変換には、式の中で発生する暗黙の型変換も含まれます。  詳細については、次のトピックを参照してください。  
  
-   [\+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [\+\= Operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [\/\= Operator](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [Char Data Type](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) を使用して文字列を連結すると、その文字列に対するすべての変換は拡大変換と見なされます。  そのような変換では、`Option Strict` がオンになっている場合でも暗黙の縮小変換エラーは生成されません。  
  
 対応するパラメーターとデータ型が異なる引数を持つメソッドを呼び出すと、`Option Strict` がオンになっている場合は、暗黙の縮小変換によってコンパイル時のエラーが発生します。  コンパイル時のエラーを回避するには、拡大変換または明示的な型変換を使用します。  
  
 `For Each…Next` コレクション内の要素からループ制御変数への変換については、コンパイル時の暗黙の縮小変換エラーは出力されません。  `Option Strict` がオンの場合でも、このエラーは出力されません。  詳細については、「[For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)」の「縮小変換」セクションを参照してください。  
  
## 遅延バインディング エラー  
 `Object` 型として宣言された変数のプロパティまたはメソッドに代入されるオブジェクトは、遅延バインディングされます。  詳細については、「[Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)」を参照してください。  
  
## 暗黙のオブジェクト型エラー  
 宣言された変数の適切な型を推論できず、`Object` の型が推論された場合、暗黙のオブジェクト型エラーが発生します。  このエラーは主に、`As` 句を使用せずに `Dim` ステートメントを使用して変数を宣言し、`Option Infer` が Off である場合に発生します。  詳細については、「[Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md)」および「[Visual Basic Language Specification](../../../visual-basic/reference/language-specification.md)」を参照してください。  
  
 メソッドのパラメーターでは、`Option Strict` がオフの場合は `As` 句は省略可能です。  しかし、いずれかのパラメーターが `As` 句を使用している場合は、すべてのパラメーターがこれを使用する必要があります。  `Option Strict` がオンの場合、`As` 句はすべてのパラメーター定義で必須です。  
  
 `As` 句を使用しないで変数を宣言し、それを `Nothing` に設定した場合、その変数の型は `Object` になります。  `Option Strict` がオンで `Option Infer` もオンの場合、コンパイル時のエラーは発生しません。  次に例を示します: `Dim something = Nothing`  
  
### 既定のデータ型と値  
 次の表に、[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)で、データ型と初期化子をさまざまに組み合わせて指定した場合の結果を示します。  
  
|||||  
|-|-|-|-|  
|データ型が指定されている|初期化子が指定されている|例|結果|  
|Ｘ|Ｘ|`Dim qty`|`Option Strict` が Off \(既定値\) の場合、変数は `Nothing` に設定されます。<br /><br /> `Option Strict` が On の場合、コンパイル時のエラーが発生します。|  
|Ｘ|○|`Dim qty = 5`|`Option Infer` が On \(既定値\) の場合、変数は初期化子のデータ型になります。  「[Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」を参照してください。<br /><br /> `Option Infer` が Off で、`Option Strict` が Off の場合、変数は `Object` のデータ型になります。<br /><br /> `Option Infer` が Off で、`Option Strict` が On の場合、コンパイル時のエラーが発生します。|  
|○|Ｘ|`Dim qty As Integer`|変数は、データ型の既定値に初期化されます。  詳細については、「[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)」を参照してください。|  
|○|○|`Dim qty  As Integer = 5`|初期化子のデータ型が、指定されたデータ型に変換できない場合、コンパイル時のエラーが発生します。|  
  
## Option Strict ステートメントが存在しない場合  
 ソース コードに `Option Strict` ステートメントが含まれていない場合は、[\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) の **Option Strict** 設定が使用されます。  **\[コンパイル\]** ページには、エラーを生成する条件に対するコントロールを追加するための設定があります。  
  
 コマンド ライン コンパイラを使用する場合は、[\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) コンパイラ オプションを使用して `Option Strict`の設定を指定します。  
  
### IDE で Option Strict を設定するには  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **\[コンパイル\]** タブで、**\[Option Strict\]** ボックスの値を設定します。  
  
###  <a name="conditions"></a> IDE で警告の構成を設定するには  
 `Option Strict` ステートメントの代わりに [\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) を使用すると、エラーを生成する条件に対するコントロールを追加できます。  **\[コンパイル\]** ページの **\[警告の構成\]** セクションには、`Option Strict` がオンのときにコンパイル時エラーの原因となる 3 つの条件に対応する設定があります。  その 3 つの設定を次に示します。  
  
-   **暗黙の型変換**  
  
-   **遅延バインディング \(呼び出しは実行時に失敗することがある\)**  
  
-   **暗黙の型 \(想定されるオブジェクト\)**  
  
 **\[Option Strict\]** を **\[On\]** に設定すると、この 3 つの警告の構成の設定はすべて、**\[エラー\]** に設定されます。  **\[Option Strict\]** を **\[Off\]** に設定すると、これらの設定はすべて、**\[なし\]** に設定されます。  
  
 警告の構成の設定を、それぞれ個別に **\[なし\]**、**\[警告\]**、または **\[エラー\]** に変更できます。  この 3 つの警告の構成の設定をすべて **\[エラー\]** に設定すると、`Option strict` ボックスに `On` が表示されます。  すべて **\[なし\]** に設定すると、このボックスには `Off` が表示されます。  これらの設定を他の組み合わせにした場合は、**\[\(カスタム\)\]** が表示されます。  
  
### \[Option Strict\] の既定の設定を新規プロジェクトに設定するには  
 プロジェクトを作成するとき、**\[コンパイル\]** タブの **\[Option Strict\]** 設定は、**\[オプション\]** ダイアログ ボックスの **\[Option Strict\]** 設定の内容に設定されます。  
  
 このダイアログ ボックスで `Option Strict` を設定するには、**\[ツール\]** メニューの **\[オプション\]** をクリックします。  **\[オプション\]** ダイアログ ボックスで、**\[プロジェクトおよびソリューション\]** を展開し、**\[Visual Basic の既定値\]** をクリックします。  **\[Visual Basic の既定値\]** の既定の初期設定は `Off` です。  
  
### コマンド ラインで Option Strict を設定するには  
 **vbc** コマンドに [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) コンパイラ オプションを指定します。  
  
## 使用例  
 暗黙の型変換が縮小変換になるために発生するコンパイル時のエラーの例を次に示します。  このエラーのカテゴリは、**\[コンパイル\]** ページの **\[暗黙的な変換\]** 条件に対応します。  
  
 [!code-vb[VbVbalrStatements#161](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/option-strict-statement_1.vb)]  
  
## 使用例  
 遅延バインディングによるコンパイル時のエラーの例を次に示します。  このエラーのカテゴリは、**\[コンパイル\]** ページの **\[遅延バインディング; 呼び出しは実行時に失敗する可能性があります\]** 条件に対応します。  
  
 [!code-vb[VbVbalrStatements#162](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/option-strict-statement_2.vb)]  
  
## 使用例  
 変数が暗黙的に `Object` 型指定で宣言されたために発生するコンパイル時のエラーの例を次に示します。  このエラーのカテゴリは、**\[コンパイル\]** ページの **\[暗黙的な型; Object と見なされます\]** 条件に対応します。  
  
 [!code-vb[VbVbalrStatements#163](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/option-strict-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#164](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/option-strict-statement_4.vb)]  
  
## 参照  
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)   
 [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [How to: Access Members of an Object](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [Office ソリューションの遅延バインディング](/office-dev/office-dev/late-binding-in-office-solutions)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [\[Visual Basic の既定値\] \(\[オプション\] ダイアログ ボックス \- \[プロジェクト\]\)](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)