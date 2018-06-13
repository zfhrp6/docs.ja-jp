---
title: '方法 : タブ ページを無効化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 94d8522a71fcd565ae8f994d73ffe4c46fcf7ce3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534268"
---
# <a name="how-to-disable-tab-pages"></a>方法 : タブ ページを無効化する
状況によっては、Windows フォーム アプリケーション内で使用可能なデータへのアクセスを制限するされます。 タブ コントロールのタブ ページに表示されるデータがある場合、一例があります。guest アカウントや下位レベルのユーザーを制限するタブ ページ上の情報を保持できたは、管理者。  
  
### <a name="to-disable-tab-pages-programmatically"></a>タブ ページをプログラムで無効にするには  
  
1.  タブ コントロールを処理するコードを記述<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>イベント。 これは、ユーザーが 1 つのタブから、次に切り替わるときに発生するイベントです。  
  
2.  資格情報を確認してください。 によって表示される情報は、タブを表示するユーザーを許可する前に、ユーザーがログインに使用するユーザー名またはその他の何らかの資格情報を確認することがあります。  
  
3.  ユーザーに適切な資格情報がある場合は、クリックしてされたタブを表示します。 ユーザーは、適切な資格情報を持っていない場合は、メッセージ ボックスを表示またはことを示すその他のユーザー インターフェイスはないとアクセスできるため、最初のタブに戻ります。  
  
    > [!NOTE]
    >  フォームの中にこの資格情報チェックを実行するには、実稼働アプリケーションでこの機能を実装するときに<xref:System.Windows.Forms.Form.Load>イベント。 これによって、プログラミングをはるかにクリーナー方法は、すべてのユーザー インターフェイスが表示される前に、タブを非表示にできます。 以下を使用する方法 (資格情報の確認と中に、タブを無効化、<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>イベント) は、わかりやすくするためです。  
  
4.  必要に応じて、3 つ以上のタブ ページがある場合は場合、は、元と異なるタブ ページを表示します。  
  
     次の例で、<xref:System.Windows.Forms.CheckBox>コントロールを使用して、代わりに、タブへのアクセスは、アプリケーションによって異なりますに対する条件として、資格情報を確認します。 ときに、<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>イベントは、資格情報チェックが true の場合 (つまり、チェック ボックスをオン)、選択したタブで、 `TabPage2` (この例では、機密情報をタブ)、し、`TabPage2`が表示されます。 それ以外の場合、`TabPage3`が表示されますされ、ユーザーに適切なアクセス特権がないことを示すメッセージ ボックスが表示されます。 次のコードにフォームを前提としています、<xref:System.Windows.Forms.CheckBox>コントロール (`CredentialCheck`) および<xref:System.Windows.Forms.TabControl>3 つのタブ ページを持つコントロール。  
  
    ```vb  
    Private Sub TabControl1_SelectedIndexChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles TabControl1.SelectedIndexChanged  
       ' Check Credentials Here  
  
       If CredentialCheck.Checked = True And _   
       TabControl1.SelectedTab Is TabPage2 Then  
          TabControl1.SelectedTab = TabPage2  
       ElseIf CredentialCheck.Checked = False _   
       And TabControl1.SelectedTab Is TabPage2 Then  
          MessageBox.Show _   
         ("Unable to load tab. You have insufficient access privileges.")  
          TabControl1.SelectedTab = TabPage3  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void tabControl1_SelectedIndexChanged(object sender, System.EventArgs e)  
    {  
        // Check Credentials Here  
  
        if ((CredentialCheck.Checked == true) && (tabControl1.SelectedTab == tabPage2))   
        {  
            tabControl1.SelectedTab = tabPage2;  
        }  
        else if ((CredentialCheck.Checked == false) && (tabControl1.SelectedTab == tabPage2))  
        {  
            MessageBox.Show("Unable to load tab. You have insufficient access privileges.");  
            tabControl1.SelectedTab = tabPage3;  
        }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void tabControl1_SelectedIndexChanged(  
          System::Object ^ sender,  
          System::EventArgs ^  e)  
       {  
          // Check Credentials Here  
          if ((CredentialCheck->Checked == true) &&  
              (tabControl1->SelectedTab == tabPage2))  
          {  
             tabControl1->SelectedTab = tabPage2;  
          }  
          else if ((CredentialCheck->Checked == false) &&  
                   (tabControl1->SelectedTab == tabPage2))  
          {  
             MessageBox::Show(String::Concat("Unable to load tab. ",  
                "You have insufficient access privileges."));  
             tabControl1->SelectedTab = tabPage3;  
          }  
       }  
    ```  
  
     (Visual c#、Visual C)イベント ハンドラーを登録するフォームのコンス トラクターに次のコードを配置します。  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a>関連項目  
 [TabControl コントロールの概要](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [方法: タブ ページにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [方法: Windows フォーム TabControl のタブを追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)  
 [方法: Windows フォーム TabControl の表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
