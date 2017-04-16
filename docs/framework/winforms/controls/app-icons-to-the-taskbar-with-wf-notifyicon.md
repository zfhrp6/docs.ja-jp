---
title: "方法 : Windows フォームの NotifyIcon コンポーネントによってタスクバーにアプリケーション アイコンを追加する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TrayIcon"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "アイコン, 追加 (タスク バーに)"
  - "NotifyIcon コンポーネント"
  - "状態通知領域のアイコン"
  - "タスク バー, 追加 (アイコンを)"
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Windows フォームの NotifyIcon コンポーネントによってタスクバーにアプリケーション アイコンを追加する
Windows フォームの <xref:System.Windows.Forms.NotifyIcon> コンポーネントは、タスクバーの状態通知領域に 1 つのアイコンを表示します。  状態通知領域に複数のアイコンを表示するには、フォームに複数の <xref:System.Windows.Forms.NotifyIcon> コンポーネントを設定する必要があります。  コントロールで表示されるアイコンを設定するには、<xref:System.Windows.Forms.NotifyIcon.Icon%2A> プロパティを使用します。  また、<xref:System.Windows.Forms.NotifyIcon.DoubleClick> イベント ハンドラーにコードを記述して、ユーザーがアイコンをダブルクリックしたときになんらかの処理を行うこともできます。  たとえば、アイコンによって表されるバックグラウンド プロセスをユーザーが設定するためのダイアログ ボックスを表示できます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.NotifyIcon> コンポーネントは、アクションまたはイベントが発生したこと、または状態になんらかの変化があったことをユーザーに通知するためにだけ使用されます。  アプリケーションとの標準的な対話には、メニューやツール バーなどのユーザー インターフェイス要素を使用してください。  
  
### アイコンを設定するには  
  
1.  <xref:System.Windows.Forms.NotifyIcon.Icon%2A> プロパティに値を割り当てます。  これは `System.Drawing.Icon` 型の値であり、.ico ファイルから読み込むことができます。  アイコン ファイルはコードで指定するか、または **\[プロパティ\]** ウィンドウの <xref:System.Windows.Forms.NotifyIcon.Icon%2A> プロパティの横にある省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックし、**\[ファイルを開く\]** ダイアログ ボックスでファイルを選択します。  
  
2.  <xref:System.Windows.Forms.NotifyIcon.Visible%2A> プロパティを `true` に設定します。  
  
3.  <xref:System.Windows.Forms.NotifyIcon.Text%2A> プロパティに適切なツールヒント文字列を設定します。  
  
     次のコード例では、アイコンの場所に対するパスとして **\[マイ ドキュメント\]** フォルダーが設定されています。  この場所を使用するのは、Windows オペレーティング システムを実行するコンピューターには、通常このディレクトリが存在すると考えられるためです。  また、この場所を選択すると、ユーザーは最小限のシステム アクセス レベルでアプリケーションを安全に実行できます。  次の例では、既に <xref:System.Windows.Forms.NotifyIcon> コントロールが追加されたフォームを必要とします。  また、`Icon.ico` という名前のアイコン ファイルも必要です。  
  
     \[Visual Basic\]  
  
    ```  
    ' You should replace the bold icon in the sample below  
    ' with an icon of your own choosing.  
    NotifyIcon1.Icon = New _   
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
    NotifyIcon1.Visible = True  
    NotifyIcon1.Text = "Antivirus program"  
  
    ```  
  
     \[C\#\]  
  
    ```  
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
  
     \[cpp\]  
  
    ```  
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
  
## 参照  
 <xref:System.Windows.Forms.NotifyIcon>   
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>   
 [方法 : ショートカット メニューを Windows フォーム NotifyIcon コンポーネントに関連付ける](../../../../docs/framework/winforms/controls/how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)   
 [NotifyIcon コンポーネント](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)   
 [NotifyIcon コンポーネントの概要](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)