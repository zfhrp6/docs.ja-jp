---
title: "Visual Basic の Main プロシージャ"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90550ce3e62e4afbc94e2d383fa73db7178633d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="2994c-102">Visual Basic の Main プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2994c-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="2994c-103">すべての Visual Basic アプリケーションが呼び出されるプロシージャを含める必要があります`Main`です。</span><span class="sxs-lookup"><span data-stu-id="2994c-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="2994c-104">このプロシージャは、開始ポイントし、アプリケーションの総合的な制御します。</span><span class="sxs-lookup"><span data-stu-id="2994c-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="2994c-105">.NET Framework の呼び出し、`Main`プロシージャ、アプリケーションが読み込まれたし、制御を渡す準備ができました。</span><span class="sxs-lookup"><span data-stu-id="2994c-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="2994c-106">記述する必要があります、Windows フォーム アプリケーションを作成する場合は、しない限り、`Main`が自分で実行されるアプリケーションのプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="2994c-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>  
  
 <span data-ttu-id="2994c-107">`Main`最初に実行するコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2994c-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="2994c-108">`Main`プログラムの開始時に最初に読み込まれる形式を決定、アプリケーションのコピーがシステムで既に実行されているかどうかを調べる、アプリケーションの変数のセットを確立またはアプリケーションに必要なデータベースを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="2994c-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>  
  
## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="2994c-109">メインのプロシージャの要件</span><span class="sxs-lookup"><span data-stu-id="2994c-109">Requirements for the Main Procedure</span></span>  
 <span data-ttu-id="2994c-110">(通常は拡張子が .exe) で自身で実行されるファイルを含める必要があります、`Main`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="2994c-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="2994c-111">(たとえば、拡張子は .dll) ライブラリで稼働していない、独自としないため、`Main`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="2994c-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="2994c-112">作成することができます、さまざまな種類のプロジェクトの要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2994c-112">The requirements for the different types of projects you can create are as follows:</span></span>  
  
-   <span data-ttu-id="2994c-113">コンソール アプリケーションは単独で実行、および少なくとも 1 つを指定する必要があります`Main`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="2994c-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span> <span data-ttu-id="2994c-114">」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2994c-114">.</span></span>  
  
-   <span data-ttu-id="2994c-115">Windows フォーム アプリケーションは単独で実行します。</span><span class="sxs-lookup"><span data-stu-id="2994c-115">Windows Forms applications run on their own.</span></span> <span data-ttu-id="2994c-116">ただし、Visual Basic コンパイラに自動的に生成、`Main`などの手順と、アプリケーションをする必要はありません 1 つ作成します。</span><span class="sxs-lookup"><span data-stu-id="2994c-116">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>  
  
-   <span data-ttu-id="2994c-117">クラス ライブラリが不要な`Main`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="2994c-117">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="2994c-118">これらには、Windows コントロール ライブラリと Web コントロール ライブラリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2994c-118">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="2994c-119">Web アプリケーションは、クラス ライブラリとして配置されます。</span><span class="sxs-lookup"><span data-stu-id="2994c-119">Web applications are deployed as class libraries.</span></span>  
  
## <a name="declaring-the-main-procedure"></a><span data-ttu-id="2994c-120">メインのプロシージャを宣言します。</span><span class="sxs-lookup"><span data-stu-id="2994c-120">Declaring the Main Procedure</span></span>  
 <span data-ttu-id="2994c-121">宣言する方法を次の 4 つが、`Main`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="2994c-121">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="2994c-122">引数を受け取るものかどうか、値を返すこと.</span><span class="sxs-lookup"><span data-stu-id="2994c-122">It can take arguments or not, and it can return a value or not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2994c-123">宣言する場合`Main`クラスでは、使用する必要があります、`Shared`キーワード。</span><span class="sxs-lookup"><span data-stu-id="2994c-123">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="2994c-124">モジュールで`Main`する必要はありません`Shared`です。</span><span class="sxs-lookup"><span data-stu-id="2994c-124">In a module, `Main` does not need to be `Shared`.</span></span>  
  
-   <span data-ttu-id="2994c-125">最も簡単な方法は、宣言、`Sub`プロシージャがない引数または戻り値です。</span><span class="sxs-lookup"><span data-stu-id="2994c-125">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   <span data-ttu-id="2994c-126">`Main`返すことも、`Integer`値で、プログラムの終了コードとしてオペレーティング システムを使用します。</span><span class="sxs-lookup"><span data-stu-id="2994c-126">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="2994c-127">その他のプログラムは、Windows ERRORLEVEL 値を確認するには、このコードをテストできます。</span><span class="sxs-lookup"><span data-stu-id="2994c-127">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="2994c-128">宣言する必要があります、終了コードを返す`Main`として、`Function`プロシージャの代わりに、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="2994c-128">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>  
  
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
  
-   <span data-ttu-id="2994c-129">`Main`とることも、`String`引数として配列します。</span><span class="sxs-lookup"><span data-stu-id="2994c-129">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="2994c-130">配列内の各文字列には、プログラムの実行に使用したコマンドライン引数のいずれかが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2994c-130">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="2994c-131">その値に応じて異なるアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="2994c-131">You can take different actions depending on their values.</span></span>  
  
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
  
-   <span data-ttu-id="2994c-132">宣言することができます`Main`にコマンドライン引数を調べてが次のように、終了コードが返されません。</span><span class="sxs-lookup"><span data-stu-id="2994c-132">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2994c-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="2994c-133">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
 <xref:System.Array.Length%2A>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [<span data-ttu-id="2994c-134">Visual Basic プログラムの構造</span><span class="sxs-lookup"><span data-stu-id="2994c-134">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="2994c-135">NIB: Visual Basic バージョンの Hello World</span><span class="sxs-lookup"><span data-stu-id="2994c-135">NIB: Visual Basic Version of Hello, World</span></span>](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)  
 [<span data-ttu-id="2994c-136">/main</span><span class="sxs-lookup"><span data-stu-id="2994c-136">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)  
 [<span data-ttu-id="2994c-137">Shared</span><span class="sxs-lookup"><span data-stu-id="2994c-137">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="2994c-138">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="2994c-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="2994c-139">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="2994c-139">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="2994c-140">整数データ型</span><span class="sxs-lookup"><span data-stu-id="2994c-140">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="2994c-141">String データ型</span><span class="sxs-lookup"><span data-stu-id="2994c-141">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
