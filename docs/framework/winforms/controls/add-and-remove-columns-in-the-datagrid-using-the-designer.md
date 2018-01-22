---
title: "方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fdb57cf2134ee4f221a26db61cfdcc48dc92548
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する
Windows フォーム<xref:System.Windows.Forms.DataGridView>コントロールは、データを表示するために列を含める必要があります。 コントロールを手動で設定する場合は、する必要があります自分自身を追加する列。 代わりに、コントロールを生成し、列を自動的に設定するデータ ソースにバインドできます。 データ ソースを表示する数より多い列が含まれている場合は、不要な列を削除することができます。  
  
 次の手順が必要な**Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.DataGridView>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-add-a-column-using-the-designer"></a>デザイナーを使用して列を追加するには  
  
1.  スマート タグ グリフをクリックして (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) の右上隅で、<xref:System.Windows.Forms.DataGridView>を制御し、**列の追加**です。  
  
2.  **列の追加** ダイアログ ボックスで、選択、**データ バインド列**オプションし、データ ソースから列を選択するかを選択して、**非バインド列**オプションし、列の定義指定されたフィールドを使用します。  
  
3.  クリックして、**追加**を既存の列は既に埋まらない場合コントロールの表示領域に、デザイナーに表示する列を追加するボタンをクリックします。  
  
    > [!NOTE]
    >  列のプロパティを変更することができます、**列の編集** ダイアログ ボックスは、コントロールのスマート タグからアクセスできます。  
  
### <a name="to-remove-a-column-using-the-designer"></a>デザイナーを使用して列を削除するには  
  
1.  選択**列の編集**コントロールのスマート タグからです。  
  
2.  列を選択して、**選択されている列** ボックスの一覧です。  
  
3.  をクリックして、**削除**ボタンに、デザイナーに表示されなくなった原因の列を削除します。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.DataGridView>  
 [方法: Windows アプリケーション プロジェクトの作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [方法: Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
