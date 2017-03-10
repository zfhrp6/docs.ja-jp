---
title: "With...End With Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.With"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "With keyword"
  - "loop structures, and With...End With statements"
  - "execution, on object"
  - "instructions, repeating"
  - "With...End With statements"
  - "With statement"
  - "With statement, nesting"
  - "objects [Visual Basic], accessing"
  - "With block"
  - "End keyword, With...End With statements"
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
caps.latest.revision: 34
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 34
---
# With...End With Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

オブジェクトまたは構造のメンバーにアクセスする場合にステートメントで簡単な構文を使用できるように、単一のオブジェクトまたは構造を繰り返し参照する一連のステートメントを実行します。構造体の使用時には、メンバー値の読み取りまたはメソッドの呼び出しのみを行うことができます。また、`With...End With` ステートメントで使用されている構造体のメンバーに値を割り当てようとすると、エラーが発生します。  
  
## 構文  
  
```  
With objectExpression  
    [ statements ]  
End With  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語|定義|  
|`objectExpression`|必須。  オブジェクトとして評価される式。  この式は、任意で複雑にできます。評価されるのは 1 回のみです。  基本データ型だけでなく、どのデータ型として評価される式でも指定できます。|  
|`statements`|省略可能。  `objectExpression` の評価によって生成されるオブジェクトのメンバーを参照できる、`With` と `End With` 間の 1 つ以上のステートメント。|  
|`End With`|必須。  `With` ブロックの定義を終了します。|  
  
## 解説  
 `With...End With` を使用すると、特定のオブジェクトの名前を複数回指定することなく、そのオブジェクトに対して一連のステートメントを実行できます。  `With` ステートメント ブロック内では、先頭に `With` ステートメント オブジェクトを付ける場合と同様に、先頭にピリオドを付けてオブジェクトのメンバーを指定できます。  
  
 たとえば、単一のオブジェクトに対して複数のプロパティを変更する場合、プロパティを割り当てるステートメントを `With...End With` ブロック内に指定すると、プロパティを割り当てるたびにオブジェクトを参照するのではなく、一度参照するだけで済みます。  
  
 コードの複数のステートメントで同じオブジェクトにアクセスする場合、`With` ステートメントを使用することにより次の利点が得られます。  
  
-   複雑な式を複数回評価したり、そのメンバーを複数回参照するために一時変数に結果を割り当てたりする必要はありません。  
  
-   反復的な修飾式の使用を避けることにより、コードを読みやすくします。  
  
 `objectExpression` のデータ型には、任意のクラス型や構造体の型、または Visual Basic の基本型 \(`Integer` など\) も使用できます。`objectExpression` の結果がオブジェクト以外になる場合、メンバー値の読み取りまたはメソッドの呼び出しのみを行うことができます。また、`With...End With` ステートメントで使用されている構造体のメンバーに値を割り当てようとすると、エラーが発生します。これは、構造体を返したメソッドを呼び出し、`GetAPoint().x = 1` など、関数の結果のメンバーにアクセスして直ちに値を割り当てた場合に発生するエラーと同じです。いずれの場合も問題になるのは、構造体が呼び出し履歴にのみ存在することです。また、こうした状況で変更された構造体のメンバーが、プログラム内の他のコードが変更を確認できるような方法でいずれかの場所に書き込むことができません。  
  
 `objectExpression` は、ブロックへの入力時にのみ評価されます。  `With` ブロック内から `objectExpression` を再度割り当てることはできません。  
  
 `With` ブロック内で、修飾せずにアクセスできるのは、指定したオブジェクトのメソッドやプロパティだけです。  他のオブジェクトのメソッドやプロパティを使用するには、オブジェクト名で修飾する必要があります。  
  
 `With...End With` ステートメントは入れ子に配置できます。  入れ子の `With...End With` ステートメントは、参照されているオブジェクトがコンテキストから明確でない場合、混乱を招くことがあります。  内側の `With` ブロックの内部からオブジェクトが参照された場合、外側の `With` ブロックにあるオブジェクトに対する完全修飾参照を提供する必要があります。  
  
 ブロック外から `With` ステートメント ブロックに分岐することはできません。  
  
 ブロックの内部にループがなければ、ステートメントは一度だけ実行されます。  さまざまな種類の制御構造を入れ子にできます。  詳細については、「[Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)」を参照してください。  
  
> [!NOTE]
>  また、オブジェクト初期化子で `With` キーワードを使用することもできます。  使用例を含む詳細については、「[Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)」および「[Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
>   
>  直前にインスタンス化したオブジェクトのプロパティまたはフィールドのみを `With` ブロックを使用して初期化する場合は、代わりにオブジェクト初期化子を使用することを考慮します。  
  
## 使用例  
 次の例では、各 `With` ブロックが単一のオブジェクトに対して一連のステートメントを実行します。  
  
 [!code-vb[VbVbalrWithStatement#2](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/vbwpfapp/mainwindow.xaml.vb#2)]  
  
## 使用例  
 次の例では、`With…End With` ステートメントを入れ子にしています。  入れ子にされた `With` ステートメント内の構文では、内側のオブジェクトを参照します。  
  
 [!code-vb[VbVbalrWithStatement#1](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/vbwpfapp/mainwindow.xaml.vb#1)]  
  
## 参照  
 <xref:System.Collections.Generic.List%601>   
 [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)