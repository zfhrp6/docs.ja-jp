---
title: '方法 : デザイン時に ElementHost コントロールをコピーして貼り付ける'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: 1a9938500287b3b44f13f0aa664da85b7fdb4675
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524856"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="0b55c-102">方法 : デザイン時に ElementHost コントロールをコピーして貼り付ける</span><span class="sxs-lookup"><span data-stu-id="0b55c-102">How to: Copy and Paste an ElementHost Control at Design Time</span></span>
<span data-ttu-id="0b55c-103">この手順では、Windows フォーム上の Windows Presentation Foundation (WPF) コントロールをコピーする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0b55c-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b55c-104">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0b55c-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0b55c-105">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0b55c-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0b55c-106">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b55c-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="0b55c-107">コピーして、デザイン時に ElementHost コントロールを貼り付ける</span><span class="sxs-lookup"><span data-stu-id="0b55c-107">To copy and paste an ElementHost control at design time</span></span>  
  
1.  <span data-ttu-id="0b55c-108">新しい WPF 追加<xref:System.Windows.Controls.UserControl>を Windows フォーム プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="0b55c-108">Add a new WPF <xref:System.Windows.Controls.UserControl> to your Windows Forms project.</span></span> <span data-ttu-id="0b55c-109">コントロール型の既定の名前である `UserControl1.xaml` を使用します。</span><span class="sxs-lookup"><span data-stu-id="0b55c-109">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="0b55c-110">詳細については、次を参照してください。[チュートリアル: 新しい WPF コンテンツの作成デザイン時に Windows フォームで](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)です。</span><span class="sxs-lookup"><span data-stu-id="0b55c-110">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="0b55c-111">**プロパティ**ウィンドウで、設定の値、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティの`UserControl1`に`200`です。</span><span class="sxs-lookup"><span data-stu-id="0b55c-111">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to `200`.</span></span>  
  
3.  <span data-ttu-id="0b55c-112"><xref:System.Windows.Controls.Control.Background%2A> プロパティの値を `Blue` に設定します。</span><span class="sxs-lookup"><span data-stu-id="0b55c-112">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
4.  <span data-ttu-id="0b55c-113">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="0b55c-113">Build the project.</span></span>  
  
5.  <span data-ttu-id="0b55c-114">Windows フォーム デザイナーで `Form1` を開きます。</span><span class="sxs-lookup"><span data-stu-id="0b55c-114">Open `Form1` in the Windows Forms Designer.</span></span>  
  
6.  <span data-ttu-id="0b55c-115">**ツールボックス**のインスタンスをドラッグ`UserControl1`フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="0b55c-115">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="0b55c-116">`UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。</span><span class="sxs-lookup"><span data-stu-id="0b55c-116">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
7.  <span data-ttu-id="0b55c-117">`elementHost1` を選択して、CTRL + C キーを押してクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0b55c-117">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
8.  <span data-ttu-id="0b55c-118">フォーム上にコピーしたコントロールを貼り付けるには、CTRL + V キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0b55c-118">Press CTRL+V to paste the copied control onto the form.</span></span>  
  
     <span data-ttu-id="0b55c-119">新しい<xref:System.Windows.Forms.Integration.ElementHost>という名前のコントロール`elementHost2`フォーム上に作成します。</span><span class="sxs-lookup"><span data-stu-id="0b55c-119">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b55c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b55c-120">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="0b55c-121">チュートリアル: ElementHost コントロールの別の Windows フォームへのコピーと貼り付け</span><span class="sxs-lookup"><span data-stu-id="0b55c-121">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 [<span data-ttu-id="0b55c-122">移行と相互運用性</span><span class="sxs-lookup"><span data-stu-id="0b55c-122">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="0b55c-123">WPF コントロールの使用</span><span class="sxs-lookup"><span data-stu-id="0b55c-123">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="0b55c-124">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="0b55c-124">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
