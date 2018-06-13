---
title: 'チュートリアル : ElementHost コントロールの別の Windows フォームへのコピーと貼り付け'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
ms.openlocfilehash: 1cce981e4cb04ab6ed6ed41e0afac0121b242761
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520943"
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a>チュートリアル : ElementHost コントロールの別の Windows フォームへのコピーと貼り付け
このチュートリアルでは、Windows フォーム間で Windows Presentation Foundation (WPF) コントロールをコピーする方法について説明します。  
  
 このチュートリアルでは次のタスクを実行します。  
  
-   プロジェクトを作成する。  
  
-   WPF コントロールをコピーする。  
  
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
  
-   Visual Basic または Visual c# のという名前で新しい Windows フォーム アプリケーション プロジェクトを作成`CopyElementHost`です。  
  
## <a name="copying-a-wpf-control"></a>WPF コントロールのコピー  
 プロジェクトに WPF コントロールを追加した後、プロジェクト内の他のフォームにコピーすることができます。  
  
#### <a name="to-copy-a-wpf-control"></a>WPF コントロールをコピーするには  
  
1.  新しい WPF <xref:System.Windows.Controls.UserControl> プロジェクトをソリューションに追加します。 コントロール型の既定の名前である `UserControl1.xaml` を使用します。 詳細については、次を参照してください。[チュートリアル: 新しい WPF コンテンツの作成デザイン時に Windows フォームで](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)です。  
  
2.  プロジェクトをビルドします。  
  
3.  Windows フォーム デザイナーで `Form1` を開きます。  
  
4.  **ツールボックス**のインスタンスをドラッグ`UserControl1`フォーム上にします。  
  
     `UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。  
  
5.  `elementHost1` を選択して、CTRL + C キーを押してクリップボードにコピーします。  
  
6.  新しい Windows フォームをプロジェクトに追加します。 フォームの種類の既定の名前である `Form2` を使用します。  
  
7.  Windows フォーム デザイナーで `Form2` を開いたまま、CTRL キーを押しながら V キーを押して、`elementHost1` のコピーをフォームに貼り付けます。  
  
     `Form2` クラスのプライベート フィールドであるため、コピーしたコントロールの名前も `elementHost1` です。 `Form1` クラスの `elementHost1` には名前の競合がありません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [WPF コントロールの使用](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [WPF デザイナー](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
