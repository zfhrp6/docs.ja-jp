---
title: "方法 : ショートカット メニューを Windows フォーム NotifyIcon コンポーネントに関連付ける"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], for background processes
- NotifyIcon component [Windows Forms], associating shortcut menus
- shortcut menus [Windows Forms], for background processes
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 985aa58056f4c4ec8f3042c682291508f1434ee0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a><span data-ttu-id="cf2ec-102">方法 : ショートカット メニューを Windows フォーム NotifyIcon コンポーネントに関連付ける</span><span class="sxs-lookup"><span data-stu-id="cf2ec-102">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>
> [!NOTE]
>  <span data-ttu-id="cf2ec-103"><xref:System.Windows.Forms.MenuStrip>と<xref:System.Windows.Forms.ContextMenuStrip>交換し、する機能を追加、<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>以前のバージョンでのコントロール<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>を選択した場合、旧バージョンとの互換性と将来の使用の両方に保持されます。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="cf2ec-104"><xref:System.Windows.Forms.NotifyIcon>コンポーネントは、タスク バーの状態通知領域にアイコンを表示します。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-104">The <xref:System.Windows.Forms.NotifyIcon> component displays an icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="cf2ec-105">一般的には、アプリケーションを使用すると、コマンドが表すアプリケーションを送信するには、このアイコンを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-105">Commonly, applications enable you to right-click this icon to send commands to the application it represents.</span></span> <span data-ttu-id="cf2ec-106">関連付けることにより、<xref:System.Windows.Forms.ContextMenu>コンポーネントを<xref:System.Windows.Forms.NotifyIcon>コンポーネントは、この機能は、アプリケーションを追加できます。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-106">By associating a <xref:System.Windows.Forms.ContextMenu> component with the <xref:System.Windows.Forms.NotifyIcon> component, you can add this functionality to your applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf2ec-107">インスタンスを表示するときに、起動時に最小化するアプリケーションの場合、<xref:System.Windows.Forms.NotifyIcon>タスク バーに、コンポーネント セットのメイン フォームの<xref:System.Windows.Forms.Form.WindowState%2A>プロパティを<xref:System.Windows.Forms.FormWindowState.Minimized>ことを確認して、<xref:System.Windows.Forms.NotifyIcon>コンポーネントの<xref:System.Windows.Forms.NotifyIcon.Visible%2A>プロパティ設定されている`true`です。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-107">If you want your application to be minimized at startup while displaying an instance of the <xref:System.Windows.Forms.NotifyIcon> component in the taskbar, set the main form's <xref:System.Windows.Forms.Form.WindowState%2A> property to <xref:System.Windows.Forms.FormWindowState.Minimized> and be sure the <xref:System.Windows.Forms.NotifyIcon> component's <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property is set to `true`.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a><span data-ttu-id="cf2ec-108">NotifyIcon コンポーネントによってデザイン時に、ショートカット メニューを関連付ける</span><span class="sxs-lookup"><span data-stu-id="cf2ec-108">To associate a shortcut menu with the NotifyIcon component at design time</span></span>  
  
1.  <span data-ttu-id="cf2ec-109">追加、<xref:System.Windows.Forms.NotifyIcon>コンポーネントをフォームになど、重要なプロパティを設定し、<xref:System.Windows.Forms.NotifyIcon.Icon%2A>と<xref:System.Windows.Forms.NotifyIcon.Visible%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-109">Add a <xref:System.Windows.Forms.NotifyIcon> component to your form, and set the important properties, such as the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties.</span></span>  
  
     <span data-ttu-id="cf2ec-110">詳細については、次を参照してください。[する方法: Windows フォームの NotifyIcon コンポーネントによってタスクバーにアプリケーション アイコンを追加](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)です。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-110">For more information, see [How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
