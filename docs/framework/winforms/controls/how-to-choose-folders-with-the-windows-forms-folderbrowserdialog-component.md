---
title: "方法 : Windows フォーム FolderBrowserDialog コンポーネントを使用してフォルダーを選択する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ディレクトリ [Windows フォーム], 選択"
  - "ディレクトリ [Windows フォーム], 選択"
  - "FolderBrowserDialog コンポーネント [Windows フォーム], 選択 (ディレクトリを)"
  - "フォルダー [Windows フォーム], 選択"
  - "フォルダー [Windows フォーム], 選択"
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : Windows フォーム FolderBrowserDialog コンポーネントを使用してフォルダーを選択する
Windows アプリケーションでは、ユーザーにフォルダーの選択を求めることがよくあります。最も一般的なのは、ファイルを保存する場合です。  Windows フォームの <xref:System.Windows.Forms.FolderBrowserDialog> コンポーネントを使用すると、この処理を簡単に実現できます。  
  
### FolderBrowserDialog コンポーネントでフォルダーを選択するには  
  
1.  プロシージャで、<xref:System.Windows.Forms.FolderBrowserDialog> コンポーネントの <xref:System.Windows.Forms.Form.DialogResult%2A> プロパティを参照して、ダイアログ ボックスがどのように閉じられたかを確認し、<xref:System.Windows.Forms.FolderBrowserDialog> コンポーネントの <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> プロパティの値を取得します。  
  
2.  ダイアログ ボックスのツリー ビューに表示される最上位のフォルダーを設定する必要がある場合は、<xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> プロパティを設定します。このプロパティには、[SpecialFolder](frlrfSystemEnvironmentSpecialFolderClassTopic) 列挙型のメンバーを指定します。  
  
3.  さらに、フォルダー ブラウザーのツリー ビューの上部に表示されるテキスト文字列を指定する <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> プロパティを設定できます。  
  
     <xref:System.Windows.Forms.FolderBrowserDialog> コンポーネントを使用してフォルダーを選択する方法を次に示します。この方法は、Visual Studio でのプロジェクトの作成時にプロジェクトの保存先フォルダーを選択する方法と同様です。  この例では、フォームの <xref:System.Windows.Forms.TextBox> コントロールにフォルダー名が表示されます。  エラーやその他の問題が発生したときにユーザーが選択内容を編集できるように、<xref:System.Windows.Forms.TextBox> コントロールなどの編集可能な領域にフォルダー名を表示することをお勧めします。  この例では、フォームに <xref:System.Windows.Forms.FolderBrowserDialog> コンポーネントと <xref:System.Windows.Forms.TextBox> コントロールがあると仮定しています。  
  
    ```vb  
    Public Sub ChooseFolder()  
        If FolderBrowserDialog1.ShowDialog() = DialogResult.OK Then  
            TextBox1.Text = FolderBrowserDialog1.SelectedPath  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    public void ChooseFolder()  
    {  
        if (folderBrowserDialog1.ShowDialog() == DialogResult.OK)   
        {  
            textBox1.Text = folderBrowserDialog1.SelectedPath;  
        }  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void ChooseFolder()  
       {  
          if (folderBrowserDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Text = folderBrowserDialog1->SelectedPath;  
          }  
       }  
    ```  
  
    > [!IMPORTANT]
    >  このクラスを使用するには、アセンブリに [FileIOPermissionAttribute.PathDiscoveryProperty](frlrfSystemSecurityPermissionsFileIOPermissionAttributeClassPathDiscoveryTopic) プロパティで権限レベルを与える必要があります。このプロパティは、<xref:System.Security.Permissions.FileIOPermissionAccess> 列挙型の一部です。  部分的に信頼できるコンテキストで動作している場合は、権限が不十分なためにプロセスが例外をスローすることがあります。  詳細については、「[コード アクセス セキュリティの基礎](../../../../docs/framework/misc/code-access-security-basics.md)」を参照してください。  
  
 ファイルを保存する方法については、「[方法 : SaveFileDialog コンポーネントを使用してファイルを保存する](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.FolderBrowserDialog>   
 [FolderBrowserDialog コンポーネントの概要 \(Windows フォーム\)](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-overview-windows-forms.md)   
 [FolderBrowserDialog コンポーネント](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)