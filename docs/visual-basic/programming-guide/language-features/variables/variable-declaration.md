---
title: "Visual Basic での変数宣言 | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "変数 [Visual Basic]、宣言"
  - "メンバー変数、宣言"
  - "Dim ステートメント、変数宣言"
  - "宣言 (変数を)"
  - "変数 [Visual Basic]、スコープ"
  - "変数 [Visual Basic]、データ型"
  - "データ型 [Visual Basic]、変数宣言"
  - "有効期間、変数"
  - "変数 [Visual Basic]、有効期間"
  - "アクセス レベル、変数"
  - "スコープ、宣言ステートメント"
  - "変数 [Visual Basic]、アクセス レベル"
  - "ローカル変数、宣言"
  - "スコープ、変数"
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: 31
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 31
---
# Visual Basic での変数宣言
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数を宣言して、変数の名前と特性を指定します。  変数の宣言ステートメントは、[Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) です。  このステートメントの場所と内容により、変数の特性が決まります。  
  
 変数の名前付け規則および考慮事項については、「[Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
## 宣言のレベル  
  
### ローカル変数およびメンバー変数  
 プロシージャ内で宣言された変数を*ローカル変数*と呼びます。  *メンバー変数*は、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 型のメンバーです。これは、クラス、構造体、またはモジュールの内部のプロシージャ内ではなく、クラス、構造体、またはモジュール内のモジュール レベルで宣言されます。  
  
### 共有変数およびインスタンス変数  
 クラスや構造体では、メンバー変数の変数のカテゴリは、その変数が共有されているかどうかによって決まります。  [共有](../../../../visual-basic/language-reference/modifiers/shared.md)キーワードを使って宣言した変数は*共有変数*となり、クラスや構造体のすべてのインスタンスが 1 つのコピーを共有します。  
  
 それ以外の変数は*インスタンス変数*となり、クラスや構造体の各インスタンスごとにコピーが作成されます。  インスタンス変数のコピーが作成されたクラスまたは構造体のインスタンスにのみ使用できます。  これは、クラスまたは構造体の他のインスタンスのインスタンス変数のコピーから独立しています。  
  
## データ型の宣言  
 宣言ステートメントで [As](../../../../visual-basic/language-reference/statements/as-clause.md) 句を使用すると、宣言する変数のデータ型またはオブジェクトの型を定義できます。  変数に指定できる型は次のとおりです。  
  
-   `Boolean`、`Long`、`Decimal` などの基本データ型  
  
-   配列や構造体などの複合データ型  
  
-   作成したアプリケーションまたはその他のアプリケーションのいずれかで定義された、オブジェクト型またはクラス  
  
-   <xref:System.Windows.Forms.Label>、<xref:System.Windows.Forms.TextBox> などの [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] クラス  
  
-   <xref:System.IComparable> または <xref:System.IDisposable> などのインターフェイス型  
  
 1 つのステートメントで複数の変数を宣言できます。この場合、データ型を繰り返す必要はありません。  次のステートメントでは、変数 `i`、`j`、および `k` は `Integer` 型として、`l` と `m` は `Long` 型として、`x` と `y` は `Single` 型として、それぞれ宣言されています。  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 データ型の詳細については、「[データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)」を参照してください。  オブジェクトの詳細については、「[Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)」および「[コンポーネントによるプログラミング](../Topic/Programming%20with%20Components.md)」を参照してください。  
  
## ローカル型の推論  
 *型の推論* は、`As` 句なしで宣言されているローカル変数のデータ型の決定に使用されます。  コンパイラは、初期化式の型から変数の型を推測します。  これにより、型を明示的に指定せずに変数を宣言することができます。  次の例では、`num1` と `num2` は両方とも整数として厳密に型指定されています。  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]  
  
 ローカル型の推論を使用する場合には、`Option Infer` を `On` に設定する必要があります。  詳細については、「[Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」および「[Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)」を参照してください。  
  
## 宣言された変数の特性  
 変数の*有効期間*とは、その変数を使用できる期間です。  一般的には、\(プロシージャまたはクラスなどの\) 変数が宣言された要素が存在し続ける限り、変数は存在します。  変数がコンテナー要素の有効期間を存続させる必要がある申告で特別な処理を行う必要はありません。  コンテナー 要素の有効期間よりも長く変数を存続させる必要がある場合は、`Dim` ステートメントに `Static` キーワード、または `Shared` キーワードを含めます。  詳細については、「[Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)」を参照してください。  
  
 変数の*スコープ*とは、名前に修飾子を付けずにその変数を参照できるコードの範囲です。  変数のスコープは、変数を宣言した位置で決まります。  変数を定義した領域にあるコードでは、名前に修飾子を付けずにその変数を使用できます。  詳細については、「[Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)」を参照してください。  
  
 変数の*アクセス レベル*は、変数へのアクセス許可を持ったコードのエクステントです。  これは、`Dim` ステートメントで使用する、\([Public](../../../../visual-basic/language-reference/modifiers/public.md) または [Private](../../../../visual-basic/language-reference/modifiers/private.md) などの\) アクセス修飾子で決まります。  詳細については、「[Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
## 参照  
 [How to: Create a New Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)   
 [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)   
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)   
 [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)