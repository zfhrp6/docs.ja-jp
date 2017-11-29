---
title: "Windows フォーム DataGridView コントロールでのデータの書式設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e716dc74946ac6f18ab82c6834518f0bd6bbea76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6fb6e-102">Windows フォーム DataGridView コントロールでのデータの書式設定</span><span class="sxs-lookup"><span data-stu-id="6fb6e-102">Data Formatting in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6fb6e-103"><xref:System.Windows.Forms.DataGridView>コントロールがセルの値と、親列を表示するデータ型の間の自動変換を提供します。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-103">The <xref:System.Windows.Forms.DataGridView> control provides automatic conversion between cell values and the data types that the parent columns display.</span></span> <span data-ttu-id="6fb6e-104">テキスト ボックスの列はたとえば、日付、時刻、数、および列挙値の文字列形式を表示し、ユーザーが入力した文字列値をデータ ストアで必要な型に変換します。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-104">Text box columns, for example, display string representations of date, time, number, and enumeration values, and convert user-entered string values to the types required by the data store.</span></span>  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a><span data-ttu-id="6fb6e-105">DataGridViewCellStyle クラスを使用した書式設定</span><span class="sxs-lookup"><span data-stu-id="6fb6e-105">Formatting with the DataGridViewCellStyle class</span></span>  
 <span data-ttu-id="6fb6e-106"><xref:System.Windows.Forms.DataGridView>コントロールは、基本的なデータを使用してセル値の書式を提供、<xref:System.Windows.Forms.DataGridViewCellStyle>クラスです。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-106">The <xref:System.Windows.Forms.DataGridView> control provides basic data formatting of cell values through the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span> <span data-ttu-id="6fb6e-107">使用することができます、<xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>プロパティで説明されている書式指定子を使用して現在の既定のカルチャの形式の日付、時刻、数、および列挙の値を[型の書式設定](../../../../docs/standard/base-types/formatting-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-107">You can use the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property to format date, time, number, and enumeration values for the current default culture using the format specifiers described in [Formatting Types](../../../../docs/standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="6fb6e-108">これらの値を使用して特定のカルチャの書式を設定することもできます、<xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-108">You can also format these values for specific cultures using the <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> property.</span></span> <span data-ttu-id="6fb6e-109">データを表示して、ユーザーが指定された形式で入力したデータの解析を指定された形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-109">The specified format is used both to display data and to parse data that the user enters in the specified format.</span></span>  
  
 <span data-ttu-id="6fb6e-110"><xref:System.Windows.Forms.DataGridViewCellStyle> Wordwrap、テキストの配置、およびデータベースの null 値のカスタム表示のクラスは追加の書式設定プロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-110">The <xref:System.Windows.Forms.DataGridViewCellStyle> class provides additional formatting properties for wordwrap, text alignment, and the custom display of null database values.</span></span> <span data-ttu-id="6fb6e-111">詳細については、「[方法 : Windows フォーム DataGridView コントロールのデータの書式を設定する](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-111">For more information, see [How to: Format Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="formatting-with-the-cellformatting-event"></a><span data-ttu-id="6fb6e-112">書式設定のイベントに書式設定</span><span class="sxs-lookup"><span data-stu-id="6fb6e-112">Formatting with the CellFormatting Event</span></span>  
 <span data-ttu-id="6fb6e-113">基本的な書式設定がニーズを満たさない場合は、カスタム データのハンドラーで書式設定を指定できます、<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>イベント。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-113">If the basic formatting does not meet your needs, you can provide custom data formatting in a handler for the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="6fb6e-114"><xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>ハンドラーに渡されるが、<xref:System.Windows.Forms.ConvertEventArgs.Value%2A>を最初に、セルの値を格納するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-114">The <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> passed to the handler has a <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property that initially contains the cell value.</span></span> <span data-ttu-id="6fb6e-115">通常、この値は自動的に表示の種類に変換します。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-115">Normally, this value is automatically converted to the display type.</span></span> <span data-ttu-id="6fb6e-116">値を自分で変換するには設定、<xref:System.Windows.Forms.ConvertEventArgs.Value%2A>プロパティの表示の種類の値。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-116">To convert the value yourself, set the <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property to a value of the display type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6fb6e-117">変更をオーバーライドし、セルの書式指定文字列が有効な場合、<xref:System.Windows.Forms.ConvertEventArgs.Value%2A>プロパティ値を設定しない限り、<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-117">If a format string is in effect for the cell, it overrides your change of the <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> property value unless you set the <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="6fb6e-118"><xref:System.Windows.Forms.DataGridView.CellFormatting>イベントを設定するときにも役立ちます<xref:System.Windows.Forms.DataGridViewCellStyle>個々 のセル プロパティの値に基づきます。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-118">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event is also useful when you want to set <xref:System.Windows.Forms.DataGridViewCellStyle> properties for individual cells based on their values.</span></span> <span data-ttu-id="6fb6e-119">詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールでデータの書式をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-119">For more information, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="6fb6e-120">ユーザー指定の値の既定の解析がニーズを満たさない場合は、処理、<xref:System.Windows.Forms.DataGridView.CellParsing>のイベント、<xref:System.Windows.Forms.DataGridView>カスタム解析を提供するコントロール。</span><span class="sxs-lookup"><span data-stu-id="6fb6e-120">If the default parsing of user-specified values does not meet your needs, you can handle the <xref:System.Windows.Forms.DataGridView.CellParsing> event of the <xref:System.Windows.Forms.DataGridView> control to provide custom parsing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb6e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="6fb6e-121">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [<span data-ttu-id="6fb6e-122">Windows フォーム DataGridView コントロールでのデータの表示</span><span class="sxs-lookup"><span data-stu-id="6fb6e-122">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="6fb6e-123">Windows フォーム DataGridView コントロールでのセルのスタイル</span><span class="sxs-lookup"><span data-stu-id="6fb6e-123">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="6fb6e-124">方法: Windows フォーム DataGridView コントロールのデータの書式を設定する</span><span class="sxs-lookup"><span data-stu-id="6fb6e-124">How to: Format Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="6fb6e-125">方法: Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="6fb6e-125">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
