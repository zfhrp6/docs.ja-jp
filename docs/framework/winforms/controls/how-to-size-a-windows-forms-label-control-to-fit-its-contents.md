---
title: '方法 : Windows フォーム Label コントロールのサイズを内容に合わせて変更する'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: e067966b606d77ceb9d11d2784c0d5f73ad332a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533729"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="fca24-102">方法 : Windows フォーム Label コントロールのサイズを内容に合わせて変更する</span><span class="sxs-lookup"><span data-stu-id="fca24-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="fca24-103">Windows フォーム<xref:System.Windows.Forms.Label>コントロールは、単一行または複数の行を指定できますしたりできるか、固定サイズで、キャプション、それに合わせて自体を自動的に変更できます。</span><span class="sxs-lookup"><span data-stu-id="fca24-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="fca24-104"><xref:System.Windows.Forms.Label.AutoSize%2A>プロパティは、拡大または縮小のキャプションに合わせてコントロールのサイズが、実行時に、キャプションが変更される場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="fca24-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="fca24-105">内容に合わせて動的にサイズを変更するラベル コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="fca24-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1.  <span data-ttu-id="fca24-106">設定の<xref:System.Windows.Forms.Label.AutoSize%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="fca24-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="fca24-107">場合<xref:System.Windows.Forms.Label.AutoSize%2A>に設定されている`false`、指定した単語、<xref:System.Windows.Forms.Label.Text%2A>プロパティは、可能であれば、次の行に折り返されますが、コントロールは拡張されません。</span><span class="sxs-lookup"><span data-stu-id="fca24-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fca24-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="fca24-108">See Also</span></span>  
 [<span data-ttu-id="fca24-109">方法: Windows フォームの Label コントロールでアクセス キーを作成する</span><span class="sxs-lookup"><span data-stu-id="fca24-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [<span data-ttu-id="fca24-110">Label コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="fca24-110">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="fca24-111">Label コントロール</span><span class="sxs-lookup"><span data-stu-id="fca24-111">Label Control</span></span>](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
