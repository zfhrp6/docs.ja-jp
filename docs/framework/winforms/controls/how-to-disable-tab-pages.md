---
title: "方法 : タブ ページを無効化する | Microsoft Docs"
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
  - "タブ ページ, 非表示 (フォーム内の)"
  - "TabControl コントロール [Windows フォーム], 無効化 (ページを)"
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : タブ ページを無効化する
状況によっては、Windows フォーム アプリケーション内で使用できるデータへのアクセスを制限する必要があります。  タブ コントロールのタブ ページに表示されるデータがその一例です。タブ ページの情報の中には、管理者がゲストや低いレベルのユーザーによるアクセスを制限する必要があると考える情報もあります。  
  
### タブ ページをプログラムで無効にするには  
  
1.  タブ コントロールの <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> イベントを処理するコードを記述します。  このイベントは、ユーザーが 1 つのタブから次のタブに切り替えたときに発生します。  
  
2.  資格情報を確認します。  ユーザーに対してタブを表示する前に、提供される情報に応じて、そのユーザーがログインに使用したユーザー名や、その他の形式の資格情報を確認します。  
  
3.  ユーザーの資格情報が適切である場合は、クリックされたタブを表示します。  ユーザーが適切な資格情報を持っていない場合は、アクセス権がないことをメッセージ ボックスなどのユーザー インターフェイスで示し、最初のタブに戻ります。  
  
    > [!NOTE]
    >  この機能を実際のアプリケーションに実装する場合には、この資格情報チェックをフォームの <xref:System.Windows.Forms.Form.Load> イベントで実行できます。  このイベントを実行すると、ユーザー インターフェイスが表示される前にタブを非表示にできます。こちらの方が洗練されたプログラミング方法です。  <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> イベントで資格情報を確認してタブを無効にする次の手順は、説明のために示しています。  
  
4.  オプションとして、タブ ページが 3 つ以上ある場合には、元のタブ ページと異なるタブ ページを表示できます。  
  
     次の例では、タブにアクセスするための条件がアプリケーションによって異なるため、資格情報を確認する代わりに <xref:System.Windows.Forms.CheckBox> コントロールが使用されています。  <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> イベントが発生すると、資格情報チェックが true であり \(つまり、チェック ボックスがオンであり\)、選択されたタブが `TabPage2` \(この例では機密情報を含むタブ\) である場合は、`TabPage2` が表示されます。  それ以外の場合は `TabPage3` が表示され、適切なアクセス権限がないことを示すメッセージ ボックスがユーザーに表示されます。  次のコードでは、フォームに <xref:System.Windows.Forms.CheckBox> コントロール \(`CredentialCheck`\) と、3 つのタブ ページを含む <xref:System.Windows.Forms.TabControl> コントロールがあると仮定しています。  
  
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
  
     \(Visual C\#、Visual C\+\+\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## 参照  
 [TabControl コントロールの概要](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)   
 [方法 : タブ ページにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)   
 [方法 : Windows フォーム TabControl のタブを追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)   
 [方法 : Windows フォーム TabControl の表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)