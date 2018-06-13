---
title: Visual Basic の Main プロシージャ
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: 109bf94eb91292cfca700a9e456c8ab53e83d68f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652153"
---
# <a name="main-procedure-in-visual-basic"></a>Visual Basic の Main プロシージャ
すべての Visual Basic アプリケーションが呼び出されるプロシージャを含める必要があります`Main`です。 このプロシージャは、開始ポイントし、アプリケーションの総合的な制御します。 .NET Framework の呼び出し、`Main`プロシージャ、アプリケーションが読み込まれたし、制御を渡す準備ができました。 記述する必要があります、Windows フォーム アプリケーションを作成する場合は、しない限り、`Main`が自分で実行されるアプリケーションのプロシージャです。  
  
 `Main` 最初に実行するコードが含まれています。 `Main`プログラムの開始時に最初に読み込まれる形式を決定、アプリケーションのコピーがシステムで既に実行されているかどうかを調べる、アプリケーションの変数のセットを確立またはアプリケーションに必要なデータベースを開くことができます。  
  
## <a name="requirements-for-the-main-procedure"></a>メインのプロシージャの要件  
 (通常は拡張子が .exe) で自身で実行されるファイルを含める必要があります、`Main`プロシージャです。 (たとえば、拡張子は .dll) ライブラリで稼働していない、独自としないため、`Main`プロシージャです。 作成することができます、さまざまな種類のプロジェクトの要件は次のとおりです。  
  
-   コンソール アプリケーションは単独で実行、および少なくとも 1 つを指定する必要があります`Main`プロシージャです。 である必要があります。  
  
-   Windows フォーム アプリケーションは単独で実行します。 ただし、Visual Basic コンパイラに自動的に生成、`Main`などの手順と、アプリケーションをする必要はありません 1 つ作成します。  
  
-   クラス ライブラリが不要な`Main`プロシージャです。 これらには、Windows コントロール ライブラリと Web コントロール ライブラリが含まれます。 Web アプリケーションは、クラス ライブラリとして配置されます。  
  
## <a name="declaring-the-main-procedure"></a>メインのプロシージャを宣言します。  
 宣言する方法を次の 4 つが、`Main`プロシージャです。 引数を受け取るものかどうか、値を返すこと.  
  
> [!NOTE]
>  宣言する場合`Main`クラスでは、使用する必要があります、`Shared`キーワード。 モジュールで`Main`する必要はありません`Shared`です。  
  
-   最も簡単な方法は、宣言、`Sub`プロシージャがない引数または戻り値です。  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   `Main` 返すことも、`Integer`値で、プログラムの終了コードとしてオペレーティング システムを使用します。 その他のプログラムは、Windows ERRORLEVEL 値を確認するには、このコードをテストできます。 宣言する必要があります、終了コードを返す`Main`として、`Function`プロシージャの代わりに、`Sub`プロシージャです。  
  
    ```  
    Module mainModule  
        Function Main() As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   `Main` とることも、`String`引数として配列します。 配列内の各文字列には、プログラムの実行に使用したコマンドライン引数のいずれかが含まれています。 その値に応じて異なるアクションを実行できます。  
  
    ```  
    Module mainModule  
        Function Main(ByVal cmdArgs() As String) As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   宣言することができます`Main`にコマンドライン引数を調べてが次のように、終了コードが返されません。  
  
    ```  
    Module mainModule  
        Sub Main(ByVal cmdArgs() As String)  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
 <xref:System.Array.Length%2A>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [Visual Basic プログラムの構造](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [/main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
 [整数データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [String データ型](../../../visual-basic/language-reference/data-types/string-data-type.md)