2.  <span data-ttu-id="cf2ec-111">追加、<xref:System.Windows.Forms.ContextMenu>コンポーネント、Windows フォームをします。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-111">Add a <xref:System.Windows.Forms.ContextMenu> component to your Windows Form.</span></span>  
  
     <span data-ttu-id="cf2ec-112">実行時に使用可能にコマンドを表すショートカット メニューにメニュー項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-112">Add menu items to the shortcut menu representing the commands you want to make available at run time.</span></span> <span data-ttu-id="cf2ec-113">アクセス キーなど、これらのメニュー項目にメニューの拡張機能を追加する絶好のタイミングにもです。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-113">This is also a good time to add menu enhancements to these menu items, such as access keys.</span></span>  
  
3.  <span data-ttu-id="cf2ec-114">設定、<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>のプロパティ、<xref:System.Windows.Forms.NotifyIcon>コンポーネントを追加したショートカット メニューをします。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-114">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="cf2ec-115">このプロパティ セットを持つ、ショートカット メニューが表示されますタスク バーにアイコンがクリックされたとき。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-115">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a><span data-ttu-id="cf2ec-116">NotifyIcon コンポーネントによってプログラムでショートカット メニューを関連付ける</span><span class="sxs-lookup"><span data-stu-id="cf2ec-116">To associate a shortcut menu with the NotifyIcon component programmatically</span></span>  
  
1.  <span data-ttu-id="cf2ec-117">インスタンスを作成、<xref:System.Windows.Forms.NotifyIcon>クラスおよび<xref:System.Windows.Forms.ContextMenu>クラスに、アプリケーションに必要なプロパティ設定 (<xref:System.Windows.Forms.NotifyIcon.Icon%2A>と<xref:System.Windows.Forms.NotifyIcon.Visible%2A>のプロパティ、<xref:System.Windows.Forms.NotifyIcon>コンポーネントのメニュー項目を<xref:System.Windows.Forms.ContextMenu>コンポーネントの場合)。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-117">Create an instance of the <xref:System.Windows.Forms.NotifyIcon> class and a <xref:System.Windows.Forms.ContextMenu> class, with whatever property settings are necessary for the application (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties for the <xref:System.Windows.Forms.NotifyIcon> component, menu items for the <xref:System.Windows.Forms.ContextMenu> component).</span></span>  
  
2.  <span data-ttu-id="cf2ec-118">設定、<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>のプロパティ、<xref:System.Windows.Forms.NotifyIcon>コンポーネントを追加したショートカット メニューをします。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-118">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="cf2ec-119">このプロパティ セットを持つ、ショートカット メニューが表示されますタスク バーにアイコンがクリックされたとき。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-119">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cf2ec-120">次のコード例では、基本的なメニュー構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-120">The following code example creates a basic menu structure.</span></span> <span data-ttu-id="cf2ec-121">開発中のアプリケーションに合わせてメニューの選択肢をカスタマイズする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-121">You will need to customize the menu choices to those that fit the application you are developing.</span></span> <span data-ttu-id="cf2ec-122">さらを処理するコードを書き込む場合は、<xref:System.Windows.Forms.MenuItem.Click>これらのメニュー項目のイベントです。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-122">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.MenuItem.Click> events for these menu items.</span></span>  
  
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
>  <span data-ttu-id="cf2ec-123">初期化する必要があります`notifyIcon1`と`contextMenu1,`フォームのコンス トラクターで、次のステートメントを含めることによって行うことができます。</span><span class="sxs-lookup"><span data-stu-id="cf2ec-123">You must initialize `notifyIcon1` and `contextMenu1,` which you can do by including the following statements in the constructor of your form:</span></span>  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf2ec-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf2ec-124">See Also</span></span>  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [<span data-ttu-id="cf2ec-125">方法: Windows フォームの NotifyIcon コンポーネントによってタスクバーにアプリケーション アイコンを追加する</span><span class="sxs-lookup"><span data-stu-id="cf2ec-125">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)  
 [<span data-ttu-id="cf2ec-126">NotifyIcon コンポーネント</span><span class="sxs-lookup"><span data-stu-id="cf2ec-126">NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [<span data-ttu-id="cf2ec-127">NotifyIcon コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="cf2ec-127">NotifyIcon Component Overview</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
