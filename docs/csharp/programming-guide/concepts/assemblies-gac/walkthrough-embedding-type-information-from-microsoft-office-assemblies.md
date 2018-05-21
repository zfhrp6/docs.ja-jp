---
title: 'チュートリアル: Visual Studio で Microsoft Office アセンブリからの型情報を埋め込む (C#)'
ms.date: 07/20/2015
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
ms.openlocfilehash: 8e7eb5c797ca87f87950d530112ec64f1327ae0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a><span data-ttu-id="535e4-102">チュートリアル: Visual Studio で Microsoft Office アセンブリからの型情報を埋め込む (C#)</span><span class="sxs-lookup"><span data-stu-id="535e4-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="535e4-103">COM オブジェクトを参照するアプリケーションに型情報を埋め込むと、プライマリ相互運用機能アセンブリ (PIA: Primary Interop Assembly) を使用する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="535e4-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="535e4-104">また、埋め込み型情報を使用することで、バージョンに依存しないアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="535e4-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="535e4-105">つまり、複数のバージョンの COM ライブラリの型を使用するようにプログラムを記述でき、バージョンごとに固有の PIA が不要になります。</span><span class="sxs-lookup"><span data-stu-id="535e4-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="535e4-106">この方法は、Microsoft Office ライブラリのオブジェクトを使用するアプリケーション向けの一般的なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="535e4-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="535e4-107">型情報を埋め込むと、プログラムの同じビルドで、異なるコンピューター上にある異なるバージョンの Microsoft Office と連携できます。Microsoft Office のバージョンごとにプログラムや PIA を再配置する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="535e4-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="535e4-108">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="535e4-108">Prerequisites</span></span>  
 <span data-ttu-id="535e4-109">このチュートリアルの前提条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="535e4-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="535e4-110">Visual Studio および Microsoft Excel がインストールされたコンピューター。</span><span class="sxs-lookup"><span data-stu-id="535e4-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="535e4-111">.NET Framework 4 以上および別のバージョンの Excel がインストールされた 2 台目のコンピューター。</span><span class="sxs-lookup"><span data-stu-id="535e4-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <a name="BKMK_createapp"></a> <span data-ttu-id="535e4-112">複数のバージョンの Microsoft Office と連携するアプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="535e4-112">To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="535e4-113">Excel がインストールされているコンピューターで Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="535e4-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="535e4-114">**[ファイル]** メニューで、 **[新規]**、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="535e4-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="535e4-115">**[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、**[Windows]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="535e4-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="535e4-116">**[テンプレート]** ペインの **[コンソール アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="535e4-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="535e4-117">**[名前]** ボックスに「`CreateExcelWorkbook`」と入力して、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="535e4-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="535e4-118">新しいプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="535e4-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="535e4-119">**[ソリューション エクスプローラー]** で、**[参照]** フォルダーのショートカット メニューを開き、**[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="535e4-119">In **Solution Explorer**, open the shortcut menu for the **References** folder and then choose **Add Reference**.</span></span>  
  
5.  <span data-ttu-id="535e4-120">**[.NET]** タブで、最新バージョンの `Microsoft.Office.Interop.Excel` を選択します。</span><span class="sxs-lookup"><span data-stu-id="535e4-120">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="535e4-121">たとえば、**[Microsoft.Office.Interop.Excel 14.0.0.0]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="535e4-121">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="535e4-122">**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="535e4-122">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="535e4-123">**CreateExcelWorkbook** プロジェクトの参照の一覧で、前の手順で追加した `Microsoft.Office.Interop.Excel` の参照を選択します。</span><span class="sxs-lookup"><span data-stu-id="535e4-123">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="535e4-124">**[プロパティ]** ウィンドウで、`Embed Interop Types` プロパティが `True` に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="535e4-124">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="535e4-125">このチュートリアルで作成したアプリケーションは、相互運用の型情報が埋め込まれているため、異なるバージョンの Microsoft Office と連携して動作します。</span><span class="sxs-lookup"><span data-stu-id="535e4-125">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="535e4-126">`Embed Interop Types` プロパティを `False` に設定した場合は、このアプリケーションと連携して動作する Microsoft Office のバージョンごとに PIA を組み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="535e4-126">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="535e4-127">**Program.cs** ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="535e4-127">Open the **Program.cs** file.</span></span> <span data-ttu-id="535e4-128">ファイル内のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="535e4-128">Replace the code in the file with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.IO;  
    using Excel = Microsoft.Office.Interop.Excel;  
  
    namespace CreateExcelWorkbook  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                int[] values = {4, 6, 18, 2, 1, 76, 0, 3, 11};  
  
                CreateWorkbook(values, @"C:\SampleFolder\SampleWorkbook.xls");  
            }  
  
            static void CreateWorkbook(int[] values, string filePath)  
            {  
                Excel.Application excelApp = null;  
                Excel.Workbook wkbk;  
                Excel.Worksheet sheet;  
  
                try  
                {  
                        // Start Excel and create a workbook and worksheet.  
                        excelApp = new Excel.Application();  
                        wkbk = excelApp.Workbooks.Add();  
                        sheet = wkbk.Sheets.Add() as Excel.Worksheet;  
                        sheet.Name = "Sample Worksheet";  
  
                        // Write a column of values.  
                        // In the For loop, both the row index and array index start at 1.  
                        // Therefore the value of 4 at array index 0 is not included.  
                        for (int i = 1; i < values.Length; i++)  
                        {  
                            sheet.Cells[i, 1] = values[i];  
                        }  
  
                        // Suppress any alerts and save the file. Create the directory   
                        // if it does not exist. Overwrite the file if it exists.  
                        excelApp.DisplayAlerts = false;  
                        string folderPath = Path.GetDirectoryName(filePath);  
                        if (!Directory.Exists(folderPath))  
                        {  
                            Directory.CreateDirectory(folderPath);  
                        }  
                        wkbk.SaveAs(filePath);  
                }  
                catch  
                {  
                }  
                finally  
                {  
                    sheet = null;  
                    wkbk = null;  
  
                    // Close Excel.  
                    excelApp.Quit();  
                    excelApp = null;  
                }  
            }  
        }  
    }  
    ```  
  
8.  <span data-ttu-id="535e4-129">プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="535e4-129">Save the project.</span></span>  
  
9. <span data-ttu-id="535e4-130">Ctrl キーを押しながら F5 キーを押して、プロジェクトをビルドおよび実行します。</span><span class="sxs-lookup"><span data-stu-id="535e4-130">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="535e4-131">プログラム例で指定した場所 (C:\SampleFolder\SampleWorkbook.xls) に Excel ブックが作成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="535e4-131">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <a name="BKMK_publishapp"></a> <span data-ttu-id="535e4-132">別のバージョンの Microsoft Office がインストールされているコンピューターにアプリケーションを発行するには</span><span class="sxs-lookup"><span data-stu-id="535e4-132">To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="535e4-133">Visual Studio で、このチュートリアルで作成したプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="535e4-133">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="535e4-134">**[ビルド]** メニューで、**[CreateExcelWorkbook の発行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="535e4-134">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="535e4-135">発行ウィザードの手順に従って、アプリケーションのインストール可能なバージョンを作成します。</span><span class="sxs-lookup"><span data-stu-id="535e4-135">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="535e4-136">詳しくは、「[発行ウィザード (Visual Studio での Office 開発)](https://msdn.microsoft.com/library/bb625071)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="535e4-136">For more information, see [Publish Wizard (Office Development in Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span></span>  
  
3.  <span data-ttu-id="535e4-137">.NET Framework 4 以上および別のバージョンの Excel がインストールされているコンピューターに、アプリケーションをインストールします。</span><span class="sxs-lookup"><span data-stu-id="535e4-137">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="535e4-138">インストールが完了したら、インストールしたプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="535e4-138">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="535e4-139">プログラム例で指定した場所 (C:\SampleFolder\SampleWorkbook.xls) に Excel ブックが作成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="535e4-139">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="535e4-140">参照</span><span class="sxs-lookup"><span data-stu-id="535e4-140">See Also</span></span>  
 [<span data-ttu-id="535e4-141">チュートリアル: Visual Studio でマネージ アセンブリからの型を埋め込む (C#)</span><span class="sxs-lookup"><span data-stu-id="535e4-141">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [<span data-ttu-id="535e4-142">/link (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="535e4-142">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
