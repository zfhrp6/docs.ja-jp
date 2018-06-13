---
title: '方法 : MDI 子フォームを配置する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
ms.openlocfilehash: d5c0d24ff8a7188a669c218ce8b0dc66ffa56c47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521028"
---
# <a name="how-to-arrange-mdi-child-forms"></a><span data-ttu-id="27652-102">方法 : MDI 子フォームを配置する</span><span class="sxs-lookup"><span data-stu-id="27652-102">How to: Arrange MDI Child Forms</span></span>
<span data-ttu-id="27652-103">多くの場合、アプリケーションには、並べて表示、重ねて表示、整列など、開いている MDI 子フォームのレイアウトを制御するメニュー コマンドがあります。</span><span class="sxs-lookup"><span data-stu-id="27652-103">Often, applications will have menu commands for actions such as Tile, Cascade, and Arrange, which control the layout of the open MDI child forms.</span></span> <span data-ttu-id="27652-104"><xref:System.Windows.Forms.Form.LayoutMdi%2A> メソッドと <xref:System.Windows.Forms.MdiLayout> 列挙値のいずれかを使用して、MDI 親フォーム内の子フォームを再配置することができます。</span><span class="sxs-lookup"><span data-stu-id="27652-104">You can use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method with one of the <xref:System.Windows.Forms.MdiLayout> enumeration values to rearrange the child forms in an MDI parent form.</span></span>  
  
 <span data-ttu-id="27652-105"><xref:System.Windows.Forms.MdiLayout> 列挙値は、子フォームを重ねて表示したり、水平方向または垂直方向に並べて表示したり、または MDI フォームの下部に沿って整列された子フォーム アイコンとして表示します。</span><span class="sxs-lookup"><span data-stu-id="27652-105">The <xref:System.Windows.Forms.MdiLayout> enumeration values display child forms as cascading, as horizontally or vertically tiled, or as child form icons arranged along the lower portion of the MDI form.</span></span> <span data-ttu-id="27652-106">これらの値が、Windows のコマンドと同じ効果がある**ウィンドウを重ねて表示**、**ウィンドウを並べて表示**、**表示**、および**デスクトップを表示します。**、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="27652-106">These values have the same effect as the Windows commands **Cascade windows**, **Show windows side by side**, **Show windows stacked**, and **Show the desktop**, respectively.</span></span>  
  
 <span data-ttu-id="27652-107">多くの場合、これらのメソッドは、メニュー項目の <xref:System.Windows.Forms.Control.Click> イベントで呼び出されるイベント ハンドラーとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="27652-107">Often, these methods are used as the event handlers called by a menu item's <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="27652-108">このようにして、テキスト "重ねて表示" を指定したメニュー項目に、MDI 子ウィンドウに対する目的の効果を持たせることができます。</span><span class="sxs-lookup"><span data-stu-id="27652-108">In this way, a menu item with the text "Cascade Windows" can have the desired effect on the MDI child windows.</span></span>  
  
### <a name="to-arrange-child-forms"></a><span data-ttu-id="27652-109">子フォームを整列させるには</span><span class="sxs-lookup"><span data-stu-id="27652-109">To arrange child forms</span></span>  
  
1.  <span data-ttu-id="27652-110">メソッドで、<xref:System.Windows.Forms.Form.LayoutMdi%2A> メソッドを使用して MDI 親フォームの <xref:System.Windows.Forms.MdiLayout> 列挙体を設定します。</span><span class="sxs-lookup"><span data-stu-id="27652-110">In a method, use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method to set the <xref:System.Windows.Forms.MdiLayout> enumeration for the MDI parent form.</span></span> <span data-ttu-id="27652-111">次に、MDI 親フォーム (<xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType>) の子ウィンドウに `Form1` 列挙値を使用する例を示します。</span><span class="sxs-lookup"><span data-stu-id="27652-111">The following example uses the <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> enumeration value for the child windows of the MDI parent form (`Form1`).</span></span> <span data-ttu-id="27652-112">列挙体は、イベント ハンドラーの中にコードで使用されて、<xref:System.Windows.Forms.Control.Click>のイベント、**ウィンドウを重ねて表示**メニュー項目。</span><span class="sxs-lookup"><span data-stu-id="27652-112">The enumeration is used in code during the event handler for the <xref:System.Windows.Forms.Control.Click> event of the **Cascade Windows** menu item.</span></span>  
  
    ```vb  
    Protected Sub CascadeWindows_Click(ByVal sender As System.Object, ByVal e As System.EventArgs)  
       Me.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade)  
    End Sub  
    ```  
  
    ```csharp  
    protected void CascadeWindows_Click(object sender, System.EventArgs e){  
       this.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="27652-113">使用する <xref:System.Windows.Forms.MdiLayout> 列挙値を変更することで、ウィンドウを並べて表示したり、ウィンドウをアイコンとして並べたりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="27652-113">You can also tile windows and arranging windows as icons by changing the <xref:System.Windows.Forms.MdiLayout> enumeration value used.</span></span>  
  
2.  <span data-ttu-id="27652-114">Visual C# を使用している場合は、フォームのコンストラクターに次のコードを追加して、イベント ハンドラーを登録します。</span><span class="sxs-lookup"><span data-stu-id="27652-114">If you’re using Visual C#, place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="27652-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="27652-115">See Also</span></span>  
 [<span data-ttu-id="27652-116">マルチ ドキュメント インターフェイス (MDI) アプリケーション</span><span class="sxs-lookup"><span data-stu-id="27652-116">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="27652-117">方法: MDI 親フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="27652-117">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="27652-118">方法: MDI 子フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="27652-118">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="27652-119">方法: アクティブな MDI 子フォームを特定する</span><span class="sxs-lookup"><span data-stu-id="27652-119">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [<span data-ttu-id="27652-120">方法: アクティブな MDI 子フォームにデータを送信する</span><span class="sxs-lookup"><span data-stu-id="27652-120">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)
