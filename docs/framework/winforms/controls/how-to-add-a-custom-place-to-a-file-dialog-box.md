---
title: "方法 : よく使用する場所をファイル ダイアログ ボックスに追加する | Microsoft Docs"
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
  - "よく使用する場所をダイアログ ボックスに"
  - "追加 (よく使用する場所をダイアログ ボックスに)"
  - "CustomPlaces コレクション"
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : よく使用する場所をファイル ダイアログ ボックスに追加する
既定値が開き、保存 ダイアログ ボックス[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] ダイアログ ボックスの左側にある領域がある**お気に入りリンク**します。 この領域には、カスタムの場所は呼び出されます。 <xref:System.Windows.Forms.OpenFileDialog>と<xref:System.Windows.Forms.SaveFileDialog>クラスを使用すると、フォルダーを追加、 <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>コレクションです。  
  
> [!NOTE]
>  カスタムの場所に表示するために、 <xref:System.Windows.Forms.OpenFileDialog>または<xref:System.Windows.Forms.SaveFileDialog>、 <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>にプロパティを設定する必要があります`true`(既定値)。  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>ファイル ダイアログ ボックスに、よく使用する場所を追加するには  
  
-   既知のフォルダー GUID を使用して、パスを追加または<xref:System.Windows.Forms.FileDialogCustomPlace>オブジェクトを<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>  ダイアログ ボックスのコレクション。  
  
     次のコード例では、パスを追加する方法を示します。  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.FileDialog>   
 <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=fullName>   
 [ファイル ダイアログ ボックスのカスタム プレイス用既知のフォルダー Guid](../../../../docs/framework/winforms/controls/known-folder-guids-for-file-dialog-custom-places.md)