---
title: '方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: f98d0e530f502655b9a48819d266a604581d22de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528146"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="be2cf-102">方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="be2cf-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="be2cf-103">Windows フォーム<xref:System.Windows.Forms.DataGridView>コントロールは、データを表示するために列を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="be2cf-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="be2cf-104">コントロールを手動で設定する場合は、する必要があります自分自身を追加する列。</span><span class="sxs-lookup"><span data-stu-id="be2cf-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="be2cf-105">代わりに、コントロールを生成し、列を自動的に設定するデータ ソースにバインドできます。</span><span class="sxs-lookup"><span data-stu-id="be2cf-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="be2cf-106">データ ソースを表示する数より多い列が含まれている場合は、不要な列を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="be2cf-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>  
  
 <span data-ttu-id="be2cf-107">次の手順が必要な**Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="be2cf-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="be2cf-108">このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="be2cf-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be2cf-109">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="be2cf-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="be2cf-110">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be2cf-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="be2cf-111">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be2cf-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="be2cf-112">デザイナーを使用して列を追加するには</span><span class="sxs-lookup"><span data-stu-id="be2cf-112">To add a column using the designer</span></span>  
  
1.  <span data-ttu-id="be2cf-113">スマート タグ グリフをクリックして (![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) の右上隅で、<xref:System.Windows.Forms.DataGridView>を制御し、**列の追加**です。</span><span class="sxs-lookup"><span data-stu-id="be2cf-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>  
  
2.  <span data-ttu-id="be2cf-114">**列の追加** ダイアログ ボックスで、選択、**データ バインド列**オプションし、データ ソースから列を選択するかを選択して、**非バインド列**オプションし、列の定義指定されたフィールドを使用します。</span><span class="sxs-lookup"><span data-stu-id="be2cf-114">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>  
  
3.  <span data-ttu-id="be2cf-115">クリックして、**追加**を既存の列は既に埋まらない場合コントロールの表示領域に、デザイナーに表示する列を追加するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="be2cf-115">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be2cf-116">列のプロパティを変更することができます、**列の編集** ダイアログ ボックスは、コントロールのスマート タグからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="be2cf-116">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>  
  
### <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="be2cf-117">デザイナーを使用して列を削除するには</span><span class="sxs-lookup"><span data-stu-id="be2cf-117">To remove a column using the designer</span></span>  
  
1.  <span data-ttu-id="be2cf-118">選択**列の編集**コントロールのスマート タグからです。</span><span class="sxs-lookup"><span data-stu-id="be2cf-118">Choose **Edit Columns** from the control's smart tag.</span></span>  
  
2.  <span data-ttu-id="be2cf-119">列を選択して、**選択されている列** ボックスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="be2cf-119">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="be2cf-120">をクリックして、**削除**ボタンに、デザイナーに表示されなくなった原因の列を削除します。</span><span class="sxs-lookup"><span data-stu-id="be2cf-120">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be2cf-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="be2cf-121">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="be2cf-122">方法: Windows アプリケーション プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="be2cf-122">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="be2cf-123">方法: Windows フォームにコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="be2cf-123">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
