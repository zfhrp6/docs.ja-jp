---
title: '方法 : テキストのトリミングを有効にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
ms.openlocfilehash: 97bc88b298500892fcc7d26e61f8052a05d9e593
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543541"
---
# <a name="how-to-enable-text-trimming"></a><span data-ttu-id="62f4c-102">方法 : テキストのトリミングを有効にする</span><span class="sxs-lookup"><span data-stu-id="62f4c-102">How to: Enable Text Trimming</span></span>
<span data-ttu-id="62f4c-103">この例は、使用法とで使用できる値の効果を示しています、<xref:System.Windows.TextTrimming>列挙します。</span><span class="sxs-lookup"><span data-stu-id="62f4c-103">This example demonstrates the usage and effects of the values available in the <xref:System.Windows.TextTrimming> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62f4c-104">例</span><span class="sxs-lookup"><span data-stu-id="62f4c-104">Example</span></span>  
 <span data-ttu-id="62f4c-105">次の例では定義、<xref:System.Windows.Controls.TextBlock>を持つ要素、<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>属性に設定します。</span><span class="sxs-lookup"><span data-stu-id="62f4c-105">The following example defines a <xref:System.Windows.Controls.TextBlock> element with the <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> attribute set.</span></span>  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a><span data-ttu-id="62f4c-106">例</span><span class="sxs-lookup"><span data-stu-id="62f4c-106">Example</span></span>  
 <span data-ttu-id="62f4c-107">対応する設定<xref:System.Windows.TextTrimming>以下にコードでプロパティを示すです。</span><span class="sxs-lookup"><span data-stu-id="62f4c-107">Setting the corresponding <xref:System.Windows.TextTrimming> property in code is demonstrated below.</span></span>  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 <span data-ttu-id="62f4c-108">テキストのトリミングの現在の 3 つのオプションがある:**切り取ら**、 **WordEllipsis**、および**None**です。</span><span class="sxs-lookup"><span data-stu-id="62f4c-108">There are currently three options for trimming text: **CharacterEllipsis**, **WordEllipsis**, and **None**.</span></span>  
  
 <span data-ttu-id="62f4c-109">ときに<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>に設定されている**切り取ら**テキストが切り捨てられるし、トリミング枠に最も近い文字の省略記号では継続します。</span><span class="sxs-lookup"><span data-stu-id="62f4c-109">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **CharacterEllipsis**, text is trimmed and continued with an ellipsis at the character closest to the trimming edge.</span></span>  <span data-ttu-id="62f4c-110">この設定では、トリミング境界により近い位置でテキストが切り取られます。ただし、単語の一部が切り取られる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="62f4c-110">This setting tends to trim text to fit more closely to the trimming boundary, but may result in words being partially trimmed.</span></span>  <span data-ttu-id="62f4c-111">次の図でこの設定の効果を示しています、<xref:System.Windows.Controls.TextBlock>上に定義されたものに似ています。</span><span class="sxs-lookup"><span data-stu-id="62f4c-111">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="62f4c-112">![例: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")</span><span class="sxs-lookup"><span data-stu-id="62f4c-112">![Example: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")</span></span>  
  
 <span data-ttu-id="62f4c-113">ときに<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>に設定されている**WordEllipsis**テキストが切り捨てられるし、トリミング枠に最も近い最初の完全単語の末尾にある省略記号では継続します。</span><span class="sxs-lookup"><span data-stu-id="62f4c-113">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **WordEllipsis**, text is trimmed and continued with an ellipsis at the end of the first full word closest to the trimming edge.</span></span>  <span data-ttu-id="62f4c-114">この設定は、部分的に単語は表示されませんが、傾向としてトリミング枠の類似した形にテキストのトリミングされませんが、**切り取ら**設定します。</span><span class="sxs-lookup"><span data-stu-id="62f4c-114">This setting will not show partially trimmed words, but tends not to trim text as closely to the trimming edge as the **CharacterEllipsis** setting.</span></span>  <span data-ttu-id="62f4c-115">次の図でこの設定の効果を示しています、<xref:System.Windows.Controls.TextBlock>上で定義します。</span><span class="sxs-lookup"><span data-stu-id="62f4c-115">The following figure shows the effect of this setting on the <xref:System.Windows.Controls.TextBlock> defined above.</span></span>  
  
 <span data-ttu-id="62f4c-116">![例: TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")</span><span class="sxs-lookup"><span data-stu-id="62f4c-116">![Example: TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")</span></span>  
  
 <span data-ttu-id="62f4c-117">ときに<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>に設定されている**None**テキストのトリミングは実行されません。</span><span class="sxs-lookup"><span data-stu-id="62f4c-117">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **None**, no text trimming is performed.</span></span>  <span data-ttu-id="62f4c-118">この場合、テキストは親テキスト コンテナーの境界にトリミングされるだけです。</span><span class="sxs-lookup"><span data-stu-id="62f4c-118">In this case, text is simply cropped to the boundary of the parent text container.</span></span>  <span data-ttu-id="62f4c-119">次の図でこの設定の効果を示しています、<xref:System.Windows.Controls.TextBlock>上に定義されたものに似ています。</span><span class="sxs-lookup"><span data-stu-id="62f4c-119">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="62f4c-120">![例: TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")</span><span class="sxs-lookup"><span data-stu-id="62f4c-120">![Example: TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")</span></span>
