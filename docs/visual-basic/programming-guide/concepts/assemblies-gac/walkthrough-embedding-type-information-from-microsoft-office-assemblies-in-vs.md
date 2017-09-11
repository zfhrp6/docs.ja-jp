---
title: "チュートリアル: Visual Studio (Visual Basic) で Microsoft Office アセンブリから型情報の埋め込み |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: c527941d6eae56d66cbede92ced3f66d24937354
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="c6d8e-102">チュートリアル: Visual Studio (Visual Basic) で Microsoft Office アセンブリから型情報の埋め込み</span><span class="sxs-lookup"><span data-stu-id="c6d8e-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="c6d8e-103">COM オブジェクトを参照するアプリケーションに型情報を埋め込むと、プライマリ相互運用機能アセンブリ (PIA: Primary Interop Assembly) を使用する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="c6d8e-104">また、埋め込み型情報を使用することで、バージョンに依存しないアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="c6d8e-105">つまり、複数のバージョンの COM ライブラリの型を使用するようにプログラムを記述でき、バージョンごとに固有の PIA が不要になります。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="c6d8e-106">この方法は、Microsoft Office ライブラリのオブジェクトを使用するアプリケーション向けの一般的なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="c6d8e-107">型情報を埋め込むと、プログラムの同じビルドで、異なるコンピューター上にある異なるバージョンの Microsoft Office と連携できます。Microsoft Office のバージョンごとにプログラムや PIA を再配置する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="c6d8e-108">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c6d8e-108">Prerequisites</span></span>  
 <span data-ttu-id="c6d8e-109">このチュートリアルの前提条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="c6d8e-110">Visual Studio や Microsoft Excel がインストールされているコンピューター。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="c6d8e-111">.NET Framework 4 以降およびさまざまなバージョンの Excel がインストールされている 2 つ目のコンピューターです。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <span data-ttu-id="c6d8e-112"><a name="BKMK_createapp"></a>Microsoft Office の複数のバージョンで動作するアプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="c6d8e-112"><a name="BKMK_createapp"></a> To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="c6d8e-113">Excel がインストールされているコンピューターでは、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="c6d8e-114">**[ファイル]** メニューで、 **[新規]**、 **[プロジェクト]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="c6d8e-115">**新しいプロジェクト**ダイアログ ボックスで、**プロジェクトの種類** ウィンドウで、ことを確認して**Windows**が選択されています。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="c6d8e-116">選択**コンソール アプリケーション**で、**テンプレート**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="c6d8e-117">**名**ボックスに、入力`CreateExcelWorkbook`を選択し、 **OK**  ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="c6d8e-118">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="c6d8e-119">CreateExcelWorkbook プロジェクトのショートカット メニューを開きを選択し、**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-119">Open the shortcut menu for the CreateExcelWorkbook project and then choose **Properties**.</span></span> <span data-ttu-id="c6d8e-120">選択、**参照** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-120">Choose the **References** tab.</span></span> <span data-ttu-id="c6d8e-121">**[追加]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-121">Choose the **Add** button.</span></span>  
  
