---
title: 各 Windows フォーム コントロールのラベル設定とショートカットの作成
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- shortcuts [Windows Forms], controls
- keyboard shortcuts [Windows Forms], controls
- Windows Forms controls, labels
ms.assetid: 6eaf868c-819f-4131-8f59-048e20c286f7
ms.openlocfilehash: 0b75a4f59cdba4ff732a92996086b77bc65cf46c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them"></a><span data-ttu-id="c98ed-102">各 Windows フォーム コントロールのラベル設定とショートカットの作成</span><span class="sxs-lookup"><span data-stu-id="c98ed-102">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>
<span data-ttu-id="c98ed-103">Windows フォームに追加されたコントロールには、ユーザー操作をさらに特殊化するために使用されるプロパティとメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="c98ed-103">Controls added to Windows Forms have properties and methods that are used to further specialize the user experience.</span></span> <span data-ttu-id="c98ed-104">ユーザーのニーズに合わせてユーザー インターフェイスをカスタマイズすることは、適切に設計された Windows アプリケーションにおいて非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="c98ed-104">Customizing your user interface to suit the needs of the user is extremely important for well-designed Windows applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c98ed-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c98ed-105">In This Section</span></span>  
 [<span data-ttu-id="c98ed-106">方法: Windows フォーム コントロールによって表示されるテキストを設定する</span><span class="sxs-lookup"><span data-stu-id="c98ed-106">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 <span data-ttu-id="c98ed-107">コントロールにテキスト ラベルを割り当てる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c98ed-107">Describes how to assign a text label to a control.</span></span>  
  
 [<span data-ttu-id="c98ed-108">方法: Windows フォーム コントロールによって表示されるイメージを設定する</span><span class="sxs-lookup"><span data-stu-id="c98ed-108">How to: Set the Image Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)  
 <span data-ttu-id="c98ed-109">イメージを表示するためのコントロールを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c98ed-109">Explains how to configure a control to display images.</span></span>  
  
 [<span data-ttu-id="c98ed-110">方法: Windows フォーム コントロールのアクセス キーを作成する</span><span class="sxs-lookup"><span data-stu-id="c98ed-110">How to: Create Access Keys for Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 <span data-ttu-id="c98ed-111">定義済みのキーボード ショートカットを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c98ed-111">Gives information about creating predefined keyboard shortcuts.</span></span>  
  
 [<span data-ttu-id="c98ed-112">Windows フォーム上のコントロールのユーザー補助情報の提供</span><span class="sxs-lookup"><span data-stu-id="c98ed-112">Providing Accessibility Information for Controls on a Windows Form</span></span>](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md)  
 <span data-ttu-id="c98ed-113">コントロールでユーザー補助機能を使用できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c98ed-113">Gives information about enabling your controls to work with accessibility aids.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c98ed-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c98ed-114">Related Sections</span></span>  
 [<span data-ttu-id="c98ed-115">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="c98ed-115">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 <span data-ttu-id="c98ed-116">コントロールを使用して実行できる、その他の基本的な項目へのリンク。</span><span class="sxs-lookup"><span data-stu-id="c98ed-116">Links to other basic things you can do with controls.</span></span>  
  
 <span data-ttu-id="c98ed-117">参照してください[する方法: 作成アクセス キーの Windows フォーム コントロールを使用して、デザイナー](http://msdn.microsoft.com/library/ms233673\(v=vs.110\))、[する方法: デザイナーを使用して Windows フォーム コントロールによって表示されるテキストを設定](http://msdn.microsoft.com/library/ms233665\(v=vs.110\))、[する方法: イメージを設定によって表示される Windows フォーム デザイナーを使用してコントロール](http://msdn.microsoft.com/library/ms233656\(v=vs.110\))です。</span><span class="sxs-lookup"><span data-stu-id="c98ed-117">Also see [How to: Create Access Keys for Windows Forms Controls Using the Designer](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [How to: Set the Text Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [How to: Set the Image Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).</span></span>
