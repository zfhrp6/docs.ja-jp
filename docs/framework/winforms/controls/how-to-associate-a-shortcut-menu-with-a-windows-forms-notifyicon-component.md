---
title: "方法 : ショートカット メニューを Windows フォーム NotifyIcon コンポーネントに関連付ける | Microsoft Docs"
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
  - "コンテキスト メニュー, バックグラウンド プロセスの"
  - "NotifyIcon コンポーネント, 関連付け (ショートカット メニュー)"
  - "ショートカット メニュー, バックグラウンド プロセスの"
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : ショートカット メニューを Windows フォーム NotifyIcon コンポーネントに関連付ける
> [!NOTE]
>  <xref:System.Windows.Forms.MenuStrip> と <xref:System.Windows.Forms.ContextMenuStrip> は、以前のバージョンの <xref:System.Windows.Forms.MainMenu> コントロールおよび <xref:System.Windows.Forms.ContextMenu> コントロールに代わると共に追加の機能を提供しますが、<xref:System.Windows.Forms.MainMenu> および <xref:System.Windows.Forms.ContextMenu> は、下位互換性を保つ目的および将来使用する目的で、必要に応じて保持できます。  
  
 <xref:System.Windows.Forms.NotifyIcon> コンポーネントは、タスクバーの状態通知領域に 1 つのアイコンを表示します。  一般に、アプリケーションでは、このアイコンを右クリックすると、アイコンに対応するアプリケーションにコマンドを送信できるようになっています。  <xref:System.Windows.Forms.NotifyIcon> コンポーネントに <xref:System.Windows.Forms.ContextMenu> コンポーネントを関連付けると、この機能をアプリケーションに追加できます。  
  
> [!NOTE]
>  起動時にアプリケーションを最小化し、<xref:System.Windows.Forms.NotifyIcon> コンポーネントのインスタンスをタスクバーに表示する場合は、メイン フォームの <xref:System.Windows.Forms.Form.WindowState%2A> プロパティを <xref:System.Windows.Forms.FormWindowState> に設定し、<xref:System.Windows.Forms.NotifyIcon> コンポーネントの <xref:System.Windows.Forms.NotifyIcon.Visible%2A> プロパティを必ず `true` に設定します。  
  
### デザイン時に、NotifyIcon コンポーネントにショートカット メニューを関連付けるには  
  
1.  フォームに <xref:System.Windows.Forms.NotifyIcon> コンポーネントを追加し、<xref:System.Windows.Forms.NotifyIcon.Icon%2A> や <xref:System.Windows.Forms.NotifyIcon.Visible%2A> などの重要なプロパティを設定します。  
  
     詳細については、「[方法 : Windows フォームの NotifyIcon コンポーネントによってタスクバーにアプリケーション アイコンを追加する](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)」を参照してください。  
  
2.  Windows フォームに <xref:System.Windows.Forms.ContextMenu> コンポーネントを追加します。  
  
     実行時に使用できるようにするコマンドを表すメニュー項目をショートカット メニューに追加します。  ここで、メニュー項目にアクセス キーなどのメニュー機能拡張を追加することもできます。  
  
3.  追加したショートカット メニューに <xref:System.Windows.Forms.NotifyIcon> コンポーネントの <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> プロパティを設定します。  
  
     このプロパティを設定すると、タスク バーのアイコンがクリックされたときにショートカット メニューが表示されるようになります。  
  
### プログラムで NotifyIcon コンポーネントにショートカット メニューを関連付けるには  
  
1.  アプリケーションに必要なすべてのプロパティ \(<xref:System.Windows.Forms.NotifyIcon> コンポーネントについて <xref:System.Windows.Forms.NotifyIcon.Icon%2A> プロパティと <xref:System.Windows.Forms.NotifyIcon.Visible%2A> プロパティ、<xref:System.Windows.Forms.ContextMenu> コンポーネントについてはメニュー項目\) を設定して <xref:System.Windows.Forms.NotifyIcon> クラスと <xref:System.Windows.Forms.ContextMenu> クラスのインスタンスを作成します。  
  
2.  追加したショートカット メニューに <xref:System.Windows.Forms.NotifyIcon> コンポーネントの <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> プロパティを設定します。  
  
     このプロパティを設定すると、タスク バーのアイコンがクリックされたときにショートカット メニューが表示されるようになります。  
  
    > [!NOTE]
    >  次のコード例では、基本的なメニュー構造を作成します。  配置するアプリケーションに合わせてメニューの選択肢をカスタマイズする必要があります。  さらに、これらのメニュー項目に対する <xref:System.Windows.Forms.MenuItem.Click> イベントを処理するコードも記述する必要があります。  
  
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
>  `notifyIcon1` と `contextMenu1,` を初期化する必要があります。そのためには、フォームのコンストラクターに次のステートメントを挿入します。  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## 参照  
 <xref:System.Windows.Forms.NotifyIcon>   
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>   
 [方法 : Windows フォームの NotifyIcon コンポーネントによってタスクバーにアプリケーション アイコンを追加する](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)   
 [NotifyIcon コンポーネント](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)   
 [NotifyIcon コンポーネントの概要](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)