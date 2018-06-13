---
title: '方法 : Windows フォームの NotifyIcon コンポーネントによってタスクバーにアプリケーション アイコンを追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TrayIcon
helpviewer_keywords:
- status area icons
- icons [Windows Forms], adding to taskbar
- NotifyIcon component
- taskbar [Windows Forms], adding icons
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
ms.openlocfilehash: c7658a3a1c72c3fed4033e644d0dd776b06ee1a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525414"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>方法 : Windows フォームの NotifyIcon コンポーネントによってタスクバーにアプリケーション アイコンを追加する
Windows フォーム<xref:System.Windows.Forms.NotifyIcon>コンポーネントには、タスク バーの状態通知領域に 1 つのアイコンが表示されます。 状態 領域で複数のアイコンを表示するにする必要があります複数<xref:System.Windows.Forms.NotifyIcon>フォーム上のコンポーネントです。 コントロールで表示されるアイコンを設定するには、使用、<xref:System.Windows.Forms.NotifyIcon.Icon%2A>プロパティです。 コードを記述することも、<xref:System.Windows.Forms.NotifyIcon.DoubleClick>のため、その問題が起こった、ユーザーがアイコンをダブルクリックすると、イベント ハンドラー。 たとえば、行うことができるダイアログ ボックスをユーザーがアイコンで表されるバック グラウンド プロセスの構成を表示します。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.NotifyIcon>コンポーネントは、アクションまたはイベントが発生した警告のユーザーに通知の目的でのみ、使用または何らかのステータスの変更が発生しました。 アプリケーションと標準的な対話するため、メニューのツールバー、およびその他のユーザー インターフェイス要素を使用する必要があります。  
  
### <a name="to-set-the-icon"></a>アイコンを設定するには  
  
1.  値を割り当てる、<xref:System.Windows.Forms.NotifyIcon.Icon%2A>プロパティです。 値型でなければなりません`System.Drawing.Icon`.ico ファイルから読み込まれたを指定できます。 または、省略記号ボタンをクリックしてコードでは、アイコン ファイルを指定できます (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) の横に、<xref:System.Windows.Forms.NotifyIcon.Icon%2A>プロパティに、 **プロパティ**ウィンドウ、および内のファイルを選択し、**開く**表示されるダイアログ ボックス。  
  
2.  <xref:System.Windows.Forms.NotifyIcon.Visible%2A> プロパティを `true` に設定します。  
  
3.  設定、<xref:System.Windows.Forms.NotifyIcon.Text%2A>プロパティを適切なツールヒント文字列です。  
  
     アイコンの場所は次のコード例では、パスが設定、**マイ ドキュメント**フォルダーです。 この場所は、Windows オペレーティング システムを実行しているほとんどのコンピューターがこのフォルダーを含めることを想定するために使用されます。 この場所を選択すると、ユーザーは最小限のシステム アクセスのレベルでアプリケーションを安全に実行もできます。 次の例には、フォームが必要です、<xref:System.Windows.Forms.NotifyIcon>コントロールが既に追加されています。 また、という名前のアイコン ファイルが必要に`Icon.ico`です。  
  
    ```vb  
    ' You should replace the bold icon in the sample below  
    ' with an icon of your own choosing.  
    NotifyIcon1.Icon = New _   
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
    NotifyIcon1.Visible = True  
    NotifyIcon1.Text = "Antivirus program"  
    ```  
  
    ```csharp  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    notifyIcon1.Icon =   
       new System.Drawing.Icon (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Icon.ico");  
    notifyIcon1.Visible = true;  
    notifyIcon1.Text = "Antivirus program";  
    ```  
  
    ```cpp  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    notifyIcon1->Icon = gcnew   
       System::Drawing::Icon(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Icon.ico"));  
    notifyIcon1->Visible = true;  
    notifyIcon1->Text = "Antivirus program";  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [方法: ショートカット メニューを Windows フォーム NotifyIcon コンポーネントに関連付ける](../../../../docs/framework/winforms/controls/how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)  
 [NotifyIcon コンポーネント](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [NotifyIcon コンポーネントの概要](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
