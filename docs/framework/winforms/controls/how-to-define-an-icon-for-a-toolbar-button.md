---
title: "方法 : ツール バー ボタンのアイコンを定義する | Microsoft Docs"
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
  - "ボタン [Windows フォーム], アイコン"
  - "例 [Windows フォーム], ツール バー"
  - "アイコン [Windows フォーム], ツール バー ボタン"
  - "イメージ [Windows フォーム], ツール バー ボタン"
  - "ToolBar コントロール [Windows フォーム], 追加 (ボタンにアイコンを)"
  - "ツール バー [Windows フォーム], 追加 (ボタンにアイコンを)"
ms.assetid: 84db98b4-8566-49ce-b2c8-1fd66a5eb3a0
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : ツール バー ボタンのアイコンを定義する
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 <xref:System.Windows.Forms.ToolBar> のボタンには、ユーザーが簡単に識別できるようにアイコンを表示することができます。  アイコンを表示するには、[ImageList コンポーネント](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) コンポーネントにイメージを追加した後、<xref:System.Windows.Forms.ImageList> コンポーネントを <xref:System.Windows.Forms.ToolBar> コントロールに関連付けます。  
  
### プログラム実行時にツール バー ボタンのアイコンを設定するには  
  
1.  プロシージャで、<xref:System.Windows.Forms.ImageList> コンポーネントと <xref:System.Windows.Forms.ToolBar> コントロールをインスタンス化します。  
  
2.  同じプロシージャで、イメージを <xref:System.Windows.Forms.ImageList> コンポーネントに割り当てます。  
  
3.  同じプロシージャで、<xref:System.Windows.Forms.ImageList> コントロールを <xref:System.Windows.Forms.ToolBar> コントロールに割り当て、各ツール バー ボタンに <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> プロパティを割り当てます。  
  
     次のコード例では、イメージの場所に対するパスとして **My Documents** フォルダーが設定されています。  これは、Windows オペレーティング システムを実行するコンピューターには、通常このディレクトリが存在すると考えられるためです。  また、ユーザーは最小限のシステム アクセス レベルでアプリケーションを安全に実行できます。  次の例は、既に <xref:System.Windows.Forms.PictureBox> コントロールが追加されたフォームを想定しています。  
  
     上記の手順に従った場合、コードは次のようになります。  
  
    ```vb  
    Public Sub InitializeMyToolBar()  
    ' Instantiate an ImageList component and a ToolBar control.  
       Dim ToolBar1 as New ToolBar  
       Dim ImageList1 as New ImageList  
    ' Assign an image to the ImageList component.  
    ' You should replace the bold image  
    ' in the sample below with an icon of your own choosing.  
       Dim myImage As System.Drawing.Image = _   
          Image.FromFile Image.FromFile _  
          (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.Personal) _  
          & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    ' Create a ToolBarButton.  
       Dim ToolBarButton1 As New ToolBarButton()  
    ' Add the ToolBarButton to the ToolBar.  
       ToolBar1.Buttons.Add(toolBarButton1)  
    ' Assign an ImageList to the ToolBar.  
       ToolBar1.ImageList = ImageList1  
    ' Assign the ImageIndex property of the ToolBarButton.  
       ToolBarButton1.ImageIndex = 0  
    End Sub  
  
    ```  
  
    ```csharp  
    public void InitializeMyToolBar()  
    {  
       // Instantiate an ImageList component and a ToolBar control.  
       ToolBar toolBar1 = new  ToolBar();   
       ImageList imageList1 = new ImageList();  
       // Assign an image to the ImageList component.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       Image myImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
       // Create a ToolBarButton.  
       ToolBarButton toolBarButton1 = new ToolBarButton();  
       // Add the ToolBarButton to the ToolBar.  
       toolBar1.Buttons.Add(toolBarButton1);  
       // Assign an ImageList to the ToolBar.  
       toolBar1.ImageList = imageList1;  
       // Assign ImageIndex property of the ToolBarButton.  
       toolBarButton1.ImageIndex = 0;  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void InitializeMyToolBar()  
       {  
          // Instantiate an ImageList component and a ToolBar control.  
          ToolBar ^ toolBar1 = gcnew  ToolBar();   
          ImageList ^ imageList1 = gcnew ImageList();  
          // Assign an image to the ImageList component.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          Image ^ myImage = Image::FromFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
          // Create a ToolBarButton.  
          ToolBarButton ^ toolBarButton1 = gcnew ToolBarButton();  
          // Add the ToolBarButton to the ToolBar.  
          toolBar1->Buttons->Add(toolBarButton1);  
          // Assign an ImageList to the ToolBar.  
          toolBar1->ImageList = imageList1;  
          // Assign ImageIndex property of the ToolBarButton.  
          toolBarButton1->ImageIndex = 0;  
       }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ToolBar>   
 [方法 : ツール バー ボタンのメニュー イベントをトリガーする](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)   
 [ToolBar コントロール](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)   
 [ImageList コンポーネント](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)