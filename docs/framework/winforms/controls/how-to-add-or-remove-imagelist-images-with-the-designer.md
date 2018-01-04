---
title: "方法 : デザイナーを使って ImageList イメージを追加または削除する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 05dd1e06c2cba31bca1282e8d409ab1b5610d1dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="55380-102">方法 : デザイナーを使って ImageList イメージを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="55380-102">How to: Add or Remove ImageList Images with the Designer</span></span>
<span data-ttu-id="55380-103">イメージを追加することができます、<xref:System.Windows.Forms.ImageList>コンポーネントいくつかの方法です。</span><span class="sxs-lookup"><span data-stu-id="55380-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="55380-104">関連付けられているスマート タグを使用してイメージを非常に迅速に追加することができます、 <xref:System.Windows.Forms.ImageList>、やの他のいくつかのプロパティを設定する場合、 <xref:System.Windows.Forms.ImageList>、[プロパティ] ウィンドウにイメージを追加する方が便利見つけることがあります。</span><span class="sxs-lookup"><span data-stu-id="55380-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="55380-105">コードを使用してイメージを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="55380-105">You can also add images by using code.</span></span> <span data-ttu-id="55380-106">コードでイメージを追加する方法の詳細については、次を参照してください。[する方法: 追加または削除する Windows フォームの ImageList コンポーネントにイメージを](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)です。</span><span class="sxs-lookup"><span data-stu-id="55380-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="55380-107">設定する通常、<xref:System.Windows.Forms.ImageList>コンポーネントはイメージ コントロールに関連付けられているが、これは必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="55380-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55380-108">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="55380-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="55380-109">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55380-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="55380-110">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55380-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="55380-111">追加またはプロパティ ウィンドウを使用してイメージを削除するには</span><span class="sxs-lookup"><span data-stu-id="55380-111">To add or remove images by using the Properties window</span></span>  
  
1.  <span data-ttu-id="55380-112">選択、<xref:System.Windows.Forms.ImageList>コンポーネントやフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="55380-112">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2.  <span data-ttu-id="55380-113">[プロパティ] ウィンドウで、省略記号ボタンをクリックします (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) の横に、<xref:System.Windows.Forms.ImageList.Images%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="55380-113">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
3.  <span data-ttu-id="55380-114">**イメージ コレクション エディター**をクリックして**追加**または**削除**を追加または一覧からイメージを削除します。</span><span class="sxs-lookup"><span data-stu-id="55380-114">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="55380-115">スマート タグを使用してイメージを追加または削除</span><span class="sxs-lookup"><span data-stu-id="55380-115">To add or remove images using the smart tag</span></span>  
  
1.  <span data-ttu-id="55380-116">選択、<xref:System.Windows.Forms.ImageList>コンポーネントやフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="55380-116">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2.  <span data-ttu-id="55380-117">スマート タグ グリフをクリックして (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span><span class="sxs-lookup"><span data-stu-id="55380-117">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>  
  
3.  <span data-ttu-id="55380-118">**ImageList タスク**ダイアログ ボックスで、 **イメージ**です。</span><span class="sxs-lookup"><span data-stu-id="55380-118">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>  
  
4.  <span data-ttu-id="55380-119">**イメージ コレクション エディター**  をクリックして**追加**または**削除**を追加または一覧からイメージを削除します。</span><span class="sxs-lookup"><span data-stu-id="55380-119">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55380-120">参照</span><span class="sxs-lookup"><span data-stu-id="55380-120">See Also</span></span>  
 [<span data-ttu-id="55380-121">イメージ、ビットマップ、メタファイル</span><span class="sxs-lookup"><span data-stu-id="55380-121">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="55380-122">チュートリアル: Windows フォーム コントロールのスマート タグを使用した共通タスクの実行</span><span class="sxs-lookup"><span data-stu-id="55380-122">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 [<span data-ttu-id="55380-123">ImageList コンポーネント</span><span class="sxs-lookup"><span data-stu-id="55380-123">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
