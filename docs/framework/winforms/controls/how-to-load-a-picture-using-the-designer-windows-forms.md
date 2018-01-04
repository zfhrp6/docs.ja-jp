---
title: "方法 : デザイナーを使用してピクチャを読み込む (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ca3e3eef1aa9e7414d3c279de5943585703bf9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>方法 : デザイナーを使用してピクチャを読み込む (Windows フォーム)
Windows フォームで<xref:System.Windows.Forms.PictureBox>コントロール、読み込みし、設定して、デザイン時にフォームに画像を表示できます、<xref:System.Windows.Forms.PictureBox.Image%2A>に有効な画像のプロパティです。 次の表は、使用可能なファイルの種類を示します。  
  
|型|ファイル名拡張子|  
|----------|-------------------------|  
|ビットマップ|.bmp|  
|アイコン|.ico|  
|GIF|.gif|  
|メタファイル|.wmf|  
|JPEG|.jpg|  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-display-a-picture-at-design-time"></a>デザイン時に画像を表示するには  
  
1.  描画、<xref:System.Windows.Forms.PictureBox>フォーム上のコントロールです。  
  
2.  プロパティ ウィンドウで、次のように選択します。、<xref:System.Windows.Forms.PictureBox.Image%2A>プロパティ、し、省略記号ボタンを表示をクリックして、**開く** ダイアログ ボックス。  
  
3.  特定のファイル タイプ (たとえば、.gif ファイルを探している場合にこれを選択、**ファイルの種類**ボックス。  
  
4.  表示するファイルを選択します。  
  
### <a name="to-clear-the-picture-at-design-time"></a>デザイン時に、画像を消去するには  
  
1.  **プロパティ**ウィンドウで、<xref:System.Windows.Forms.PictureBox.Image%2A>プロパティと、イメージ オブジェクトの名前の左側に表示される小さなのサムネイル画像を右クリックします。 選択**リセット**です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.PictureBox>  
 [PictureBox コントロールの概要](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [方法: 実行時にピクチャのサイズまたは配置を変更する](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [方法: 実行時にピクチャを設定する](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [PictureBox コントロール](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
