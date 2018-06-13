---
title: '方法 : ショートカット メニューを Windows フォーム NotifyIcon コンポーネントに関連付ける'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], for background processes
- NotifyIcon component [Windows Forms], associating shortcut menus
- shortcut menus [Windows Forms], for background processes
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
ms.openlocfilehash: c0371dfb30c70bd2c4d98362abc7dc06926a5e88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527883"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>方法 : ショートカット メニューを Windows フォーム NotifyIcon コンポーネントに関連付ける
> [!NOTE]
>  <xref:System.Windows.Forms.MenuStrip>と<xref:System.Windows.Forms.ContextMenuStrip>交換し、する機能を追加、<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>以前のバージョンでのコントロール<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>を選択した場合、旧バージョンとの互換性と将来の使用の両方に保持されます。  
  
 <xref:System.Windows.Forms.NotifyIcon>コンポーネントは、タスク バーの状態通知領域にアイコンを表示します。 一般的には、アプリケーションを使用すると、コマンドが表すアプリケーションを送信するには、このアイコンを右クリックします。 関連付けることにより、<xref:System.Windows.Forms.ContextMenu>コンポーネントを<xref:System.Windows.Forms.NotifyIcon>コンポーネントは、この機能は、アプリケーションを追加できます。  
  
> [!NOTE]
>  インスタンスを表示するときに、起動時に最小化するアプリケーションの場合、<xref:System.Windows.Forms.NotifyIcon>タスク バーに、コンポーネント セットのメイン フォームの<xref:System.Windows.Forms.Form.WindowState%2A>プロパティを<xref:System.Windows.Forms.FormWindowState.Minimized>ことを確認して、<xref:System.Windows.Forms.NotifyIcon>コンポーネントの<xref:System.Windows.Forms.NotifyIcon.Visible%2A>プロパティ設定されている`true`です。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>NotifyIcon コンポーネントによってデザイン時に、ショートカット メニューを関連付ける  
  
1.  追加、<xref:System.Windows.Forms.NotifyIcon>コンポーネントをフォームになど、重要なプロパティを設定し、<xref:System.Windows.Forms.NotifyIcon.Icon%2A>と<xref:System.Windows.Forms.NotifyIcon.Visible%2A>プロパティです。  
  
     詳細については、次を参照してください。[する方法: Windows フォームの NotifyIcon コンポーネントによってタスクバーにアプリケーション アイコンを追加](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)です。  
  
2.  追加、<xref:System.Windows.Forms.ContextMenu>コンポーネント、Windows フォームをします。  
  
     実行時に使用可能にコマンドを表すショートカット メニューにメニュー項目を追加します。 アクセス キーなど、これらのメニュー項目にメニューの拡張機能を追加する絶好のタイミングにもです。  
  
3.  設定、<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>のプロパティ、<xref:System.Windows.Forms.NotifyIcon>コンポーネントを追加したショートカット メニューをします。  
  
     このプロパティ セットを持つ、ショートカット メニューが表示されますタスク バーにアイコンがクリックされたとき。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>NotifyIcon コンポーネントによってプログラムでショートカット メニューを関連付ける  
  
1.  インスタンスを作成、<xref:System.Windows.Forms.NotifyIcon>クラスおよび<xref:System.Windows.Forms.ContextMenu>クラスに、アプリケーションに必要なプロパティ設定 (<xref:System.Windows.Forms.NotifyIcon.Icon%2A>と<xref:System.Windows.Forms.NotifyIcon.Visible%2A>のプロパティ、<xref:System.Windows.Forms.NotifyIcon>コンポーネントのメニュー項目を<xref:System.Windows.Forms.ContextMenu>コンポーネントの場合)。  
  
2.  設定、<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>のプロパティ、<xref:System.Windows.Forms.NotifyIcon>コンポーネントを追加したショートカット メニューをします。  
  
     このプロパティ セットを持つ、ショートカット メニューが表示されますタスク バーにアイコンがクリックされたとき。  
  
    > [!NOTE]
    >  次のコード例では、基本的なメニュー構造を作成します。 開発中のアプリケーションに合わせてメニューの選択肢をカスタマイズする必要があります。 さらを処理するコードを書き込む場合は、<xref:System.Windows.Forms.MenuItem.Click>これらのメニュー項目のイベントです。  
  
    ```vb  
    Public ContextMenu1 As New ContextMenu  
    Public NotifyIcon1 As New NotifyIcon  
  
    Public Sub CreateIconMenuStructure()  
       ' Add menu items to shortcut menu.  
       ContextMenu1.MenuItems.Add("&Open Application")  
       ContextMenu1.MenuItems.Add("S&uspend Application")  
       ContextMenu1.MenuItems.Add("E&xit")  
  
       ' Set properties of NotifyIcon component.  
       NotifyIcon1.Icon = New System.Drawing.Icon _   
          (System.Environment.GetFolderPath _   
          (System.Environment.SpecialFolder.Personal)  _   
          & "\Icon.ico")  
       NotifyIcon1.Text = "Right-click me!"  
       NotifyIcon1.Visible = True  
       NotifyIcon1.ContextMenu = ContextMenu1  
    End Sub  
    ```  
  
```csharp  
public NotifyIcon notifyIcon1 = new NotifyIcon();  
public ContextMenu contextMenu1 = new ContextMenu();  
  
public void createIconMenuStructure()  
{  
   // Add menu items to shortcut menu.  
   contextMenu1.MenuItems.Add("&Open Application");  
   contextMenu1.MenuItems.Add("S&uspend Application");  
   contextMenu1.MenuItems.Add("E&xit");  
  
   // Set properties of NotifyIcon component.  
   notifyIcon1.Icon = new System.Drawing.Icon  
      (System.Environment.GetFolderPath  
      (System.Environment.SpecialFolder.Personal)  
      + @"\Icon.ico");  
   notifyIcon1.Visible = true;  
   notifyIcon1.Text = "Right-click me!";  
   notifyIcon1.Visible = true;  
   notifyIcon1.ContextMenu = contextMenu1;  
}  
```  
  
```cpp  
public:  
   System::Windows::Forms::NotifyIcon ^ notifyIcon1;  
   System::Windows::Forms::ContextMenu ^ contextMenu1;  
  
   void createIconMenuStructure()  
   {  
      // Add menu items to shortcut menu.  
      contextMenu1->MenuItems->Add("&Open Application");  
      contextMenu1->MenuItems->Add("S&uspend Application");  
      contextMenu1->MenuItems->Add("E&xit");  
  
      // Set properties of NotifyIcon component.  
      notifyIcon1->Icon = gcnew System::Drawing::Icon  
          (String::Concat(System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::Personal),  
          "\\Icon.ico"));  
      notifyIcon1->Text = "Right-click me!";  
      notifyIcon1->Visible = true;  
      notifyIcon1->ContextMenu = contextMenu1;  
   }  
```  
  
> [!NOTE]
>  初期化する必要があります`notifyIcon1`と`contextMenu1,`フォームのコンス トラクターで、次のステートメントを含めることによって行うことができます。  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [方法: Windows フォームの NotifyIcon コンポーネントによってタスクバーにアプリケーション アイコンを追加する](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)  
 [NotifyIcon コンポーネント](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [NotifyIcon コンポーネントの概要](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
