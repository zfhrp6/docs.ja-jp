---
title: "On Error Statement (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.OnError"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, control flow"
  - "Resume Next statement"
  - "errors [Visual Basic], trapping"
  - "error handling, On Error statement"
  - "Next statement, On Error"
  - "control flow, branching"
  - "Error keyword"
  - "execution, conditional"
  - "Resume statement, and On Error statement"
  - "Error statement, and On Error statement"
  - "GoTo statement, and On Error statement"
  - "branching, on error"
  - "conditional statements, On Error"
  - "On Error statement, syntax"
  - "On keyword"
  - "run-time errors, handling"
  - "On Error statement"
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# On Error Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

エラー処理ルーチンを有効にして、プロシージャ内でルーチンの場所を指定します。また、エラー処理ルーチンを無効にする場合にも使用できます。  
  
 `On Error` ステートメントを使用しないと、発生するすべてのランタイム エラーが致命的なエラーになります。つまり、エラー メッセージが表示され、実行が停止します。  
  
 可能であればコードで例外処理を使用することをお勧めします\)非構造化例外処理と `On Error` のステートメントを使用する必要がありません。  詳細については、「[Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」を参照してください。  
  
> [!NOTE]
>  [Error Statement](../../../visual-basic/language-reference/statements/error-statement.md)では `Error` キーワードも使用されます。これは、下位互換性のためにサポートされています。  
  
## 構文  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`GoTo` `line`|必須の `line` 引数で指定した行から始まるエラー処理ルーチンを有効にします。  引数 `line` には、任意の行ラベルまたは行番号を指定します。  ランタイム エラーが発生すると、指定した行に制御が分岐され、エラー ハンドラーがアクティブになります。  `On Error` ステートメントと同じプロシージャ内の行を指定する必要があります。それ以外の行を指定すると、コンパイル エラーが発生します。|  
|`GoTo` 0|現在のプロシージャで有効になっていたエラー ハンドラーを無効にし、`Nothing` にリセットされます。|  
|`GoTo` \-1|現在のプロシージャで有効になっていた例外を無効にし、`Nothing` にリセットされます。|  
|`Resume Next`|ランタイム エラーが発生すると、エラーが発生したステートメントの直後のステートメントに制御が移り、そのステートメントから実行が継続されます。  オブジェクトにアクセスするときは、`On Error GoTo` ではなくこの形式を使用します。|  
  
## 解説  
  
> [!NOTE]
>  ここでは構造化されていない例外処理とステートメントの `On Error` を使用するよりも構造化例外処理を使用することをお勧めします。  詳細については、「[Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」を参照してください。  
  
 "有効な" エラー ハンドラーとは、`On Error` ステートメントによって有効化されているものを指します。  "アクティブな" エラー ハンドラーとは、エラー処理を行っている最中の有効なハンドラーのことを指します。  
  
 エラー ハンドラーがアクティブな間 \(エラーの発生から、`Resume`、`Exit Sub`、`Exit Function`、または `Exit Property` の各ステートメントまで\) にエラーが発生した場合は、現在のプロシージャのエラー ハンドラーはエラーを処理できません。  制御は呼び出しプロシージャに戻ります。  
  
 呼び出しプロシージャに有効なエラー ハンドラーがある場合は、そのハンドラーがアクティブになり、エラーを処理します。  呼び出しプロシージャのエラー ハンドラーもアクティブである場合は、有効であってもアクティブではないエラー ハンドラーが見つかるまで、元の呼び出しプロシージャに制御が順次戻されます。  有効であってもアクティブではないエラー ハンドラーが見つからない場合は、実際にエラーが起こった位置で致命的なエラーが発生します。  
  
 エラー ハンドラーが呼び出しプロシージャに制御を戻すたびに、そのプロシージャが現在のプロシージャになります。  いずれかのプロシージャのエラー ハンドラーによってエラーが処理された後は、`Resume`ステートメントで指定された位置から現在のプロシージャの実行が再開されます。  
  
> [!NOTE]
>  エラー処理ルーチンは、`Sub` プロシージャまたは `Function` プロシージャではありません。  行ラベルまたは行番号でマークされたコードのセクションです。  
  
## Number プロパティ  
 エラー処理ルーチンは、`Err` オブジェクトの `Number` プロパティの値に基づいて、エラーの原因を判断します。  このルーチンでは、他のエラーが発生する前、またはエラーを引き起こす可能性のあるプロシージャが呼び出される前に、`Err` オブジェクトの関連するプロパティ値をテストまたは保存する必要があります。  `Err` オブジェクトのプロパティ値には、直前に発生したエラーが反映されます。  `Err.Number` に関連付けられているエラー メッセージは `Err.Description` に格納されます。  
  
## Throw ステートメント  
 `Err.Raise` メソッドによってエラーを発生させたときは、`Exception` プロパティが <xref:System.Exception> クラスの新しいインスタンスに設定されます。  派生した例外型の例外を発生させるには、`Throw` ステートメントを使用します。  **Throw** ステートメントは、スローする例外インスタンスを指定する 1 つのパラメーターを持っています。  これらの機能を既存の例外処理サポートで使用する方法を次に示します。  
  
 [!code-vb[VbVbalrErrorHandling#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_1.vb)]  
  
 `On Error GoTo` ステートメントは、例外クラスに関係なく、すべてのエラーをトラップするという点に注意してください。  
  
## On Error Resume Next  
 `On Error Resume Next` ステートメントは、ランタイム エラーを発生させたステートメントの直後にあるステートメント、または、`On Error Resume Next` ステートメントが入っているプロシージャから最後に呼び出しを行ったステートメントの直後のステートメントを使用して、実行を継続させます。  これにより、ランタイム エラーが発生しても処理を続けることができます。  プロシージャ内の別の場所に制御を移さなくても、エラー処理ルーチンをエラーが発生する可能性がある場所に配置できます。  `On Error Resume Next` ステートメントは、別のプロシージャが呼び出されると非アクティブになるため、実行時にインライン エラー処理が必要な場合は、呼び出しルーチンごとに `On Error Resume Next` ステートメントを実行する必要があります。  
  
> [!NOTE]
>  他のオブジェクトへのアクセス中に生成されたエラーを処理する場合は、`On Error GoTo` よりも `On Error Resume Next` 構成要素の方が適しています。  オブジェクトと対話した後に毎回 `Err` を調べれば、そのコードがどのオブジェクトにアクセスしたかが明らかになります。  どのオブジェクトが `Err.Number` にエラー コードを設定したかと、どのオブジェクトが最初にエラーを生成したかについても確認できます \(このオブジェクトは `Err.Source` で指定されます\)。  
  
## On Error GoTo 0  
 `On Error GoTo 0` は、現在のプロシージャ内のエラー処理を無効にします。  このステートメントは、プロシージャに番号 0 の行があったとしても、その行をエラー処理コードの開始位置にするわけではありません。  `On Error GoTo 0` ステートメントを指定しなくても、エラー ハンドラーはプロシージャが終了すると自動的に無効になります。  
  
## On Error GoTo \-1  
 `On Error GoTo -1` は、現在のプロシージャ内の例外を無効にします。  このステートメントは、プロシージャに番号 \-1 の行があったとしても、その行をエラー処理コードの開始位置にするわけではありません。  `On Error GoTo -1` ステートメントを指定しなくても、例外はプロシージャが終了すると自動的に無効になります。  
  
 エラーが発生しないときにエラー処理コードが実行されないようにするには、次のコード例のように、エラー処理ルーチンの直前に `Exit Sub`、`Exit Function`、または `Exit Property` ステートメントを指定します。  
  
 [!code-vb[VbVbalrErrorHandling#18](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_2.vb)]  
  
 この例では、エラー処理コードが `Exit Sub` ステートメントに続く形で `End Sub` ステートメントよりも前に置かれ、プロシージャのフローからは分離されています。  エラー処理コードは、プロシージャ内の任意の場所に指定できます。  
  
## トラップされないエラー  
 オブジェクトを実行可能ファイルとして実行している場合、オブジェクト内のトラップされないエラーはコントローラー アプリケーションに戻されます。  開発環境では、トラップされないエラーがコントローラー アプリケーションに戻されるのは、適切なオプションが設定されている場合だけです。  デバッグ時に設定するオプションの説明、そのオプションの設定方法、およびホストがクラスを作成できるかどうかについては、ホスト アプリケーションのドキュメントを参照してください。  
  
 他のオブジェクトにアクセスするオブジェクトを作成する場合は、アクセス先のオブジェクトが戻す未処理のエラーを処理する必要があります。  このオブジェクト内でエラーを処理できない場合は、`Err.Number` 内のエラー コードをこのオブジェクトの独自のエラーのいずれかに割り当てて、もう 1 レベル上の呼び出し元に渡します。  独自のエラーを指定するには、独自のエラー コードを `VbObjectError` 定数に追加する必要があります。  たとえば、独自のエラー コードが 1052 の場合は、次のように割り当てます。  
  
 [!code-vb[VbVbalrErrorHandling#19](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_3.vb)]  
  
> [!CAUTION]
>  Windows ダイナミック リンク ライブラリ \(DLL: Dynamic Link Library\) の呼び出し中にシステム エラーが起こった場合は例外が発生しないため、Visual Basic エラー トラッピングではトラッピングされません。  DLL 関数を呼び出すときは、API の仕様に従ってそれぞれの戻り値を調べ、処理が正しく実行されたかどうかを確認する必要があります。エラーの場合には、`Err` オブジェクトの `LastDLLError` プロパティの値を調べます。  
  
## 使用例  
 この例では、`On Error GoTo` ステートメントを使用して、プロシージャ内のエラー処理ルーチンの場所を指定します。  ゼロによる除算が行われると、エラー番号 6 が生成されます。  このエラーがエラー処理ルーチンで処理された後、エラーが発生したステートメントに制御が戻ります。  `On Error GoTo 0` ステートメントはエラー トラッピングを無効にします。  その後で、`On Error Resume Next` ステートメントを使用してエラー トラッピングを遅延させ、次のステートメントによって生成されたエラーのコンテキストが確認できるようにします。  `Err.Clear` は、エラーを処理した後に `Err` オブジェクトのプロパティをクリアするために使用されます。  
  
 [!code-vb[VbVbalrErrorHandling#20](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_4.vb)]  
  
## 必要条件  
 **名前空間**: [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **アセンブリ**: Visual Basic ランタイム ライブラリ \(Microsoft.VisualBasic.dll 内\)  
  
## 参照  
 <xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.Number%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.Description%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>   
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Resume Statement](../../../visual-basic/language-reference/statements/resume-statement.md)   
 [Error Messages](../../../visual-basic/language-reference/error-messages/index.md)   
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)