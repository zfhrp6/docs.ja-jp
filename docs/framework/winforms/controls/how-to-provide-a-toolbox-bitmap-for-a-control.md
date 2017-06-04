---
title: "方法 : コントロールにツールボックス ビットマップを指定する | Microsoft Docs"
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
  - "ビットマップ [Windows フォーム], カスタム コントロール"
  - "カスタム コントロール [Windows フォーム], ツールボックスのビットマップ"
  - "ツールボックス [Windows フォーム], 追加 (カスタム コントロール用のビットマップを)"
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 方法 : コントロールにツールボックス ビットマップを指定する
コントロールの特殊なアイコンを**ツールボックス**に表示させる場合は、<xref:System.Drawing.ToolboxBitmapAttribute> を使用して特定のイメージを指定します。  このクラスは*属性*であり、他のクラスに追加できる特殊なクラスです。  属性の詳細については、[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] の場合は「[NOT IN BUILD: Attributes Overview in Visual Basic](http://msdn.microsoft.com/ja-jp/0d0cff64-892d-4f57-83bd-bef388553d4f)」、[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] の場合は「[属性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 <xref:System.Drawing.ToolboxBitmapAttribute> を使用すると、16 x 16 ピクセルのビットマップのパスとファイル名を示す文字列を指定できます。  コントロールを**ツールボックス**に追加すると、このビットマップがコントロールの横に表示されます。  また、<xref:System.Type> を指定して、特定の種類に関連付けられたビットマップを読み込むようにすることもできます。  <xref:System.Type> と文字列の両方を指定すると、コントロールは、<xref:System.Type> パラメーターで指定された種類のイメージが含まれるアセンブリから、文字列パラメーターで指定された名前のイメージ リソースを検索します。  
  
### コントロールにツールボックス ビットマップを指定するには  
  
1.  コントロールのクラス宣言に <xref:System.Drawing.ToolboxBitmapAttribute> を追加します。[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] の場合は `Class` キーワードの前に、[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] の場合はクラス宣言の上に追加します。  
  
    ```vb  
    ' Specifies the bitmap associated with the Button type.  
    <ToolboxBitmap(GetType(Button))> Class MyControl1  
    ' Specifies a bitmap file.  
    End Class  
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _  
       Class MyControl2  
    End Class  
    ' Specifies a type that indicates the assembly to search, and the name   
    ' of an image resource to look for.  
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl  
    End Class  
    ```  
  
    ```csharp  
    // Specifies the bitmap associated with the Button type.  
    [ToolboxBitmap(typeof(Button))]  
    class MyControl1 : UserControl  
    {  
    }  
    // Specifies a bitmap file.  
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]  
    class MyControl2 : UserControl  
    {  
    }  
    // Specifies a type that indicates the assembly to search, and the name   
    // of an image resource to look for.  
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]  
    class MyControl : UserControl  
    {  
    }  
    ```  
  
2.  プロジェクトを再ビルドします。  
  
    > [!NOTE]
    >  自動的に生成されたコントロールとコンポーネントのビットマップがツールボックスに表示されません。  ビットマップを表示するには、**\[ツールボックス アイテムの選択\]** ダイアログ ボックスを使用してコントロールを再読み込みします。  詳細については、「[チュートリアル : ツールボックスへのカスタム コンポーネントの自動設定](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)」を参照してください。  
  
## 参照  
 <xref:System.Drawing.ToolboxBitmapAttribute>   
 [チュートリアル : ツールボックスへのカスタム コンポーネントの自動設定](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)   
 [デザイン時の Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)   
 [Attributes](../Topic/Attributes%20\(Visual%20Basic\)1.md)   
 [属性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)