---
title: '方法 : Windows フォーム上のオブジェクトをレイヤー化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: 1a2a25f2e7eaa6618c0bf535a34f7dc6a28d51fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533687"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="c0e36-102">方法 : Windows フォーム上のオブジェクトをレイヤー化する</span><span class="sxs-lookup"><span data-stu-id="c0e36-102">How to: Layer Objects on Windows Forms</span></span>
<span data-ttu-id="c0e36-103">複雑なユーザー インターフェイスを作成またはマルチ ドキュメント インターフェイス (MDI) フォームを操作するときに多くの場合のコントロールと複雑なユーザー インターフェイス (UI) を作成する子フォームをレイヤーにします。</span><span class="sxs-lookup"><span data-stu-id="c0e36-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="c0e36-104">移動し、コントロールと windows グループのコンテキスト内での追跡を z オーダーを操作できます。</span><span class="sxs-lookup"><span data-stu-id="c0e36-104">To move and keep track of controls and windows within the context of a group, you manipulate their z-order.</span></span> <span data-ttu-id="c0e36-105">*Z オーダー* (深度) のフォームの z 軸に沿ってフォーム上のコントロールのビジュアルの重ね順がします。</span><span class="sxs-lookup"><span data-stu-id="c0e36-105">*Z-order* is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="c0e36-106">Z オーダーの上部にあるウィンドウには、他のすべてのウィンドウが重複しています。</span><span class="sxs-lookup"><span data-stu-id="c0e36-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="c0e36-107">その他のすべての windows では、z オーダーの下部にあるウィンドウと重複します。</span><span class="sxs-lookup"><span data-stu-id="c0e36-107">All other windows overlap the window at the bottom of the z-order.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0e36-108">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c0e36-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c0e36-109">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0e36-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c0e36-110">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0e36-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="c0e36-111">デザイン時にコントロールをレイヤーに</span><span class="sxs-lookup"><span data-stu-id="c0e36-111">To layer controls at design time</span></span>  
  
1.  <span data-ttu-id="c0e36-112">レイヤーにするコントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="c0e36-112">Select a control that you want to layer.</span></span>  
  
2.  <span data-ttu-id="c0e36-113">**形式** メニューのをポイント**順序**、クリックして**前面へ移動**または**最背面へ移動**です。</span><span class="sxs-lookup"><span data-stu-id="c0e36-113">On the **Format** menu, point to **Order**, and then click **Bring To Front** or **Send To Back**.</span></span>  
  
### <a name="to-layer-controls-programmatically"></a><span data-ttu-id="c0e36-114">コントロールをプログラムでレイヤーを</span><span class="sxs-lookup"><span data-stu-id="c0e36-114">To layer controls programmatically</span></span>  
  
-   <span data-ttu-id="c0e36-115">使用して、<xref:System.Windows.Forms.Control.BringToFront%2A>と<xref:System.Windows.Forms.Control.SendToBack%2A>コントロールの z オーダーを操作するメソッド。</span><span class="sxs-lookup"><span data-stu-id="c0e36-115">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>  
  
     <span data-ttu-id="c0e36-116">たとえば場合、<xref:System.Windows.Forms.TextBox>コントロール、`txtFirstName`はすぐ下に別制御したい場合一番上にある、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="c0e36-116">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="c0e36-117">Windows フォームをサポートしている*コントロール コンテインメント*です。</span><span class="sxs-lookup"><span data-stu-id="c0e36-117">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="c0e36-118">コントロール コンテインメントの数などのコンテナー コントロール内のコントロールの数に配置する<xref:System.Windows.Forms.RadioButton>内で制御、<xref:System.Windows.Forms.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="c0e36-118">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="c0e36-119">コントロールを格納しているコントロール内で、階層化することができます。</span><span class="sxs-lookup"><span data-stu-id="c0e36-119">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="c0e36-120">グループ化するボックスを移動すると、その内部に格納されているためにも、コントロールが移動します。</span><span class="sxs-lookup"><span data-stu-id="c0e36-120">Moving the group box moves the controls as well, because they are contained inside it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e36-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0e36-121">See Also</span></span>  
 [<span data-ttu-id="c0e36-122">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="c0e36-122">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="c0e36-123">Windows フォームでのコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="c0e36-123">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="c0e36-124">各 Windows フォーム コントロールのラベル設定とショートカットの作成</span><span class="sxs-lookup"><span data-stu-id="c0e36-124">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="c0e36-125">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="c0e36-125">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="c0e36-126">Windows フォーム コントロールの機能別一覧</span><span class="sxs-lookup"><span data-stu-id="c0e36-126">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
