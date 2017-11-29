---
title: "方法 : コントロール クラスを継承する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 75b9c56d2d9df80745cec2b811c39f5e438d07c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="89122-102">方法 : コントロール クラスを継承する</span><span class="sxs-lookup"><span data-stu-id="89122-102">How to: Inherit from the Control Class</span></span>
<span data-ttu-id="89122-103">Windows フォームで使用する完全なカスタム コントロールを作成する場合から継承する必要があります、<xref:System.Windows.Forms.Control>クラスです。</span><span class="sxs-lookup"><span data-stu-id="89122-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="89122-104">継承するときに、<xref:System.Windows.Forms.Control>を計画および実装の詳細を実行するオプションを提供するオプションの最大範囲とクラスが必要です。</span><span class="sxs-lookup"><span data-stu-id="89122-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="89122-105">継承する場合<xref:System.Windows.Forms.Control>コントロールの動作を実現する非常に基本的な機能を継承します。</span><span class="sxs-lookup"><span data-stu-id="89122-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="89122-106">本来の機能、<xref:System.Windows.Forms.Control>クラス、キーボードとマウスを介してユーザー入力の処理、境界とコントロールのサイズを定義、windows ハンドルを提供およびメッセージの処理とセキュリティを提供します。</span><span class="sxs-lookup"><span data-stu-id="89122-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="89122-107">描画機能 (ここではコントロールのグラフィカル インターフェイスを実際に表示する機能) や、ユーザーとやり取りするための特定の機能は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="89122-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="89122-108">このような機能はすべて、カスタム コードによって提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89122-108">You must provide all of these aspects through custom code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89122-109">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="89122-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="89122-110">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89122-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="89122-111">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89122-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-custom-control"></a><span data-ttu-id="89122-112">カスタム コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="89122-112">To create a custom control</span></span>  
  
1.  <span data-ttu-id="89122-113">新しい **Windows アプリケーション** プロジェクトまたは **Windows コントロール ライブラリ** プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="89122-113">Create a new **Windows Application** or **Windows Control Library** project.</span></span>  
  
2.  <span data-ttu-id="89122-114">**[プロジェクト]** メニューの **[クラスの追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="89122-114">From the **Project** menu, choose **Add Class**.</span></span>  
  
3.  <span data-ttu-id="89122-115">**[新しい項目の追加]** ダイアログ ボックスの **[カスタム コントロール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="89122-115">In the **Add New Item** dialog box, click **Custom Control**.</span></span>  
  
     <span data-ttu-id="89122-116">新しいカスタム コントロールがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="89122-116">A new custom control is added to your project.</span></span>  
  
4.  <span data-ttu-id="89122-117">F7 キーを押して、カスタム コントロールの**コード エディター**を開きます。</span><span class="sxs-lookup"><span data-stu-id="89122-117">Press F7 to open the **Code Editor** for your custom control.</span></span>  
  
5.  <span data-ttu-id="89122-118">検索、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドの呼び出しを除く空になります、<xref:System.Windows.Forms.Control.OnPaint%2A>基底クラスのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="89122-118">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>  
  
6.  <span data-ttu-id="89122-119">コントロールで使用するカスタム描画が組み込まれるように、コードを修正します。</span><span class="sxs-lookup"><span data-stu-id="89122-119">Modify the code to incorporate any custom painting you want for your control.</span></span>  
  
     <span data-ttu-id="89122-120">コントロールのグラフィックスをレンダリングするコードの記述については、「[コントロールのカスタム描画およびレンダリング](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89122-120">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span></span>  
  
7.  <span data-ttu-id="89122-121">コントロールに組み込むカスタム メソッド、カスタム プロパティ、カスタム イベントを実装します。</span><span class="sxs-lookup"><span data-stu-id="89122-121">Implement any custom methods, properties, or events that your control will incorporate.</span></span>  
  
8.  <span data-ttu-id="89122-122">コントロールを保存して、動作確認を行います。</span><span class="sxs-lookup"><span data-stu-id="89122-122">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89122-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="89122-123">See Also</span></span>  
 [<span data-ttu-id="89122-124">さまざまなカスタム コントロール</span><span class="sxs-lookup"><span data-stu-id="89122-124">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="89122-125">方法: UserControl クラスを継承する</span><span class="sxs-lookup"><span data-stu-id="89122-125">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [<span data-ttu-id="89122-126">方法: 既存の Windows フォーム コントロールから継承する</span><span class="sxs-lookup"><span data-stu-id="89122-126">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [<span data-ttu-id="89122-127">方法: Windows フォームのコントロールを作成する</span><span class="sxs-lookup"><span data-stu-id="89122-127">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="89122-128">Visual Basic での継承されたイベント ハンドラーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="89122-128">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [<span data-ttu-id="89122-129">デザイン時の Windows フォーム コントロールの開発</span><span class="sxs-lookup"><span data-stu-id="89122-129">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
