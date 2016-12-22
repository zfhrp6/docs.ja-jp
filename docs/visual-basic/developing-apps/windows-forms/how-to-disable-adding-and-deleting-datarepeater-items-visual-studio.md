---
title: "How to: Disable Adding and Deleting DataRepeater Items (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, disabling delete"
  - "DataRepeater, disabling add"
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Disable Adding and Deleting DataRepeater Items (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

既定では、ユーザーは <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロール内の項目を追加および削除できます。  ユーザーは、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> にフォーカスがあるときに Ctrl キーを押しながら N キーを押すか、<xref:System.Windows.Forms.BindingNavigator> コントロールの **AddNewItem** ボタンをクリックして新しい項目を追加できます。  ユーザーは、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> にフォーカスがあるときに Del キーを押すか、<xref:System.Windows.Forms.BindingNavigator> コントロールの **DeleteItem** ボタンをクリックして項目を削除できます。  
  
 追加と削除の機能は、デザイン時または実行時に無効にできます。  
  
### デザイン時に追加と削除を無効にするには  
  
1.  Windows フォーム デザイナーで、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを選択します。  
  
    > [!NOTE]
    >  コントロールの下部セクションを選択する必要があります。  項目テンプレート セクションを選択している場合は、異なるプロパティ一式が表示されます。  
  
2.  \[プロパティ\] ウィンドウで、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> プロパティを **False** に設定します。  
  
3.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> プロパティを **False** に設定します。  
  
4.  Windows フォーム デザイナーで、<xref:System.Windows.Forms.BindingNavigator> コントロールを選択し、**AddNewItem** ボタン \(正符号が表示されているボタン\) をクリックします。  
  
5.  \[プロパティ\] ウィンドウで、<xref:System.Windows.Forms.ToolBarButton.Enabled%2A> プロパティを **False** に設定します。  
  
6.  Windows フォーム デザイナーで、<xref:System.Windows.Forms.BindingNavigator> コントロールを選択し、**DeleteItem** ボタン \(赤い X が表示されているボタン\) をクリックします。  
  
7.  \[プロパティ\] ウィンドウで、<xref:System.Windows.Forms.ToolBarButton.Enabled%2A> プロパティを **False** に設定します。  
  
8.  コンポーネント トレイで、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> がバインドされている <xref:System.Windows.Forms.BindingSource> を選択します。  
  
9. \[プロパティ\] ウィンドウで、<xref:System.Windows.Forms.BindingSource.AllowNew%2A> プロパティを **False** に設定します。  
  
10. Windows フォーム デザイナーで、**DeleteItem** ボタンをダブルクリックしてコード エディターを開きます。  
  
11. \[イベント\] ボックスの `BindingNavigatorDeleteItem_EnabledChanged` イベントをクリックします。  
  
12. `BindingNavigatorDeleteItem_EnabledChanged` イベント ハンドラーに次のコードを追加します。  
  
     [!code-cs[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  現在のレコードが変更されるたびに <xref:System.Windows.Forms.BindingSource> によって **DeleteItem** ボタンが有効になるため、この手順が必要となります。  
  
### 実行時に追加と削除を無効にするには  
  
1.  Windows フォーム デザイナーで、フォームをダブルクリックしてコード エディターを開きます。  
  
2.  `Form_Load` イベントに次のコードを追加します。  
  
     [!code-cs[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  `BindingNavigatorDeleteItem_EnabledChanged` イベント ハンドラーに次のコードを追加します。  
  
     [!code-cs[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  現在のレコードが変更されるたびに <xref:System.Windows.Forms.BindingSource> によって **DeleteItem** ボタンが有効になるため、この手順が必要となります。  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)