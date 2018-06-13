---
title: On Error ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.OnError
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement [Visual Basic]
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement [Visual Basic], On Error
- control flow [Visual Basic], branching
- Error keyword [Visual Basic]
- execution [Visual Basic], conditional
- Resume statement [Visual Basic], and On Error statement
- Error statement [Visual Basic], and On Error statement
- GoTo statement [Visual Basic], and On Error statement
- branching [Visual Basic], on error
- conditional statements [Visual Basic], On Error
- On Error statement [Visual Basic], syntax
- On keyword [Visual Basic]
- run-time errors [Visual Basic], handling
- On Error statement [Visual Basic]
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
ms.openlocfilehash: b2e32dcca2e29a178af6dc985da536b47f0ebae6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605096"
---
# <a name="on-error-statement-visual-basic"></a>On Error ステートメント (Visual Basic)
エラー処理ルーチンを有効にし、プロシージャ内のルーチンの場所を指定しますエラー処理ルーチンを無効にも使用できます。  
  
 エラー処理せず、実行時に発生するは致命的なエラー: エラー メッセージが表示され、実行が停止します。  
  
 可能な限り、ことをお勧め非構造化例外処理を使用するのではなく、処理、コードの構造化例外を使用して、`On Error`ステートメントです。 詳しくは、「[Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」をご覧ください。  
  
> [!NOTE]
>  `Error`キーワードでも使用、 [Error ステートメント](../../../visual-basic/language-reference/statements/error-statement.md)、旧バージョンとの互換性のためサポートされています。  
  
## <a name="syntax"></a>構文  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`GoTo` `line`|要求で指定した行から開始するエラー処理ルーチンを有効に`line`引数。 `line`引数が任意の行ラベルまたは行番号。 実行時エラーが発生した場合は、エラー ハンドラーをアクティブにする際、指定した行に分岐を制御します。 指定した行と同じ手順である必要があります、`On Error`ステートメント、またはコンパイル時エラーが発生します。|  
|`GoTo` 0|現在のプロシージャで有効になっているエラー ハンドラーが無効になり、リセット`Nothing`です。|  
|`GoTo` -1|現在のプロシージャで有効になっている例外を無効にしをリセット`Nothing`です。|  
|`Resume Next`|実行時エラーが発生したときに、エラーが発生し、そのポイントから実行が継続ステートメントの直後のステートメントに制御が移動を指定します。 このフォームを使用してなく`On Error GoTo`オブジェクトにアクセスするときにします。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  非構造化例外処理を使用するのではなく、可能な限り、コードに構造化例外処理を使用することをお勧めおよび`On Error`ステートメントです。 詳しくは、「[Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」をご覧ください。  
  
 "Enabled"のエラー ハンドラーは 1 つで有効になっている、`On Error`ステートメントです。 "アクティブな"エラー ハンドラーは、有効になっているハンドラーのエラーの処理中であります。  
  
 エラー ハンドラーがアクティブな間にエラーが発生したかどうか (エラーの発生間と`Resume`、 `Exit Sub`、 `Exit Function`、または`Exit Property`ステートメント)、現在のプロシージャのエラー ハンドラーは、エラーを処理できません。 コントロールは、呼び出し元のプロシージャを返します。  
  
 呼び出し元のプロシージャに、有効なエラー ハンドラーがある場合、エラー処理でアクティブ化されます。 呼び出し元のプロシージャのエラー ハンドラーもアクティブである場合、有効であっても、非アクティブなエラー ハンドラーが見つかるまでに元の呼び出しプロシージャを介して返さ制御が渡されます。 このようなエラー ハンドラーが見つからない場合は、エラーが、実際に発生した時点で致命的です。  
  
 エラー ハンドラーは、呼び出し元のプロシージャにコントロールを通過するたびにそのプロシージャには、現在のプロシージャになります。 指定された位置から現在のプロシージャの実行が再開されるエラーは、すべてのプロシージャのエラー ハンドラーによって処理されたが後、`Resume`ステートメントです。  
  
> [!NOTE]
>  エラー処理ルーチンは、`Sub`プロシージャまたは`Function`プロシージャです。 これは、行ラベルまたは行番号でマークされたコードのセクションです。  
  
## <a name="number-property"></a>Number プロパティ  
 エラー処理ルーチンがの値を使用して、`Number`のプロパティ、`Err`エラーの原因を特定するオブジェクト。 ルーチンのテストまたはに関連するプロパティ値を保存する必要があります、`Err`他のエラーが発生する可能性がまたは、エラーが呼び出される可能性がある手順の前に、事前にします。 プロパティの値を`Err`オブジェクトは、最新のエラーのみを反映します。 エラー メッセージに関連付けられている`Err.Number`に含まれる`Err.Description`です。  
  
## <a name="throw-statement"></a>Throw ステートメント  
 発生したエラー、`Err.Raise`メソッドのセット、`Exception`プロパティの新しく作成されたインスタンスを<xref:System.Exception>クラスです。 派生した例外の種類の例外の発生をサポートするために、`Throw`ステートメントは、言語でサポートされています。 これは、スローされる例外のインスタンスである単一パラメーターを受け取ります。 次の例では、既存の例外処理のサポートでこれらの機能を使用する方法を示しています。  
  
 [!code-vb[VbVbalrErrorHandling#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_1.vb)]  
  
 注意して、`On Error GoTo`ステートメントは、例外クラスに関係なく、すべてのエラーをトラップします。  
  
## <a name="on-error-resume-next"></a>On Error Resume Next  
 `On Error Resume Next` 実行をすぐに実行時エラーの原因となったステートメントを次のステートメントから続行するか、最新直後のステートメントを含むプロシージャの外に呼び出し、`On Error Resume Next`ステートメントです。 このステートメントは、実行時エラーに関係なく、引き続き実行できます。 プロシージャ内の別の場所に制御を転送するのではなく、エラーが発生すると、エラー処理ルーチンを配置することができます。 `On Error Resume Next`ステートメントになり、非アクティブな別のプロシージャが呼び出されたときに実行する必要があります、`On Error Resume Next`インライン内でエラー処理ルーチンをする場合、各ステートメントがルーチンを呼び出すとします。  
  
> [!NOTE]
>  `On Error Resume Next`コンストラクトことをお勧めする`On Error GoTo`他のオブジェクトへのアクセス中にエラーを処理するときにします。 チェック`Err`オブジェクトと対話をコードによってアクセスされたオブジェクトがあいまいさを削除した後です。 確認するオブジェクトのエラー コードを配置する`Err.Number`、どのオブジェクトが最初に、エラーを生成および (で指定されたオブジェクト`Err.Source`)。  
  
## <a name="on-error-goto-0"></a>On Error GoTo 0  
 `On Error GoTo 0` 現在のプロシージャでのエラー処理を無効にします。 0 行目の手順には、番号 0 の行が含まれている場合でも、エラー処理コードの先頭として指定しません。 なし、`On Error GoTo 0`プロシージャが終了したときに、ステートメントでは、エラー ハンドラーが自動的に無効にします。  
  
## <a name="on-error-goto--1"></a>On Error GoTo-1  
 `On Error GoTo -1` 現在のプロシージャに、例外を無効にします。 指定しません行-1、エラー処理コードの先頭としてプロシージャには、-1 を番号の行が含まれている場合でもです。 なし、`On Error GoTo -1`プロシージャが終了したときに、ステートメントでは、例外が自動的に無効にします。  
  
 エラー処理コードのエラーが発生していないときに実行を回避するのには、配置、 `Exit Sub`、 `Exit Function`、または`Exit Property`直前に次のフラグメントのように、エラー処理ルーチン ステートメント。  
  
 [!code-vb[VbVbalrErrorHandling#18](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_2.vb)]  
  
 ここでは、エラー処理コードに依存、`Exit Sub`ステートメント続き、`End Sub`ステートメント、プロシージャのフローから分離します。 プロシージャで任意の場所エラー処理コードを配置することができます。  
  
## <a name="untrapped-errors"></a>エラーをトラップしません。  
 オブジェクトでトラップされないエラーは、オブジェクトが、実行可能ファイルとして実行されているときに、制御のアプリケーションに返されます。 開発環境内でエラーをトラップしないが、適切なオプションが設定されている場合にのみ、制御側のアプリケーションに返されます。 詳細についてはデバッグ中に設定、これらを設定する方法、およびホストがクラスを作成するかどうかをオプションにする、ホスト アプリケーションのマニュアルを参照してください。  
  
 その他のオブジェクトにアクセスするオブジェクトを作成する場合戻す未処理のエラーを処理しようとする必要があります。 場合はエラー コードをマップすることはできません、`Err.Number`独自のエラーとし、パスのいずれかには、オブジェクトの呼び出し元に戻します。 エラー コードを追加して、エラーを指定する必要があります、`VbObjectError`定数。 たとえば、独自のエラー コードが 1052 の場合は、それに割り当てます。  
  
 [!code-vb[VbVbalrErrorHandling#19](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_3.vb)]  
  
> [!CAUTION]
>  Windows ダイナミック リンク ライブラリ (Dll) への呼び出し中にシステム エラーは、例外を発生させません、Visual Basic エラー トラップをトラップすることはできません。 DLL 関数を呼び出すときにの成功または失敗 (、API 仕様に従って)、それぞれの戻り値をチェックする必要があります、障害発生時値を確認し、`Err`オブジェクトの`LastDLLError`プロパティです。  
  
## <a name="example"></a>例  
 この例を使用して、`On Error GoTo`ステートメント、プロシージャ内のエラー処理ルーチンの場所を指定します。 例では、0 で除算しようとするはエラー番号 6 を生成します。 エラー処理ルーチンで、エラーが処理され、エラーが発生したステートメントに制御が返されます。 `On Error GoTo 0`ステートメントがエラー トラップをオフにします。 続いて、`On Error Resume Next`エラー トラップできるように、次のステートメントによって生成されたエラーのコンテキストを特定の認識することができますを延期するステートメントを使用します。 なお`Err.Clear`をクリアするために使用、`Err`エラーが処理された後、オブジェクトのプロパティです。  
  
 [!code-vb[VbVbalrErrorHandling#20](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_4.vb)]  
  
## <a name="requirements"></a>要件  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **アセンブリ:** Visual Basic Runtime Library (Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Number%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Description%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>  
 [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)  
 [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Resume ステートメント](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [エラー メッセージ](../../../visual-basic/language-reference/error-messages/index.md)  
 [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
