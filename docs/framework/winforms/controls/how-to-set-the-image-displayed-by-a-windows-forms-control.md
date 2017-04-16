---
title: "方法 : Windows フォーム コントロールによって表示されるイメージを設定する | Microsoft Docs"
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
  - "Button コントロール [Windows フォーム], イメージ"
  - "コントロール [Windows フォーム], イメージ"
  - "例 [Windows フォーム], コントロール"
  - "イメージ [Windows フォーム], Windows フォーム コントロール"
  - "Windows フォーム コントロール, イメージ"
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Windows フォーム コントロールによって表示されるイメージを設定する
いくつかの Windows フォーム コントロールは、イメージを表示できます。  イメージの例としては、ボタン上のフロッピー ディスクのアイコンが**\[上書き保存\]** コマンドを示すように、コントロールの目的を明確にするアイコンがあります。  また、コントロールに特定の外観と動作を与えるための背景イメージとしてのアイコンもあります。  
  
### コントロールによって表示されるイメージを設定するには  
  
1.  コントロールの `Image` または `BackgroundImage` プロパティを <xref:System.Drawing.Image> 型のオブジェクトに設定します。  一般的に、ファイルからイメージを読み込む場合は、<xref:System.Drawing.Image.FromFile%2A> メソッドを使用します。  
  
     次のコード例では、イメージの場所に対するパスとして **\[マイ ピクチャ\]** フォルダーが設定されています。  Windows オペレーティング システムを実行するほとんどのコンピューターには、このディレクトリがあります。  また、ユーザーは最小限のシステム アクセス レベルでアプリケーションを安全に実行できます。  次のコード例では、既に <xref:System.Windows.Forms.PictureBox> コントロールが追加されたフォームが必要です。  
  
    ```vb  
    ' Replace the image named below  
    ' with an icon of your own choosing.  
    PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.MyPictures) _  
       & "\Image.gif")  
  
    ```  
  
    ```csharp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.MyPictures)  
       + @"\Image.gif");  
  
    ```  
  
    ```cpp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    pictureBox1->Image = Image::FromFile(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::MyPictures),  
       "\\Image.gif"));  
    ```  
  
## 参照  
 <xref:System.Drawing.Image.FromFile%2A>   
 <xref:System.Drawing.Image>   
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>