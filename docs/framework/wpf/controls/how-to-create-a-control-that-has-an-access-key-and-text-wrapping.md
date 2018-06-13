---
title: '方法 : アクセス キーおよびテキスト折り返し機能を持つコントロールを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
ms.openlocfilehash: 8343c660ddeb5487f46e87534e555936d1b86371
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553788"
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a><span data-ttu-id="d10f0-102">方法 : アクセス キーおよびテキスト折り返し機能を持つコントロールを作成する</span><span class="sxs-lookup"><span data-stu-id="d10f0-102">How to: Create a Control That Has an Access Key and Text Wrapping</span></span>
<span data-ttu-id="d10f0-103">この例では、アクセス キーがありテキスト折り返しをサポートするコントロールを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d10f0-103">This example shows how to create a control that has an access key and supports text wrapping.</span></span> <span data-ttu-id="d10f0-104">この例では、<xref:System.Windows.Controls.Label>これらの概念を説明するために管理します。</span><span class="sxs-lookup"><span data-stu-id="d10f0-104">The example uses a <xref:System.Windows.Controls.Label> control to illustrate these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d10f0-105">例</span><span class="sxs-lookup"><span data-stu-id="d10f0-105">Example</span></span>  
 <span data-ttu-id="d10f0-106">**ラベルにテキスト折り返し機能を追加する**</span><span class="sxs-lookup"><span data-stu-id="d10f0-106">**Add Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="d10f0-107"><xref:System.Windows.Controls.Label>コントロールがテキストの折り返しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d10f0-107">The <xref:System.Windows.Controls.Label> control does not support text wrapping.</span></span> <span data-ttu-id="d10f0-108">複数の行を折り返せるラベルが必要な場合には、テキスト折り返し機能をサポートしている別の要素を入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d10f0-108">If you need a label that wraps across multiple lines, you can nest another element that does support text wrapping and put the element inside the label.</span></span> <span data-ttu-id="d10f0-109">次の例を使用する方法を示しています、<xref:System.Windows.Controls.TextBlock>数行のテキストをラップするラベルにします。</span><span class="sxs-lookup"><span data-stu-id="d10f0-109">The following example shows how to use a <xref:System.Windows.Controls.TextBlock> to make a label that wraps several lines of text.</span></span>  
  
 [!code-xaml[LabelSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 <span data-ttu-id="d10f0-110">**アクセス キーおよびテキスト折り返し機能をラベルに追加する**</span><span class="sxs-lookup"><span data-stu-id="d10f0-110">**Add an Access Key and Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="d10f0-111">必要がある場合、<xref:System.Windows.Controls.Label>アクセス キー (ニーモニック) を持つを使用して、<xref:System.Windows.Controls.AccessText>要素内にある、<xref:System.Windows.Controls.Label>です。</span><span class="sxs-lookup"><span data-stu-id="d10f0-111">If you need a <xref:System.Windows.Controls.Label> that has an access key (mnemonic), use the <xref:System.Windows.Controls.AccessText> element that is inside the <xref:System.Windows.Controls.Label>.</span></span>  
  
 <span data-ttu-id="d10f0-112">などのコントロール<xref:System.Windows.Controls.Label>、 <xref:System.Windows.Controls.Button>、 <xref:System.Windows.Controls.RadioButton>、 <xref:System.Windows.Controls.CheckBox>、 <xref:System.Windows.Controls.MenuItem>、 <xref:System.Windows.Controls.TabItem>、 <xref:System.Windows.Controls.Expander>、および<xref:System.Windows.Controls.GroupBox>コントロールの既定のテンプレートがあります。</span><span class="sxs-lookup"><span data-stu-id="d10f0-112">Controls such as <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, and <xref:System.Windows.Controls.GroupBox> have default control templates.</span></span> <span data-ttu-id="d10f0-113">これらのテンプレートが含まれて、<xref:System.Windows.Controls.ContentPresenter>です。</span><span class="sxs-lookup"><span data-stu-id="d10f0-113">These templates contain a <xref:System.Windows.Controls.ContentPresenter>.</span></span> <span data-ttu-id="d10f0-114">設定できるプロパティの 1 つ、<xref:System.Windows.Controls.ContentPresenter>は<xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true"、コントロールのアクセス キーの指定に使用できます。</span><span class="sxs-lookup"><span data-stu-id="d10f0-114">One of the properties that you can set on the <xref:System.Windows.Controls.ContentPresenter> is <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true", which you can use to specify an access key for the control.</span></span>  
  
 <span data-ttu-id="d10f0-115">次の例を作成する方法を示しています、<xref:System.Windows.Controls.Label>アクセス キーがあり、テキストの折り返しをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d10f0-115">The following example shows how to create a <xref:System.Windows.Controls.Label> that has an access key and supports text wrapping.</span></span> <span data-ttu-id="d10f0-116">テキストの折り返しを例のセットを有効にする、<xref:System.Windows.Controls.AccessText.TextWrapping%2A>下線付きのアクセス キーを指定する文字使用してプロパティです。</span><span class="sxs-lookup"><span data-stu-id="d10f0-116">To enable text wrapping, the example sets the <xref:System.Windows.Controls.AccessText.TextWrapping%2A> property and uses an underline character to specify the access key.</span></span> <span data-ttu-id="d10f0-117">(下線文字の直後の文字はアクセス キーになります。)</span><span class="sxs-lookup"><span data-stu-id="d10f0-117">(The character that immediately follows the underline character is the access key.)</span></span>  
  
 [!code-xaml[LabelSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="d10f0-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d10f0-118">See Also</span></span>  
 [<span data-ttu-id="d10f0-119">方法: ラベルのターゲット プロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="d10f0-119">How to: Set the Target Property of a Label</span></span>](http://msdn.microsoft.com/library/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)
