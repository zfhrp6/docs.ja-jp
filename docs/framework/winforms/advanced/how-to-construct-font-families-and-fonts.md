---
title: "方法 : フォント ファミリとフォントを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e152c525550554082d7d6c38a972ccc150adabb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-construct-font-families-and-fonts"></a><span data-ttu-id="e4a13-102">方法 : フォント ファミリとフォントを作成する</span><span class="sxs-lookup"><span data-stu-id="e4a13-102">How to: Construct Font Families and Fonts</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="e4a13-103">スタイルは異なっても同じ書体を使用するフォントのフォント ファミリにグループ化します。</span><span class="sxs-lookup"><span data-stu-id="e4a13-103"> groups fonts with the same typeface but different styles into font families.</span></span> <span data-ttu-id="e4a13-104">たとえば、Arial フォント ファミリには、次のフォントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e4a13-104">For example, the Arial font family contains the following fonts:</span></span>  
  
-   <span data-ttu-id="e4a13-105">Arial 標準</span><span class="sxs-lookup"><span data-stu-id="e4a13-105">Arial Regular</span></span>  
  
-   <span data-ttu-id="e4a13-106">Arial 太字</span><span class="sxs-lookup"><span data-stu-id="e4a13-106">Arial Bold</span></span>  
  
-   <span data-ttu-id="e4a13-107">Arial 斜体</span><span class="sxs-lookup"><span data-stu-id="e4a13-107">Arial Italic</span></span>  
  
-   <span data-ttu-id="e4a13-108">Arial 太字斜体</span><span class="sxs-lookup"><span data-stu-id="e4a13-108">Arial Bold Italic</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="e4a13-109">フォームのファミリに 4 つのスタイルを使用します。 標準、太字、斜体、および太字斜体です。</span><span class="sxs-lookup"><span data-stu-id="e4a13-109"> uses four styles to form families: regular, bold, italic, and bold italic.</span></span> <span data-ttu-id="e4a13-110">などの形容詞*を絞り込む*と*丸め*スタイル; とは見なされません、ファミリ名の一部であるではなくです。</span><span class="sxs-lookup"><span data-stu-id="e4a13-110">Adjectives such as *narrow* and *rounded* are not considered styles; rather they are part of the family name.</span></span> <span data-ttu-id="e4a13-111">たとえば、次のメンバーのフォント ファミリはゴシックのように。</span><span class="sxs-lookup"><span data-stu-id="e4a13-111">For example, Arial Narrow is a font family with the following members:</span></span>  
  
-   <span data-ttu-id="e4a13-112">Arial ナロー標準</span><span class="sxs-lookup"><span data-stu-id="e4a13-112">Arial Narrow Regular</span></span>  
  
-   <span data-ttu-id="e4a13-113">太字 arial ナロー</span><span class="sxs-lookup"><span data-stu-id="e4a13-113">Arial Narrow Bold</span></span>  
  
-   <span data-ttu-id="e4a13-114">Arial ナロー斜体</span><span class="sxs-lookup"><span data-stu-id="e4a13-114">Arial Narrow Italic</span></span>  
  
-   <span data-ttu-id="e4a13-115">Arial ナロー太字斜体</span><span class="sxs-lookup"><span data-stu-id="e4a13-115">Arial Narrow Bold Italic</span></span>  
  
 <span data-ttu-id="e4a13-116">テキストを描画する前に[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、構築する必要があります、<xref:System.Drawing.FontFamily>オブジェクトおよび<xref:System.Drawing.Font>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e4a13-116">Before you can draw text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to construct a <xref:System.Drawing.FontFamily> object and a <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="e4a13-117"><xref:System.Drawing.FontFamily>オブジェクト (たとえば、Arial) 書体を指定して、<xref:System.Drawing.Font>オブジェクトは、サイズ、スタイル、および単位を指定します。</span><span class="sxs-lookup"><span data-stu-id="e4a13-117">The <xref:System.Drawing.FontFamily> object specifies the typeface (for example, Arial), and the <xref:System.Drawing.Font> object specifies the size, style, and units.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4a13-118">例</span><span class="sxs-lookup"><span data-stu-id="e4a13-118">Example</span></span>  
 <span data-ttu-id="e4a13-119">次の例では、標準のスタイル、サイズが 16 ピクセルの Arial フォントを構築します。</span><span class="sxs-lookup"><span data-stu-id="e4a13-119">The following example constructs a regular style Arial font with a size of 16 pixels.</span></span> <span data-ttu-id="e4a13-120">次のコードでは、最初の引数が渡される、<xref:System.Drawing.Font.%23ctor%2A>コンス トラクターは、<xref:System.Drawing.FontFamily>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e4a13-120">In the following code, the first argument passed to the <xref:System.Drawing.Font.%23ctor%2A> constructor is the <xref:System.Drawing.FontFamily> object.</span></span> <span data-ttu-id="e4a13-121">2 番目の引数は、4 番目の引数によって識別される単位でフォントのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4a13-121">The second argument specifies the size of the font measured in units identified by the fourth argument.</span></span> <span data-ttu-id="e4a13-122">3 番目の引数は、スタイルを識別します。</span><span class="sxs-lookup"><span data-stu-id="e4a13-122">The third argument identifies the style.</span></span>  
  
 <span data-ttu-id="e4a13-123"><xref:System.Drawing.GraphicsUnit.Pixel>メンバーである、<xref:System.Drawing.GraphicsUnit>列挙型、および<xref:System.Drawing.FontStyle.Regular>のメンバーである、<xref:System.Drawing.FontStyle>列挙します。</span><span class="sxs-lookup"><span data-stu-id="e4a13-123"><xref:System.Drawing.GraphicsUnit.Pixel> is a member of the <xref:System.Drawing.GraphicsUnit> enumeration, and <xref:System.Drawing.FontStyle.Regular> is a member of the <xref:System.Drawing.FontStyle> enumeration.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4a13-124">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="e4a13-124">Compiling the Code</span></span>  
 <span data-ttu-id="e4a13-125">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> のパラメーターである `e`<xref:System.Windows.Forms.PaintEventHandler> を必要とします。</span><span class="sxs-lookup"><span data-stu-id="e4a13-125">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4a13-126">参照</span><span class="sxs-lookup"><span data-stu-id="e4a13-126">See Also</span></span>  
 [<span data-ttu-id="e4a13-127">フォントとテキストの使用</span><span class="sxs-lookup"><span data-stu-id="e4a13-127">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="e4a13-128">Windows フォームにおけるグラフィックスと描画</span><span class="sxs-lookup"><span data-stu-id="e4a13-128">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
