---
title: "方法 : Windows フォームに単純バインド コントロールを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c55480e02eac4cc4156fa119493f2fd2f57c07a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="d14e3-102">方法 : Windows フォームに単純バインド コントロールを作成する</span><span class="sxs-lookup"><span data-stu-id="d14e3-102">How to: Create a Simple-Bound Control on a Windows Form</span></span>
<span data-ttu-id="d14e3-103">*単純バインディング*、コントロールがデータセット テーブルの列の値など、1 つのデータ要素を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="d14e3-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="d14e3-104">できる単純なをバインドするコントロールの任意のプロパティ データ値。</span><span class="sxs-lookup"><span data-stu-id="d14e3-104">You can simple-bind any property of a control to a data value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d14e3-105">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d14e3-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d14e3-106">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d14e3-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d14e3-107">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d14e3-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-simple-bind-a-control"></a><span data-ttu-id="d14e3-108">単純なコントロールをバインドする</span><span class="sxs-lookup"><span data-stu-id="d14e3-108">To simple-bind a control</span></span>  
  
1.  <span data-ttu-id="d14e3-109">データ ソースに接続します。</span><span class="sxs-lookup"><span data-stu-id="d14e3-109">Connect to a data source.</span></span> <span data-ttu-id="d14e3-110">詳細については、次を参照してください。[データ ソースに接続する](../../../docs/framework/data/adonet/connecting-to-a-data-source.md)です。</span><span class="sxs-lookup"><span data-stu-id="d14e3-110">For more information, see [Connecting to a Data Source](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="d14e3-111">フォームでコントロールを選択し、表示、**プロパティ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="d14e3-111">In the form, select the control and display the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="d14e3-112">展開して、 **(DataBindings)**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d14e3-112">Expand the **(DataBindings)** property.</span></span>  
  
     <span data-ttu-id="d14e3-113">最も頻繁にバインドされているプロパティは、下に表示されます、 **(DataBindings)**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d14e3-113">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="d14e3-114">たとえば、ほとんどのコントロールで、**テキスト**プロパティが最も頻繁に連結します。</span><span class="sxs-lookup"><span data-stu-id="d14e3-114">For example, in most controls, the **Text** property is most frequently bound.</span></span>  
  
4.  <span data-ttu-id="d14e3-115">場合、プロパティにバインド一般的にバインドされたプロパティの 1 つはありません をクリックして、**省略記号**ボタン (![VisualStudioEllipsesButton スクリーン ショット](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) で、 **(詳細)**を表示するボックス、**フォーマットと詳細バインド**そのコントロールのプロパティの完全な一覧がダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="d14e3-115">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>  
  
5.  <span data-ttu-id="d14e3-116">下にあるドロップダウン矢印をクリックし、バインドするプロパティを選択する**バインド**です。</span><span class="sxs-lookup"><span data-stu-id="d14e3-116">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>  
  
     <span data-ttu-id="d14e3-117">使用できるデータ ソースの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d14e3-117">A list of available data sources is displayed.</span></span>  
  
6.  <span data-ttu-id="d14e3-118">目的の 1 つのデータ要素が見つかるまで、バインド先のデータ ソースを展開します。</span><span class="sxs-lookup"><span data-stu-id="d14e3-118">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="d14e3-119">たとえば、データセットのテーブル内の列の値にバインドする場合は、データセットの名前を展開し、次にテーブル名を展開して、列名を表示します。</span><span class="sxs-lookup"><span data-stu-id="d14e3-119">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
7.  <span data-ttu-id="d14e3-120">バインド先の要素の名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d14e3-120">Click the name of an element to bind to.</span></span>  
  
8.  <span data-ttu-id="d14e3-121">作業している場合、**フォーマットと詳細バインド**ダイアログ ボックスで、をクリックして**OK**に戻るには、**プロパティ**ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="d14e3-121">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>  
  
9. <span data-ttu-id="d14e3-122">コントロールの追加のプロパティをバインドする場合は、手順 3. ~ 7. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="d14e3-122">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d14e3-123">単純バインド コントロールでは、単一のデータ要素のみを表示するため、Windows フォームに単純バインド コントロールにナビゲーション ロジックを含めるごく一般的なものです。</span><span class="sxs-lookup"><span data-stu-id="d14e3-123">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d14e3-124">参照</span><span class="sxs-lookup"><span data-stu-id="d14e3-124">See Also</span></span>  
 <xref:System.Windows.Forms.Binding>  
 [<span data-ttu-id="d14e3-125">Windows フォームでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="d14e3-125">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="d14e3-126">データ連結と Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="d14e3-126">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
