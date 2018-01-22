---
title: "方法 : Windows フォームにコントロールを固定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ceaacc250d48e7199d7224f95aa91ed976c097e0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>方法 : Windows フォームにコントロールを固定する
実行時にサイズを変更できるユーザーをフォームをデザインする場合、フォーム上のコントロールがサイズし、位置を正しくです。 使用することができますが、フォームを動的にコントロールのサイズを変更するには、 <xref:System.Windows.Forms.Control.Anchor%2A> Windows フォーム コントロールのプロパティです。 <xref:System.Windows.Forms.Control.Anchor%2A>プロパティがコントロールの固定位置を定義します。 フォームにコントロールを固定すると、フォームのサイズが、コントロールは、コントロールと、アンカー位置の間の距離を保持します。 ある場合など、<xref:System.Windows.Forms.TextBox>フォームのサイズを変更、左、右、およびフォームの下端が固定されるコントロール、<xref:System.Windows.Forms.TextBox>フォームの横の右側と左側からの距離が維持されるため、水平方向にサイズ変更を制御します。 さらに、コントロール配置自体垂直方向にその場所は、フォームの下部エッジからの距離では常にできるようにします。 コントロールが固定されていないと、フォームのサイズが、フォームの端を基準としたコントロールの位置が変更されました。  
  
 <xref:System.Windows.Forms.Control.Anchor%2A>プロパティの対話、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティです。 詳細については、次を参照してください。 [AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-anchor-a-control-on-a-form"></a>フォーム上のコントロールを固定するには  
  
1.  固定するコントロールを選択します。  
  
    > [!NOTE]
    >  CTRL キーを押し、して選択し、各コントロールをクリックし、この手順の残りの部分で同時に複数のコントロールを固定できます。  
  
2.  **プロパティ** ウィンドウの右側の矢印をクリックして、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティです。  
  
     クロス エディターが表示されます。  
  
3.  アンカーを設定するには、左上、右、またはクロスの下部のセクションをクリックします。  
  
     コントロール、ページのトップへと左に固定既定です。  
  
4.  固定されているコントロールの辺をクリアするには、その arm クロスをクリックします。  
  
5.  閉じるには、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティ エディターをクリックして、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティ名をもう一度です。  
  
 実行時に、フォームが表示されたら、フォームの端からの距離を保持するコントロールのサイズを変更します。 アンカーのエッジからの距離。 常に同じ距離は、Windows フォーム デザイナーでコントロールが配置されているときに定義されています。  
  
> [!NOTE]
>  などの特定のコントロール、<xref:System.Windows.Forms.ComboBox>の高さに制限されている、制御します。 フォームまたはコンテナーの最下位にコントロールを固定強制的にコントロールを制限された高さを高くことはできません。  
  
 継承されたコントロールがある必要があります`Protected`固定できるようにします。 コントロールのアクセス レベルを変更するには、次のように設定します。 その`Modifiers`プロパティに、**プロパティ**ウィンドウです。  
  
## <a name="see-also"></a>参照  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)  
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [方法: Windows フォーム上のコントロールをドッキングする](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [チュートリアル: FlowLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [チュートリアル: TableLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [チュートリアル : Padding、Margin、および AutoSize プロパティを使用した Windows フォーム コントロールのレイアウト](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
