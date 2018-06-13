---
title: '方法: Windows フォーム FolderBrowserDialog コンポーネントを使用してフォルダーを選択する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
ms.openlocfilehash: 657aad6efa195ec3d9741f4f91d4e01af4a54a19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531236"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>方法: Windows フォーム FolderBrowserDialog コンポーネントを使用してフォルダーを選択する
多くの場合、作成した Windows アプリケーション内で、フォルダーを選択するようにユーザーに促す必要があります。とりわけ、一連のファイルを保存するように求める場合が多いです。 Windows フォーム<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントでは、このタスクを簡単に実行することができます。  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>FolderBrowserDialog コンポーネントを使用してフォルダーを選択するには  
  
1.  プロシージャでは、確認、<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントの<xref:System.Windows.Forms.Form.DialogResult%2A> ダイアログ ボックスが閉じられました方法を表示し、値を取得するプロパティ、<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントの<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>プロパティです。  
  
2.  ダイアログ ボックスのツリー ビューに表示されるセットの最上位のフォルダーの必要がある場合は、設定、<xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>プロパティのメンバー、<xref:System.Environment.SpecialFolder>列挙します。  
  
3.  さらに、設定、<xref:System.Windows.Forms.FolderBrowserDialog.Description%2A>フォルダー ブラウザーのツリー ビューの上部にあるテキスト文字列を指定するには、プロパティが表示されます。  
  
     次の例で、<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントを使用して Visual Studio でプロジェクトを作成し、保存するフォルダーを選択するように求められますのようなフォルダーを選択します。 この例では、フォルダー名に表示されますが、<xref:System.Windows.Forms.TextBox>フォーム上のコントロールです。 編集可能な領域のなどの場所を配置することをお勧め、<xref:System.Windows.Forms.TextBox>を制御するユーザーがエラーまたはその他の問題が発生した場合、選択項目を編集できるようにします。 この例では、フォーム、<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントおよび<xref:System.Windows.Forms.TextBox>コントロール。  
  
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
    >  このクラスを使用するアセンブリが必要です、特権レベル許可によって、<xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>含まれているプロパティの<xref:System.Security.Permissions.FileIOPermissionAccess>列挙します。 部分的に信頼されたコンテキストで実行している場合、プロセスは、特権がないため例外をスローする可能性があります。 詳しくは、「[コード アクセス セキュリティの基礎](../../../../docs/framework/misc/code-access-security-basics.md)」をご覧ください。  
  
 ファイルの保存方法については、「[方法: SaveFileDialog コンポーネントを使用してファイルを保存する](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.FolderBrowserDialog>  
 [FolderBrowserDialog コンポーネントの概要 (Windows フォーム)](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-overview-windows-forms.md)  
 [FolderBrowserDialog コンポーネント](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)
