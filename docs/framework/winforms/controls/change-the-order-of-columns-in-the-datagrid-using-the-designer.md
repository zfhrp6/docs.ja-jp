---
title: "方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列の順序を変更する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c36bfdd69cb4a3e7827302a7bde5139675a30429
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="50053-102">方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列の順序を変更する</span><span class="sxs-lookup"><span data-stu-id="50053-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="50053-103">Windows フォームのバインドと<xref:System.Windows.Forms.DataGridView>コントロール、データ ソースを自動的に生成された列の表示順序には、データ ソースによって決まります。</span><span class="sxs-lookup"><span data-stu-id="50053-103">When you bind a Windows Forms <xref:System.Windows.Forms.DataGridView> control to a data source, the display order of the automatically generated columns is dictated by the data source.</span></span> <span data-ttu-id="50053-104">この順序が好ましくない場合は、デザイナーを使用して列の順序を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="50053-104">If this order is not what you prefer, you can change the order of the columns using the designer.</span></span> <span data-ttu-id="50053-105">コントロールにバインドされていない列を追加し、その表示順序を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="50053-105">You may also want to add unbound columns to the control and change their display order.</span></span> <span data-ttu-id="50053-106">プログラムで列の順序を変更する方法については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで列の順序を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="50053-106">For information about how to change the column order programmatically, see [How to: Change the Order of Columns in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="50053-107">次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="50053-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="50053-108">このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="50053-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50053-109">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="50053-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="50053-110">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50053-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="50053-111">詳細については、次を参照してください[Visual Studio での開発設定のカスタマイズ。](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="50053-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span></span>  
  
### <a name="to-change-the-column-order-using-the-designer"></a><span data-ttu-id="50053-112">デザイナーを使用して列の順序を変更するには</span><span class="sxs-lookup"><span data-stu-id="50053-112">To change the column order using the designer</span></span>  
  
1.  <span data-ttu-id="50053-113">スマート タグ グリフをクリックして (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) の右上隅で、<xref:System.Windows.Forms.DataGridView>を制御し、**列の編集**です。</span><span class="sxs-lookup"><span data-stu-id="50053-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="50053-114">列を選択して、**選択されている列** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="50053-114">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="50053-115">上矢印または下矢印の右側に、**選択した列**選択した列が目的の位置になるまでを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="50053-115">Click the up or down arrow to the right of the **Selected Columns** list until the selected column is in the position you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50053-116">参照</span><span class="sxs-lookup"><span data-stu-id="50053-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="50053-117">方法: デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="50053-117">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="50053-118">方法: Windows アプリケーション プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="50053-118">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="50053-119">方法: Windows フォームにコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="50053-119">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
