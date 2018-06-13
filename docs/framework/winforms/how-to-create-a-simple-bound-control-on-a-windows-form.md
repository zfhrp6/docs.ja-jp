---
title: '方法 : Windows フォームに単純バインド コントロールを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: ce4585a1c5c2b9acbdb7ec33c62a1e91851b720e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538833"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="e2bee-102">方法 : Windows フォームに単純バインド コントロールを作成する</span><span class="sxs-lookup"><span data-stu-id="e2bee-102">How to: Create a Simple-Bound Control on a Windows Form</span></span>
<span data-ttu-id="e2bee-103">*単純バインディング*、コントロールがデータセット テーブルの列の値など、1 つのデータ要素を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="e2bee-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="e2bee-104">できる単純なをバインドするコントロールの任意のプロパティ データ値。</span><span class="sxs-lookup"><span data-stu-id="e2bee-104">You can simple-bind any property of a control to a data value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2bee-105">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e2bee-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e2bee-106">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e2bee-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e2bee-107">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2bee-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-simple-bind-a-control"></a><span data-ttu-id="e2bee-108">単純なコントロールをバインドする</span><span class="sxs-lookup"><span data-stu-id="e2bee-108">To simple-bind a control</span></span>  
  
1.  <span data-ttu-id="e2bee-109">データ ソースに接続します。</span><span class="sxs-lookup"><span data-stu-id="e2bee-109">Connect to a data source.</span></span> <span data-ttu-id="e2bee-110">詳細については、次を参照してください。[データ ソースに接続する](../../../docs/framework/data/adonet/connecting-to-a-data-source.md)です。</span><span class="sxs-lookup"><span data-stu-id="e2bee-110">For more information, see [Connecting to a Data Source](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="e2bee-111">フォームでコントロールを選択し、表示、**プロパティ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="e2bee-111">In the form, select the control and display the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="e2bee-112">展開して、 **(DataBindings)** プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e2bee-112">Expand the **(DataBindings)** property.</span></span>  
  
     <span data-ttu-id="e2bee-113">最も頻繁にバインドされているプロパティは、下に表示されます、 **(DataBindings)** プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e2bee-113">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="e2bee-114">たとえば、ほとんどのコントロールで、**テキスト**プロパティが最も頻繁に連結します。</span><span class="sxs-lookup"><span data-stu-id="e2bee-114">For example, in most controls, the **Text** property is most frequently bound.</span></span>  
  
4.  <span data-ttu-id="e2bee-115">場合、プロパティにバインド一般的にバインドされたプロパティの 1 つはありません をクリックして、**省略記号**ボタン (![VisualStudioEllipsesButton スクリーン ショット](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) で、 **(詳細)** を表示するボックス、**フォーマットと詳細バインド**そのコントロールのプロパティの完全な一覧がダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="e2bee-115">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>  
  
5.  <span data-ttu-id="e2bee-116">下にあるドロップダウン矢印をクリックし、バインドするプロパティを選択する**バインド**です。</span><span class="sxs-lookup"><span data-stu-id="e2bee-116">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>  
  
     <span data-ttu-id="e2bee-117">使用できるデータ ソースの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e2bee-117">A list of available data sources is displayed.</span></span>  
  
6.  <span data-ttu-id="e2bee-118">目的の 1 つのデータ要素が見つかるまで、バインド先のデータ ソースを展開します。</span><span class="sxs-lookup"><span data-stu-id="e2bee-118">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="e2bee-119">たとえば、データセットのテーブル内の列の値にバインドする場合は、データセットの名前を展開し、次にテーブル名を展開して、列名を表示します。</span><span class="sxs-lookup"><span data-stu-id="e2bee-119">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
7.  <span data-ttu-id="e2bee-120">バインド先の要素の名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e2bee-120">Click the name of an element to bind to.</span></span>  
  
8.  <span data-ttu-id="e2bee-121">作業している場合、**フォーマットと詳細バインド**ダイアログ ボックスで、をクリックして**OK**に戻るには、**プロパティ**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="e2bee-121">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>  
  
9. <span data-ttu-id="e2bee-122">コントロールの追加のプロパティをバインドする場合は、手順 3. ~ 7. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="e2bee-122">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e2bee-123">単純バインド コントロールでは、単一のデータ要素のみを表示するため、Windows フォームに単純バインド コントロールにナビゲーション ロジックを含めるごく一般的なものです。</span><span class="sxs-lookup"><span data-stu-id="e2bee-123">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2bee-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2bee-124">See Also</span></span>  
 <xref:System.Windows.Forms.Binding>  
 [<span data-ttu-id="e2bee-125">Windows フォームでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="e2bee-125">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="e2bee-126">データ連結と Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="e2bee-126">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
