---
title: "Main Procedure in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Main"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Main procedure"
  - "Main method [Visual Basic]"
  - "main function"
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Main Procedure in Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

すべての Visual Basic アプリケーションには、`Main` という名前のプロシージャが含まれている必要があります。  このプロシージャは、アプリケーションの開始点となり、アプリケーションの総合的な制御を行います。  .NET Framework は、アプリケーションをロードして、アプリケーションに制御を渡せる状態になると、`Main` プロシージャを呼び出します。  Windows フォーム アプリケーションを作成する場合以外は、アプリケーションのエントリ ポイントとなる `Main` プロシージャを作成する必要があります。  
  
 `Main` には、最初に実行するコードを記述します。  `Main` では、プログラムの起動時に最初に読み込まれるフォームを決定したり、同一アプリケーションが既にシステム上で稼動しているかどうかを調べたり、アプリケーションで使用する一連の変数を作成したり、アプリケーションで必要なデータベースを開いたりできます。  
  
## Main プロシージャの要件  
 単独で実行されるファイル \(通常は拡張子 .exe を持つ\) には、`Main` プロシージャを含める必要があります。  ライブラリ \(拡張子 .dll を持つものなど\) は単独では実行されないので、`Main` プロシージャは必要ありません。  各種のプロジェクトについての要件を次に示します。  
  
-   コンソール アプリケーションは単独で実行されるので、少なくとも 1 つの `Main` プロシージャを記述する必要があります。  .  
  
-   Windows フォーム アプリケーションは単独で実行されます。  しかし、このようなアプリケーションでは Visual Basic コンパイラが自動的に `Main` プロシージャを生成するので、独自に記述する必要はありません。  
  
-   クラス ライブラリには `Main` プロシージャは必要ありません。  これには Windows コントロール ライブラリと Web コントロール ライブラリが含まれます。  Web アプリケーションはクラス ライブラリとして配置されます。  
  
## Main プロシージャの宣言  
 `Main` プロシージャを宣言するには 4 種類の方法があります。  引数を受け取るものと受け取らないもの、値を返すものと返さないものです。  
  
> [!NOTE]
>  クラス内で `Main` プロシージャを宣言する場合は、`Shared` キーワードを使用する必要があります。  モジュールで `Main` プロシージャを宣言する場合、`Shared` キーワードは不要です。  
  
-   最も単純な方法は、引数を受け取らず、値を返さない `Sub` プロシージャとして宣言することです。  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   また、`Main` プロシージャは `Integer` 値を返すことができます。オペレーティング システムは、この値をプログラムの終了コードとして使用します。  他のプログラムは、Windows ERRORLEVEL 値を確認することで、このコードをテストできます。  終了コードを返すには、`Main` を `Sub` プロシージャではなく `Function` プロシージャとして宣言する必要があります。  
  
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
  
-   `Main` は、引数として `String` 配列を受け取ることができます。  配列内の各文字列には、プログラムの実行に使用するコマンド ライン引数の 1 つが含まれます。  これらの値に応じて、異なる動作を実行できます。  
  
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
  
-   コマンド ライン引数を受け取り、終了コードを返さない場合は、`Main` を次のように宣言します。  
  
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
  
## 参照  
 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>   
 <xref:System.Array.Length%2A>   
 <xref:Microsoft.VisualBasic.Information.UBound%2A>   
 [Structure of a Visual Basic Program](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)   
 [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/ja-jp/9d030b60-e148-4366-a462-69532f02294c)   
 [\/main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md)