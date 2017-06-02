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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4347ba0e740419b53a1aa662c43933dead107e9c
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a>チュートリアル: Visual Studio (Visual Basic) で Microsoft Office アセンブリから型情報の埋め込み
COM オブジェクトを参照するアプリケーションに型情報を埋め込むと、プライマリ相互運用機能アセンブリ (PIA: Primary Interop Assembly) を使用する必要がなくなります。 また、埋め込み型情報を使用することで、バージョンに依存しないアプリケーションを作成できます。 つまり、複数のバージョンの COM ライブラリの型を使用するようにプログラムを記述でき、バージョンごとに固有の PIA が不要になります。 この方法は、Microsoft Office ライブラリのオブジェクトを使用するアプリケーション向けの一般的なシナリオです。 型情報を埋め込むと、プログラムの同じビルドで、異なるコンピューター上にある異なるバージョンの Microsoft Office と連携できます。Microsoft Office のバージョンごとにプログラムや PIA を再配置する必要はありません。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルの前提条件は次のとおりです。  
  
-   Visual Studio や Microsoft Excel がインストールされているコンピューター。  
  
-   .NET Framework 4 以降およびさまざまなバージョンの Excel がインストールされている 2 つ目のコンピューターです。  
  
##  <a name="BKMK_createapp"></a>Microsoft Office の複数のバージョンで動作するアプリケーションを作成するには  
  
1.  Excel がインストールされているコンピューターでは、Visual Studio を起動します。  
  
2.  **[ファイル]** メニューで、 **[新規]**、 **[プロジェクト]**をクリックします。  
  
3.  **新しいプロジェクト**ダイアログ ボックスで、**プロジェクトの種類** ウィンドウで、ことを確認して**Windows**が選択されています。 選択**コンソール アプリケーション**で、**テンプレート**ウィンドウです。 **名**ボックスに、入力`CreateExcelWorkbook`を選択し、 **OK**  ボタンをクリックします。 新しいプロジェクトが作成されます。  
  
4.  CreateExcelWorkbook プロジェクトのショートカット メニューを開きを選択し、**プロパティ**します。 選択、**参照** タブをクリックします。 **[追加]** ボタンをクリックします。  
  
5.  **.NET**  タブで、最新バージョンの選択`Microsoft.Office.Interop.Excel`します。 たとえば、 **Microsoft.Office.Interop.Excel 14.0.0.0**します。 **[OK]** を選択します。  
  
6.  参照の一覧で、 **CreateExcelWorkbook**プロジェクトでの参照を選択`Microsoft.Office.Interop.Excel`前の手順で追加します。 **プロパティ**ウィンドウことを確認して、`Embed Interop Types`にプロパティが設定されている`True`します。  
  
    > [!NOTE]
    >  このチュートリアルで作成したアプリケーションは、相互運用の型情報が埋め込まれているため、異なるバージョンの Microsoft Office と連携して動作します。 `Embed Interop Types` プロパティを `False` に設定した場合は、このアプリケーションと連携して動作する Microsoft Office のバージョンごとに PIA を組み込む必要があります。  
  
7.  Module1.vb ファイルを開きます。 ファイルのコードを次のコードに置き換えます。  
  
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
  
8.  プロジェクトを保存します。  
  
9. Ctrl キーを押しながら F5 キーを押して、プロジェクトをビルドおよび実行します。 プログラム例で指定した場所 (C:\SampleFolder\SampleWorkbook.xls) に Excel ブックが作成されていることを確認します。  
  
##  <a name="BKMK_publishapp"></a>Microsoft Office の異なるバージョンがインストールされているコンピューターにアプリケーションを発行するには  
  
1.  Visual Studio では、このチュートリアルで作成したプロジェクトを開きます。  
  
2.  **ビルド** メニューの 選択**createexcelworkbook の発行**します。 発行ウィザードの手順に従って、アプリケーションのインストール可能なバージョンを作成します。 詳細については、次を参照してください。[発行ウィザード (Visual Studio での Office 開発)](https://msdn.microsoft.com/library/bb625071)します。  
  
3.  .NET Framework 4 以降およびさまざまなバージョンの Excel がインストールされているコンピューターにアプリケーションをインストールします。  
  
4.  インストールが完了したら、インストールしたプログラムを実行します。  
  
5.  プログラム例で指定した場所 (C:\SampleFolder\SampleWorkbook.xls) に Excel ブックが作成されていることを確認します。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: Visual Studio (Visual Basic) でのマネージ アセンブリから型の埋め込み](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)   
 [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)

