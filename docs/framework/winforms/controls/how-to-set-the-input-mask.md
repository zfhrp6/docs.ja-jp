---
title: '方法 : 定型入力を設定する'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 6f554c239e3444db5f6ac84f7994108ac70df0a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="afa9f-102">方法 : 定型入力を設定する</span><span class="sxs-lookup"><span data-stu-id="afa9f-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="afa9f-103">マスクされたテキスト ボックス コントロールは、承認または拒否するユーザー入力の宣言の構文をサポートする高度なテキスト ボックス コントロールです。</span><span class="sxs-lookup"><span data-stu-id="afa9f-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="afa9f-104">マスクのプロパティの設定によって、アプリケーションで任意のカスタム検証ロジックを記述することがなく、許容されるユーザー入力を指定できます。</span><span class="sxs-lookup"><span data-stu-id="afa9f-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="afa9f-105">詳細については、の「解説」セクションを参照してください、<xref:System.Windows.Forms.MaskedTextBox>クラスです。</span><span class="sxs-lookup"><span data-stu-id="afa9f-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="afa9f-106">手動で、マスクのプロパティを設定</span><span class="sxs-lookup"><span data-stu-id="afa9f-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="afa9f-107">Mask プロパティをサポートする文字に精通場合は、手動で入力することができます。</span><span class="sxs-lookup"><span data-stu-id="afa9f-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="afa9f-108">概要については、マスクのプロパティをサポートする文字のの「解説」セクションを参照してください、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="afa9f-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
#### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="afa9f-109">手動で、マスクのプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="afa9f-109">To set the Mask property manually</span></span>  
  
1.  <span data-ttu-id="afa9f-110">**デザイン**ビューで、<xref:System.Windows.Forms.MaskedTextBox>です。</span><span class="sxs-lookup"><span data-stu-id="afa9f-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2.  <span data-ttu-id="afa9f-111">**プロパティ**ウィンドウで、検索、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="afa9f-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3.  <span data-ttu-id="afa9f-112">設定するマスクを入力します。</span><span class="sxs-lookup"><span data-stu-id="afa9f-112">Type the mask that you want.</span></span> <span data-ttu-id="afa9f-113">たとえば、「`###`です。</span><span class="sxs-lookup"><span data-stu-id="afa9f-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="afa9f-114">[定型入力] ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="afa9f-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="afa9f-115">[定型入力] ダイアログ ボックスでは、いくつかの定義済みの入力マスクを提供します。</span><span class="sxs-lookup"><span data-stu-id="afa9f-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="afa9f-116">定義済みのマスクを変更したり、独自のマスクを手動で入力できます。</span><span class="sxs-lookup"><span data-stu-id="afa9f-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
#### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="afa9f-117">[定型入力] ダイアログ ボックスを開く</span><span class="sxs-lookup"><span data-stu-id="afa9f-117">To open the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="afa9f-118">**デザイン**ビューで、<xref:System.Windows.Forms.MaskedTextBox>です。</span><span class="sxs-lookup"><span data-stu-id="afa9f-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1.  <span data-ttu-id="afa9f-119">開くには、スマート タグをクリックして、 **MaskedTextBox タスク**パネルです。</span><span class="sxs-lookup"><span data-stu-id="afa9f-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2.  <span data-ttu-id="afa9f-120">をクリックして**マスクを設定する**です。</span><span class="sxs-lookup"><span data-stu-id="afa9f-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="afa9f-121">\- または -</span><span class="sxs-lookup"><span data-stu-id="afa9f-121">\- or -</span></span>  
  
    1.  <span data-ttu-id="afa9f-122">**プロパティ**ウィンドウで、<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="afa9f-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2.  <span data-ttu-id="afa9f-123">プロパティ値 列にある省略記号ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="afa9f-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="afa9f-124">**定型入力** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="afa9f-124">The **Input Mask** dialog box appears.</span></span>  
  
#### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="afa9f-125">[定型入力] ダイアログ ボックスを使用するには</span><span class="sxs-lookup"><span data-stu-id="afa9f-125">To use the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="afa9f-126">(省略可能)一覧で定義済みのマスクのいずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="afa9f-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2.  <span data-ttu-id="afa9f-127">(省略可能)定義済みのマスクを編集、**マスク**ボックス。</span><span class="sxs-lookup"><span data-stu-id="afa9f-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3.  <span data-ttu-id="afa9f-128">(省略可能)新しいマスクを入力、**マスク**ボックス。</span><span class="sxs-lookup"><span data-stu-id="afa9f-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="afa9f-129">定義済みのマスクのいずれかを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="afa9f-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="afa9f-130">[プレビュー] ボックスでユーザーに表示される文字が表示されます、<xref:System.Windows.Forms.MaskedTextBox>です。</span><span class="sxs-lookup"><span data-stu-id="afa9f-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="afa9f-131">これらの文字に役立つガイドをユーザーがデータを正しく入力します。</span><span class="sxs-lookup"><span data-stu-id="afa9f-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4.  <span data-ttu-id="afa9f-132">オンまたはオフにして、**使用 ValidatingType**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="afa9f-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="afa9f-133">**使用 ValidatingType**  チェック ボックスは、データ型は、ユーザーがデータ入力の検証に使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="afa9f-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="afa9f-134">詳細については、<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> プロパティを参照してください。</span><span class="sxs-lookup"><span data-stu-id="afa9f-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5.  <span data-ttu-id="afa9f-135">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="afa9f-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="afa9f-136">マスクは、入力、**マスク**プロパティに、**プロパティ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="afa9f-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa9f-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="afa9f-137">See Also</span></span>  
 [<span data-ttu-id="afa9f-138">チュートリアル: MaskedTextBox コントロールの使用</span><span class="sxs-lookup"><span data-stu-id="afa9f-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)