5.  <span data-ttu-id="c6d8e-122">**.NET**  タブで、最新バージョンの選択`Microsoft.Office.Interop.Excel`します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-122">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="c6d8e-123">たとえば、 **Microsoft.Office.Interop.Excel 14.0.0.0**します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-123">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="c6d8e-124">**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-124">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="c6d8e-125">参照の一覧で、 **CreateExcelWorkbook**プロジェクトでの参照を選択`Microsoft.Office.Interop.Excel`前の手順で追加します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-125">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="c6d8e-126">**プロパティ**ウィンドウことを確認して、`Embed Interop Types`にプロパティが設定されている`True`します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-126">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c6d8e-127">このチュートリアルで作成したアプリケーションは、相互運用の型情報が埋め込まれているため、異なるバージョンの Microsoft Office と連携して動作します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-127">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="c6d8e-128">`Embed Interop Types` プロパティを `False` に設定した場合は、このアプリケーションと連携して動作する Microsoft Office のバージョンごとに PIA を組み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-128">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="c6d8e-129">Module1.vb ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-129">Open the Module1.vb file.</span></span> <span data-ttu-id="c6d8e-130">ファイルのコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-130">Replace the code in the file with the following code:</span></span>  
  
    ```vb  
    Imports Excel = Microsoft.Office.Interop.Excel  
  
    Module Module1  
  
        Sub Main()  
            Dim values = {4, 6, 18, 2, 1, 76, 0, 3, 11}  
  
            CreateWorkbook(values, "C:\SampleFolder\SampleWorkbook.xls")  
        End Sub  
  
        Sub CreateWorkbook(ByVal values As Integer(), ByVal filePath As String)  
            Dim excelApp As Excel.Application = Nothing  
            Dim wkbk As Excel.Workbook  
            Dim sheet As Excel.Worksheet  
  
            Try  
                ' Start Excel and create a workbook and worksheet.  
                excelApp = New Excel.Application  
                wkbk = excelApp.Workbooks.Add()  
                sheet = CType(wkbk.Sheets.Add(), Excel.Worksheet)  
                sheet.Name = "Sample Worksheet"  
  
                ' Write a column of values.  
                ' In the For loop, both the row index and array index start at 1.  
                ' Therefore the value of 4 at array index 0 is not included.  
                For i = 1 To values.Length - 1  
                    sheet.Cells(i, 1) = values(i)  
                Next  
  
                ' Suppress any alerts and save the file. Create the directory   
                ' if it does not exist. Overwrite the file if it exists.  
                excelApp.DisplayAlerts = False  
                Dim folderPath = My.Computer.FileSystem.GetParentPath(filePath)  
                If Not My.Computer.FileSystem.DirectoryExists(folderPath) Then  
                    My.Computer.FileSystem.CreateDirectory(folderPath)  
                End If  
                wkbk.SaveAs(filePath)  
        Catch  
  
            Finally  
                sheet = Nothing  
                wkbk = Nothing  
  
                ' Close Excel.  
                excelApp.Quit()  
                excelApp = Nothing  
            End Try  
  
        End Sub  
    End Module  
    ```  
  
8.  <span data-ttu-id="c6d8e-131">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-131">Save the project.</span></span>  
  
9. <span data-ttu-id="c6d8e-132">Ctrl キーを押しながら F5 キーを押して、プロジェクトをビルドおよび実行します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-132">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="c6d8e-133">プログラム例で指定した場所 (C:\SampleFolder\SampleWorkbook.xls) に Excel ブックが作成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-133">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <span data-ttu-id="c6d8e-134"><a name="BKMK_publishapp"></a>Microsoft Office の異なるバージョンがインストールされているコンピューターにアプリケーションを発行するには</span><span class="sxs-lookup"><span data-stu-id="c6d8e-134"><a name="BKMK_publishapp"></a> To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="c6d8e-135">Visual Studio では、このチュートリアルで作成したプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-135">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="c6d8e-136">**ビルド** メニューの 選択**createexcelworkbook の発行**します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-136">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="c6d8e-137">発行ウィザードの手順に従って、アプリケーションのインストール可能なバージョンを作成します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-137">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="c6d8e-138">詳細については、次を参照してください。[発行ウィザード (Visual Studio での Office 開発)](https://msdn.microsoft.com/library/bb625071)します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-138">For more information, see [Publish Wizard (Office Development in Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span></span>  
  
3.  <span data-ttu-id="c6d8e-139">.NET Framework 4 以降およびさまざまなバージョンの Excel がインストールされているコンピューターにアプリケーションをインストールします。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-139">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="c6d8e-140">インストールが完了したら、インストールしたプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-140">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="c6d8e-141">プログラム例で指定した場所 (C:\SampleFolder\SampleWorkbook.xls) に Excel ブックが作成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c6d8e-141">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6d8e-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6d8e-142">See Also</span></span>  
 <span data-ttu-id="c6d8e-143">[チュートリアル: Visual Studio (Visual Basic) でのマネージ アセンブリから型の埋め込み](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md) </span><span class="sxs-lookup"><span data-stu-id="c6d8e-143">[Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md) </span></span>  
<span data-ttu-id="c6d8e-144"> [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)</span><span class="sxs-lookup"><span data-stu-id="c6d8e-144"> [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)</span></span>

