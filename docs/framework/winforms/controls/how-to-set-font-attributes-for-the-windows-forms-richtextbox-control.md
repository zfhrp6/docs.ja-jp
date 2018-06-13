---
title: '方法: Windows フォームの RichTextBox コントロールのフォント属性を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
ms.openlocfilehash: 7c4c9362bb5a32bd8d5afc2b1edeb935d505fd19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533644"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a><span data-ttu-id="64a78-102">方法: Windows フォームの RichTextBox コントロールのフォント属性を設定する</span><span class="sxs-lookup"><span data-stu-id="64a78-102">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="64a78-103">Windows フォーム<xref:System.Windows.Forms.RichTextBox>コントロールが、表示されるテキストを書式設定するためのさまざまなオプションです。</span><span class="sxs-lookup"><span data-stu-id="64a78-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="64a78-104">ことができます、選択した文字太字、下線、または斜体などを使用して、<xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="64a78-104">You can make the selected characters bold, underlined, or italic, using the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property.</span></span> <span data-ttu-id="64a78-105">また、このプロパティを使用して、選択した文字のサイズと書体を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="64a78-105">You can also use this property to change the size and typeface of the selected characters.</span></span> <span data-ttu-id="64a78-106"><xref:System.Windows.Forms.RichTextBox.SelectionColor%2A>プロパティでは、選択した文字の色を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="64a78-106">The <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property enables you to change the selected characters' color.</span></span>  
  
### <a name="to-change-the-appearance-of-characters"></a><span data-ttu-id="64a78-107">文字の外観を変更するには</span><span class="sxs-lookup"><span data-stu-id="64a78-107">To change the appearance of characters</span></span>  
  
1.  <span data-ttu-id="64a78-108">設定、<xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>プロパティを適切なフォントです。</span><span class="sxs-lookup"><span data-stu-id="64a78-108">Set the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property to an appropriate font.</span></span>  
  
     <span data-ttu-id="64a78-109">ユーザーにアプリケーションでのフォント ファミリ、サイズ、およびフォントの設定を有効にするのには通常使用する、<xref:System.Windows.Forms.FontDialog>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="64a78-109">To enable users to set the font family, size, and typeface in an application, you would typically use the <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="64a78-110">概要については、「[FontDialog Component Overview](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md)」 (FontDialog コンポーネントの概要) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64a78-110">For an overview, see [FontDialog Component Overview](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="64a78-111">設定、<xref:System.Windows.Forms.RichTextBox.SelectionColor%2A>プロパティを適切な色にします。</span><span class="sxs-lookup"><span data-stu-id="64a78-111">Set the <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property to an appropriate color.</span></span>  
  
     <span data-ttu-id="64a78-112">アプリケーションで色を設定するユーザーを有効にするのには通常使用する、<xref:System.Windows.Forms.ColorDialog>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="64a78-112">To enable users to set the color in an application, you would typically use the <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="64a78-113">概要については、「[ColorDialog Component Overview](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)」 (ColorDialog コンポーネントの概要) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64a78-113">For an overview, see [ColorDialog Component Overview](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).</span></span>  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="64a78-114">これらのプロパティは選択したテキストにのみ影響します。テキストが選択されていない場合は、現在の挿入ポイントの場所に入力されるテキストに影響します。</span><span class="sxs-lookup"><span data-stu-id="64a78-114">These properties only affect selected text, or, if no text is selected, the text that is typed at the current location of the insertion point.</span></span> <span data-ttu-id="64a78-115">プログラムによってテキストを選択する方法の詳細については、次を参照してください。<xref:System.Windows.Forms.TextBoxBase.Select%2A>です。</span><span class="sxs-lookup"><span data-stu-id="64a78-115">For information on selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64a78-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="64a78-116">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="64a78-117">RichTextBox コントロール</span><span class="sxs-lookup"><span data-stu-id="64a78-117">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="64a78-118">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="64a78-118">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
