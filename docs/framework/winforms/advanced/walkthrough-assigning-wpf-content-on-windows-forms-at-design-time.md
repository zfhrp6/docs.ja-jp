---
title: "チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの割り当て"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93ff6f39f4d8bcdd037d373f8bd26cbb3c32c125
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a>チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの割り当て
このチュートリアルでは、フォームに表示する Windows Presentation Foundation (WPF) コントロール型を選択する方法について説明します。 プロジェクトに含まれている WPF コントロール型であれば、どれでも選択できます。  
  
 このチュートリアルでは次のタスクを実行します。  
  
-   プロジェクトを作成する。  
  
-   WPF コントロール型を作成する。  
  
-   WPF コントロールを選択する。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 まず、Windows フォーム プロジェクトを作成します。  
  
> [!NOTE]
>  WPF コンテンツをホストする場合は、C# プロジェクトと Visual Basic プロジェクトのみがサポートされます。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
-   Visual Basic または Visual c# のという名前で新しい Windows フォーム アプリケーション プロジェクトを作成`SelectingWpfContent`です。  
  
## <a name="creating-the-wpf-control-types"></a>WPF コントロール型の作成  
 プロジェクトに追加した WPF コントロール型は、さまざまな <xref:System.Windows.Forms.Integration.ElementHost> コントロール内でホストできます。  
  
#### <a name="to-create-wpf-control-types"></a>WPF コントロール型を作成するには  
  
1.  新しい WPF <xref:System.Windows.Controls.UserControl> プロジェクトをソリューションに追加します。 コントロール型の既定の名前である `UserControl1.xaml` を使用します。 詳細については、次を参照してください。[チュートリアル: 新しい WPF コンテンツの作成デザイン時に Windows フォームで](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)です。  
  
2.  デザイン ビューで `UserControl1` が選択されていることを確認します。 詳細については、次を参照してください。[する方法: Select およびデザイン サーフェイス上の要素の移動](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474)です。  
  
3.  **プロパティ**ウィンドウで、設定の値、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティ`200`です。  
  
4.  追加、<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>コントロールを<xref:System.Windows.Controls.UserControl>の値を設定し、<xref:System.Windows.Controls.TextBox.Text%2A>プロパティを**ホストするコンテンツの**します。  
  
5.  WPF <xref:System.Windows.Controls.UserControl> をプロジェクトにもう 1 つ追加します。 コントロール型の既定の名前である `UserControl2.xaml` を使用します。  
  
6.  **プロパティ**ウィンドウで、設定の値、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティ`200`です。  
  
7.  追加、<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>コントロールを<xref:System.Windows.Controls.UserControl>の値を設定し、<xref:System.Windows.Controls.TextBox.Text%2A>プロパティを**Hosted Content 2**です。  
  
 **注**一般より高度な WPF コンテンツをホストする必要があります。 ここでは、説明する目的でのみ <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> コントロールを使用しています。  
  
1.  プロジェクトをビルドします。  
  
## <a name="selecting-wpf-controls"></a>WPF コントロールの選択  
 既にコンテンツをホストしている <xref:System.Windows.Forms.Integration.ElementHost> コントロールに異なる WPF コンテンツを割り当てることができます。  
  
#### <a name="to-select-wpf-controls"></a>WPF コントロールを選択するには  
  
1.  Windows フォーム デザイナーで `Form1` を開きます。  
  
2.  **ツールボックス**をダブルクリックして`UserControl1`のインスタンスを作成する`UserControl1`フォームにします。  
  
     `UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。  
  
3.  スマート タグ パネルで`elementHost1`を開き、 **ホストするコンテンツ**ドロップダウン リスト。  
  
4.  選択**[usercontrol2]**ドロップダウン リスト ボックスからです。  
  
     これで、`elementHost1` コントロールが `UserControl2` 型のインスタンスをホストするようになりました。  
  
5.  **プロパティ**ウィンドウ、いることを確認、<xref:System.Windows.Forms.Integration.ElementHost.Child%2A>プロパティに設定されている**[usercontrol2]**です。  
  
6.  **ツールボックス**で、 **WPF 相互運用性**グループで、ドラッグ、<xref:System.Windows.Forms.Integration.ElementHost>コントロールをフォームにします。  
  
     新しい名前として、このコントロールの既定である `elementHost2` を使用します。  
  
7.  スマート タグ パネルで`elementHost2`を開き、 **ホストするコンテンツ**ドロップダウン リスト。  
  
8.  選択**UserControl1**ドロップダウン リストからです。  
  
9. これで、`elementHost2` コントロールが `UserControl1` 型のインスタンスをホストするようになりました。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [WPF コントロールの使用](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [WPF デザイナー](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
