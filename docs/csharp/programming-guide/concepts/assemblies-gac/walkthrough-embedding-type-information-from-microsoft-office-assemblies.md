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
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a>チュートリアル: Visual Studio で Microsoft Office アセンブリからの型情報を埋め込む (C#)
COM オブジェクトを参照するアプリケーションに型情報を埋め込むと、プライマリ相互運用機能アセンブリ (PIA: Primary Interop Assembly) を使用する必要がなくなります。 また、埋め込み型情報を使用することで、バージョンに依存しないアプリケーションを作成できます。 つまり、複数のバージョンの COM ライブラリの型を使用するようにプログラムを記述でき、バージョンごとに固有の PIA が不要になります。 この方法は、Microsoft Office ライブラリのオブジェクトを使用するアプリケーション向けの一般的なシナリオです。 型情報を埋め込むと、プログラムの同じビルドで、異なるコンピューター上にある異なるバージョンの Microsoft Office と連携できます。Microsoft Office のバージョンごとにプログラムや PIA を再配置する必要はありません。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルの前提条件は次のとおりです。  
  
-   Visual Studio および Microsoft Excel がインストールされたコンピューター。  
  
-   .NET Framework 4 以上および別のバージョンの Excel がインストールされた 2 台目のコンピューター。  
  
##  <a name="BKMK_createapp"></a> 複数のバージョンの Microsoft Office と連携するアプリケーションを作成するには  
  
1.  Excel がインストールされているコンピューターで Visual Studio を起動します。  
  
2.  **[ファイル]** メニューで、 **[新規]**、 **[プロジェクト]** をクリックします。  
  
3.  **[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、**[Windows]** が選択されていることを確認します。 **[テンプレート]** ペインの **[コンソール アプリケーション]** を選択します。 **[名前]** ボックスに「`CreateExcelWorkbook`」と入力して、 **[OK]** を選択します。 新しいプロジェクトが作成されます。  
  
4.  **[ソリューション エクスプローラー]** で、**[参照]** フォルダーのショートカット メニューを開き、**[参照の追加]** をクリックします。  
  
5.  **[.NET]** タブで、最新バージョンの `Microsoft.Office.Interop.Excel` を選択します。 たとえば、**[Microsoft.Office.Interop.Excel 14.0.0.0]** をクリックします。 **[OK]** を選択します。  
  
6.  **CreateExcelWorkbook** プロジェクトの参照の一覧で、前の手順で追加した `Microsoft.Office.Interop.Excel` の参照を選択します。 **[プロパティ]** ウィンドウで、`Embed Interop Types` プロパティが `True` に設定されていることを確認します。  
  
    > [!NOTE]
    >  このチュートリアルで作成したアプリケーションは、相互運用の型情報が埋め込まれているため、異なるバージョンの Microsoft Office と連携して動作します。 `Embed Interop Types` プロパティを `False` に設定した場合は、このアプリケーションと連携して動作する Microsoft Office のバージョンごとに PIA を組み込む必要があります。  
  
7.  **Program.cs** ファイルを開きます。 ファイル内のコードを次のコードに置き換えます。  
  
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
  
8.  プロジェクトを保存します。  
  
9. Ctrl キーを押しながら F5 キーを押して、プロジェクトをビルドおよび実行します。 プログラム例で指定した場所 (C:\SampleFolder\SampleWorkbook.xls) に Excel ブックが作成されていることを確認します。  
  
##  <a name="BKMK_publishapp"></a> 別のバージョンの Microsoft Office がインストールされているコンピューターにアプリケーションを発行するには  
  
1.  Visual Studio で、このチュートリアルで作成したプロジェクトを開きます。  
  
2.  **[ビルド]** メニューで、**[CreateExcelWorkbook の発行]** をクリックします。 発行ウィザードの手順に従って、アプリケーションのインストール可能なバージョンを作成します。 詳しくは、「[発行ウィザード (Visual Studio での Office 開発)](https://msdn.microsoft.com/library/bb625071)」をご覧ください。  
  
3.  .NET Framework 4 以上および別のバージョンの Excel がインストールされているコンピューターに、アプリケーションをインストールします。  
  
4.  インストールが完了したら、インストールしたプログラムを実行します。  
  
5.  プログラム例で指定した場所 (C:\SampleFolder\SampleWorkbook.xls) に Excel ブックが作成されていることを確認します。  
  
## <a name="see-also"></a>参照  
 [チュートリアル: Visual Studio でマネージ アセンブリからの型を埋め込む (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [/link (C# コンパイラ オプション)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
