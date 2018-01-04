---
title: "方法 : Windows フォームで Windows エクスプローラー スタイルのインターフェイスを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c30dd18e7303cf9fe913760da3f9dad7bca3c95
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>方法 : Windows フォームで Windows エクスプローラー スタイルのインターフェイスを作成する
Windows エクスプ ローラーは、準備ができて、使いやすさのためのアプリケーションの一般的なユーザー インターフェイス選択です。  
  
 Windows エクスプ ローラーは、基本的に、<xref:System.Windows.Forms.TreeView>コントロールと<xref:System.Windows.Forms.ListView>別のパネル上のコントロールです。 パネルは、スプリッターによってサイズ変更可能で行われます。 このコントロールの配置は、表示する情報と参照に対して非常に効果的です。  
  
 次の手順では、Windows エクスプ ローラーのようなフォームでコントロールを配置する方法を示します。 Windows エクスプ ローラーのアプリケーションのファイル参照機能を追加する方法には表示されません。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a>Windows エクスプ ローラー スタイルの Windows フォームを作成するには  
  
1.  新しい Windows アプリケーション プロジェクトを作成します。 詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  **ツールボックス**:  
  
    1.  ドラッグ、<xref:System.Windows.Forms.SplitContainer>コントロールをフォームにします。  
  
    2.  ドラッグ、<xref:System.Windows.Forms.TreeView>にコントロールを**SplitterPanel1** (のパネル、<xref:System.Windows.Forms.SplitContainer>マークされているコントロール**Panel1**)。  
  
    3.  ドラッグ、<xref:System.Windows.Forms.ListView>にコントロールを**SplitterPanel2** (のパネル、<xref:System.Windows.Forms.SplitContainer>マークされているコントロール**Panel2**)。  
  
3.  CTRL キーを押しながらクリックするとさらに、3 つすべてのコントロールを選択します。 選択した場合、<xref:System.Windows.Forms.SplitContainer>制御、パネルではなく、分割バーをクリックします。  
  
    > [!NOTE]
    >  使用しないで、**すべて選択**コマンドを**編集**メニュー。 これを行う場合、次の手順で必要なプロパティには表示されません、**プロパティ**ウィンドウです。  
  
4.  **プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.SplitContainer.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>です。  
  
5.  F5 キーを押してアプリケーションを実行します。  
  
     フォームには、Windows エクスプ ローラーのような 2 部構成のユーザー インターフェイスが表示されます。  
  
    > [!NOTE]
    >  分割線をドラッグすると、パネル サイズが変更されます。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.SplitContainer>  
 [方法: Windows フォームでマルチペイン ユーザー インターフェイスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [方法: 分割ウィンドウでのサイズ変更および位置指定動作を定義する](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [方法: ウィンドウを水平方向に分割する](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [SplitContainer コントロール](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
