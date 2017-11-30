---
title: "チュートリアル : Visual Basic による複合コントロールの作成"
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
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c86a3d420b85c1287597cda738c6d72f0433d0f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a><span data-ttu-id="04811-102">チュートリアル : Visual Basic による複合コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="04811-102">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>
<span data-ttu-id="04811-103">複合コントロールは、カスタム グラフィカル インターフェイスを作成し、再利用するための手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="04811-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="04811-104">複合コントロールは、基本的には視覚的に表示されるコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="04811-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="04811-105">そのため、複合コントロールは、1 つ以上の Windows フォーム コントロール、コンポーネント、または機能を拡張できるコード ブロックで構成されます。コード ブロックでは、ユーザー入力の検証、表示プロパティの変更、作成者が必要とする他のタスクの実行などによって機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="04811-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="04811-106">複合コントロールは、他のコントロールと同様に Windows フォームに配置できます。</span><span class="sxs-lookup"><span data-stu-id="04811-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="04811-107">このチュートリアルの前半では、`ctlClock` という単純な複合コントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="04811-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="04811-108">チュートリアルの後半では、継承によって `ctlClock` の機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="04811-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04811-109">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="04811-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="04811-110">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="04811-111">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04811-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="04811-112">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="04811-112">Creating the Project</span></span>  
 <span data-ttu-id="04811-113">新しいプロジェクトを作成するときは、ルート名前空間、アセンブリ名、プロジェクト名を設定し、既定のコンポーネントが適切な名前空間に含まれるようにするために、プロジェクトの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="04811-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="04811-114">ctlClockLib コントロール ライブラリと ctlClock コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="04811-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1.  <span data-ttu-id="04811-115">**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックして **[新しいプロジェクト]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="04811-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="04811-116">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] プロジェクトの一覧で、**[Windows コントロール ライブラリ]** プロジェクト テンプレートを選択し、**[名前]** ボックスに「`ctlClockLib`」と入力して、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-116">From the list of [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] projects, select the **Windows Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="04811-117">プロジェクト名 `ctlClockLib` は、既定でルート名前空間にも割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="04811-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="04811-118">ルート名前空間は、アセンブリ内のコンポーネント名の修飾に使用されます。</span><span class="sxs-lookup"><span data-stu-id="04811-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="04811-119">たとえば、`ctlClock` という名前のコンポーネントが 2 つのアセンブリに含まれている場合、`ctlClockLib.ctlClock.` を使用して目的の `ctlClock` コンポーネントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="04811-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>  
  
3.  <span data-ttu-id="04811-120">ソリューション エクスプローラーで、**[UserControl1.vb]** を右クリックし、**[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-120">In Solution Explorer, right-click **UserControl1.vb**, and then click **Rename**.</span></span> <span data-ttu-id="04811-121">ファイル名を `ctlClock.vb` に変更します。</span><span class="sxs-lookup"><span data-stu-id="04811-121">Change the file name to `ctlClock.vb`.</span></span> <span data-ttu-id="04811-122">コード要素 "UserControl1" へのすべての参照の名前を変更するかどうかをたずねられたら、**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04811-123">既定では、複合コントロールを継承から、<xref:System.Windows.Forms.UserControl>システムによって提供されるクラスです。</span><span class="sxs-lookup"><span data-stu-id="04811-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="04811-124"><xref:System.Windows.Forms.UserControl>クラスは、すべての複合コントロールに必要な機能を提供し、標準的なメソッドとプロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="04811-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4.  <span data-ttu-id="04811-125">**[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="04811-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="04811-126">複合コントロールへの Windows コントロールとコンポーネントの追加</span><span class="sxs-lookup"><span data-stu-id="04811-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="04811-127">ビジュアル インターフェイスは、複合コントロールに不可欠な部分です。</span><span class="sxs-lookup"><span data-stu-id="04811-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="04811-128">このビジュアル インターフェイスは、デザイナー画面に 1 つ以上の Windows コントロールを追加することによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="04811-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="04811-129">次の例では、複合コントロールに Windows コントロールを組み込み、機能を実装するコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="04811-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="04811-130">複合コントロールに Label と Timer を追加するには</span><span class="sxs-lookup"><span data-stu-id="04811-130">To add a Label and a Timer to your composite control</span></span>  
  
1.  <span data-ttu-id="04811-131">ソリューション エクスプローラーで、**[ctlClock.vb]** を右クリックし、**[デザイナーの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-131">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="04811-132">ツールボックスの **[コモン コントロール]** ノードを展開し、**[Label]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-132">In the Toolbox, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="04811-133">A<xref:System.Windows.Forms.Label>という名前のコントロール`Label1`デザイナー画面上のコントロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="04811-133">A <xref:System.Windows.Forms.Label> control named `Label1` is added to your control on the designer surface.</span></span>  
  
3.  <span data-ttu-id="04811-134">デザイナーで **[Label1]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-134">In the designer, click **Label1**.</span></span> <span data-ttu-id="04811-135">[プロパティ] ウィンドウで、次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="04811-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="04811-136">プロパティ</span><span class="sxs-lookup"><span data-stu-id="04811-136">Property</span></span>|<span data-ttu-id="04811-137">変更後の値</span><span class="sxs-lookup"><span data-stu-id="04811-137">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="04811-138">**名前**</span><span class="sxs-lookup"><span data-stu-id="04811-138">**Name**</span></span>|`lblDisplay`|  
    |<span data-ttu-id="04811-139">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="04811-139">**Text**</span></span>|`(blank space)`|  
    |<span data-ttu-id="04811-140">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="04811-140">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="04811-141">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="04811-141">**Font.Size**</span></span>|`14`|  
  
4.  <span data-ttu-id="04811-142">**ツールボックス**の **[コンポーネント]** ノードを展開し、**[Timer]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="04811-143"><xref:System.Windows.Forms.Timer>コンポーネントは、実行時に視覚的表現がありません。</span><span class="sxs-lookup"><span data-stu-id="04811-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="04811-144">そのため、コントロールと共にデザイナー画面に表示されるのではなく、コンポーネント デザイナー (デザイナー画面の下部にあるトレイ) に表示されます。</span><span class="sxs-lookup"><span data-stu-id="04811-144">Therefore, it does not appear with the controls on the designer surface, but rather in the Component Designer (a tray at the bottom of the designer surface).</span></span>  
  
5.  <span data-ttu-id="04811-145">コンポーネント デザイナーで、をクリックして**Timer1**、し、設定、<xref:System.Windows.Forms.Timer.Interval%2A>プロパティを`1000`と<xref:System.Windows.Forms.Timer.Enabled%2A>プロパティを`True`です。</span><span class="sxs-lookup"><span data-stu-id="04811-145">In the Component Designer, click **Timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `True`.</span></span>  
  
     <span data-ttu-id="04811-146"><xref:System.Windows.Forms.Timer.Interval%2A>プロパティを timer コンポーネント タイマー刻みの頻度を制御します。</span><span class="sxs-lookup"><span data-stu-id="04811-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the timer component ticks.</span></span> <span data-ttu-id="04811-147">`Timer1` が時を刻むたびに、`Timer1_Tick` イベントのコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="04811-147">Each time `Timer1` ticks, it runs the code in the `Timer1_Tick` event.</span></span> <span data-ttu-id="04811-148">このプロパティは、タイマーの刻み間隔をミリ秒単位で表します。</span><span class="sxs-lookup"><span data-stu-id="04811-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6.  <span data-ttu-id="04811-149">コンポーネント デザイナーで **[Timer1]** をダブルクリックして、`ctlClock` の `Timer1_Tick` イベントに移動します。</span><span class="sxs-lookup"><span data-stu-id="04811-149">In the Component Designer, double-click **Timer1** to go to the `Timer1_Tick` event for `ctlClock`.</span></span>  
  
7.  <span data-ttu-id="04811-150">コードを次のコード サンプルのように変更します。</span><span class="sxs-lookup"><span data-stu-id="04811-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="04811-151">アクセス修飾子を `Private` から `Protected` に必ず変更してください。</span><span class="sxs-lookup"><span data-stu-id="04811-151">Be sure to change the access modifier from `Private` to `Protected`.</span></span>  
  
    ```vb  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     <span data-ttu-id="04811-152">このコードにより、現在の時刻が `lblDisplay` に表示されます。</span><span class="sxs-lookup"><span data-stu-id="04811-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="04811-153">`Timer1` の間隔が `1000` に設定されているため、このイベントは 1000 ミリ秒ごとに発生します。したがって、現在の時刻が 1 秒ごとに更新されます。</span><span class="sxs-lookup"><span data-stu-id="04811-153">Because the interval of `Timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8.  <span data-ttu-id="04811-154">メソッドをオーバーライド可能に変更します。</span><span class="sxs-lookup"><span data-stu-id="04811-154">Modify the method to be overridable.</span></span> <span data-ttu-id="04811-155">詳細については、後述の「複合コントロールの継承」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04811-155">For more information, see the "Inheriting from a User Control" section below.</span></span>  
  
    ```vb  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. <span data-ttu-id="04811-156">**[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="04811-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="04811-157">複合コントロールへのプロパティの追加</span><span class="sxs-lookup"><span data-stu-id="04811-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="04811-158">時計コントロールを今すぐカプセル化、<xref:System.Windows.Forms.Label>コントロールと<xref:System.Windows.Forms.Timer>それぞれ固有のプロパティの独自のセットを持つコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="04811-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="04811-159">時計コントロールを今後使用するユーザーは、これらのコントロールの個々のプロパティにアクセスすることはできませんが、適切なコード ブロックを記述することで、カスタム プロパティを作成して公開できます。</span><span class="sxs-lookup"><span data-stu-id="04811-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="04811-160">次の手順では、ユーザーが背景とテキストの色を変更できるようにするプロパティをコントロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="04811-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="04811-161">複合コントロールにプロパティを追加するには</span><span class="sxs-lookup"><span data-stu-id="04811-161">To add a property to your composite control</span></span>  
  
1.  <span data-ttu-id="04811-162">ソリューション エクスプローラーで、**[ctlClock.vb]** を右クリックし、**[コードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-162">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="04811-163">コントロールのコード エディターが開きます。</span><span class="sxs-lookup"><span data-stu-id="04811-163">The Code Editor for your control opens.</span></span>  
  
2.  <span data-ttu-id="04811-164">`Public Class ctlClock` ステートメントを探します。</span><span class="sxs-lookup"><span data-stu-id="04811-164">Locate the `Public Class ctlClock` statement.</span></span> <span data-ttu-id="04811-165">このステートメントの下に、次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="04811-165">Beneath it, type the following code.</span></span>  
  
    ```vb  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     <span data-ttu-id="04811-166">これらのステートメントにより、作成するプロパティの値の格納に使用するプライベート変数が作成されます。</span><span class="sxs-lookup"><span data-stu-id="04811-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3.  <span data-ttu-id="04811-167">手順 2. の変数の宣言の下に次のコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="04811-167">Insert the following code beneath the variable declarations from step 2.</span></span>  
  
    ```vb  
    ' Declares the name and type of the property.  
    Property ClockBackColor() as Color  
        ' Retrieves the value of the private variable colBColor.  
        Get  
            Return colBColor  
        End Get  
        ' Stores the selected value in the private variable colBColor, and   
        ' updates the background color of the label control lblDisplay.  
        Set(ByVal value as Color)  
            colBColor = value  
            lblDisplay.BackColor = colBColor     
        End Set  
  
    End Property  
    ' Provides a similar set of instructions for the foreground color.  
    Property ClockForeColor() as Color  
        Get  
            Return colFColor  
        End Get  
        Set(ByVal value as Color)  
            colFColor = value  
            lblDisplay.ForeColor = colFColor  
        End Set  
    End Property  
    ```  
  
     <span data-ttu-id="04811-168">上記のコードは、`Property` ステートメントを呼び出すことによって、このコントロールを今後使用するユーザーが、`ClockForeColor` と `ClockBackColor` の 2 つのカスタム プロパティを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="04811-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control by invoking the `Property` statement.</span></span> <span data-ttu-id="04811-169">`Get` ステートメントと `Set` ステートメントは、プロパティ値を格納および取得できるようにし、そのプロパティに適した機能を実装するコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="04811-169">The `Get` and `Set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4.  <span data-ttu-id="04811-170">**[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="04811-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="04811-171">コントロールのテスト</span><span class="sxs-lookup"><span data-stu-id="04811-171">Testing the Control</span></span>  
 <span data-ttu-id="04811-172">コントロールはスタンドアロン プロジェクトではないため、コンテナー内でホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="04811-172">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="04811-173">**UserControl Test Container** でコントロールの実行時の動作をテストし、プロパティを実行します。</span><span class="sxs-lookup"><span data-stu-id="04811-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="04811-174">詳細については、「[方法: UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04811-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="04811-175">コントロールをテストするには</span><span class="sxs-lookup"><span data-stu-id="04811-175">To test your control</span></span>  
  
1.  <span data-ttu-id="04811-176">F5 キーを押してプロジェクトをビルドし、**UserControl Test Container** でコントロールを実行します。</span><span class="sxs-lookup"><span data-stu-id="04811-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="04811-177">テスト コンテナーのプロパティ グリッドで、`ClockBackColor` プロパティを選択し、ドロップダウン矢印をクリックしてカラー パレットを表示します。</span><span class="sxs-lookup"><span data-stu-id="04811-177">In the test container's property grid, select the `ClockBackColor` property, and then click the drop-down arrow to display the color palette.</span></span>  
  
3.  <span data-ttu-id="04811-178">任意の色をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="04811-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="04811-179">コントロールの背景色が選択した色に変更されます。</span><span class="sxs-lookup"><span data-stu-id="04811-179">The background color of your control changes to the color you selected.</span></span>  
  
4.  <span data-ttu-id="04811-180">同様のイベント シーケンスを使用して、`ClockForeColor` プロパティが予想どおりに機能していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="04811-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
5.  <span data-ttu-id="04811-181">**[閉じる]** をクリックして、**UserControl Test Container** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="04811-181">Click **Close** to close the **UserControl Test Container**.</span></span>  
  
     <span data-ttu-id="04811-182">このセクションとこれまでのセクションでは、コンポーネントと Windows コントロールをコードと組み合わせてパッケージ化し、複合コントロールの形でカスタム機能を提供する方法を説明しました。</span><span class="sxs-lookup"><span data-stu-id="04811-182">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="04811-183">また、複合コントロールのプロパティを公開し、完了後にコントロールをテストする方法も説明しました。</span><span class="sxs-lookup"><span data-stu-id="04811-183">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="04811-184">次のセクションでは、`ctlClock` をベースとして使用して、継承された複合コントロールを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="04811-184">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="04811-185">複合コントロールの継承</span><span class="sxs-lookup"><span data-stu-id="04811-185">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="04811-186">これまでのセクションでは、Windows コントロール、コンポーネント、コードを組み合わせて、再利用可能な複合コントロールを作成する方法を説明しました。</span><span class="sxs-lookup"><span data-stu-id="04811-186">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="04811-187">作成した複合コントロールをベースとして使用して、他のコントロールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="04811-187">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="04811-188">基本クラスからクラスを派生するプロセスは "*継承*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="04811-188">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="04811-189">このセクションでは、`ctlAlarmClock` という複合コントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="04811-189">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="04811-190">このコントロールは、親コントロールである `ctlClock` から派生します。</span><span class="sxs-lookup"><span data-stu-id="04811-190">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="04811-191">ここでは、親のメソッドをオーバーライドし、新しいメソッドとプロパティを追加して、`ctlClock` の機能を拡張する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="04811-191">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="04811-192">継承されたコントロールを作成するには、まず、親から派生します。</span><span class="sxs-lookup"><span data-stu-id="04811-192">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="04811-193">これにより、親コントロールのプロパティ、メソッド、グラフィカル特性をすべて備えた新しいコントロールが作成されます。このコントロールをベースとして使用して、新しい機能や変更された機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="04811-193">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="04811-194">継承されたコントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="04811-194">To create the inherited control</span></span>  
  
1.  <span data-ttu-id="04811-195">ソリューション エクスプローラーで、**[ctlClockLib]** を右クリックし、**[追加]** をポイントして、**[ユーザー コントロール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-195">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="04811-196">**[新しい項目の追加]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="04811-196">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="04811-197">**[継承されたユーザー コントロール]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="04811-197">Select the **Inherited User Control** template.</span></span>  
  
3.  <span data-ttu-id="04811-198">**[名前]** ボックスに「`ctlAlarmClock.vb`」と入力し、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-198">In the **Name** box, type `ctlAlarmClock.vb`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="04811-199">**[継承ピッカー]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="04811-199">The **Inheritance Picker** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="04811-200">**[コンポーネント名]** の **[ctlClock]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-200">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5.  <span data-ttu-id="04811-201">ソリューション エクスプローラーで、現在のプロジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="04811-201">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04811-202">現在のプロジェクトに、**ctlAlarmClock.vb** というファイルが追加されています。</span><span class="sxs-lookup"><span data-stu-id="04811-202">A file called **ctlAlarmClock.vb** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="04811-203">アラームのプロパティの追加</span><span class="sxs-lookup"><span data-stu-id="04811-203">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="04811-204">複合コントロールにプロパティを追加する場合と同様に、継承されたコントロールにプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="04811-204">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="04811-205">ここでは、プロパティ宣言の構文を使用して、コントロールに 2 つのプロパティを追加します。`AlarmTime` プロパティは、アラームを鳴らす日時の値を格納し、`AlarmSet` プロパティは、アラームが設定されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="04811-205">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="04811-206">複合コントロールにプロパティを追加するには</span><span class="sxs-lookup"><span data-stu-id="04811-206">To add properties to your composite control</span></span>  
  
1.  <span data-ttu-id="04811-207">ソリューション エクスプローラーで、**[ctlAlarmClock]** を右クリックし、**[コードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-207">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="04811-208">ctlAlarmClock コントロールのクラスの宣言を探します。これは、`Public Class ctlAlarmClock` と表示されています。</span><span class="sxs-lookup"><span data-stu-id="04811-208">Locate the class declaration for the ctlAlarmClock control, which appears as `Public Class ctlAlarmClock`.</span></span>  <span data-ttu-id="04811-209">クラスの宣言に次のコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="04811-209">In the class declaration, insert the following code.</span></span>  
  
    ```vb  
    Private dteAlarmTime As Date  
    Private blnAlarmSet As Boolean  
    ' These properties will be declared as Public to allow future   
    ' developers to access them.  
    Public Property AlarmTime() As Date  
        Get  
            Return dteAlarmTime  
        End Get  
        Set(ByVal value as Date)  
            dteAlarmTime = value  
        End Set  
    End Property  
    Public Property AlarmSet() As Boolean  
        Get  
            Return blnAlarmSet  
        End Get  
        Set(ByVal value as Boolean)  
            blnAlarmSet = value  
        End Set  
    End Property  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="04811-210">コントロールのグラフィカル インターフェイスへの追加</span><span class="sxs-lookup"><span data-stu-id="04811-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="04811-211">継承されたコントロールには、継承元のコントロールと同じビジュアル インターフェイスがあります。</span><span class="sxs-lookup"><span data-stu-id="04811-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="04811-212">継承されたコントロールは親コントロールと同じ内在コントロールを持ちますが、内在コントロールのプロパティは、明確に公開されていない限り使用できません。</span><span class="sxs-lookup"><span data-stu-id="04811-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="04811-213">複合コントロールに追加する場合と同様に、継承された複合コントロールのグラフィカル インターフェイスに追加できます。</span><span class="sxs-lookup"><span data-stu-id="04811-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="04811-214">引き続き、アラーム時計のビジュアル インターフェイスに、アラームが鳴っているときに点滅するラベル コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="04811-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="04811-215">ラベル コントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="04811-215">To add the label control</span></span>  
  
1.  <span data-ttu-id="04811-216">ソリューション エクスプローラーで、**[ctlAlarmClock]** を右クリックし、**[デザイナーの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-216">In Solution Explorer, right-click **ctlAlarmClock**, and click **View Designer**.</span></span>  
  
     <span data-ttu-id="04811-217">メイン ウィンドウに、`ctlAlarmClock` のデザイナーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="04811-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2.  <span data-ttu-id="04811-218">`lblDisplay` (コントロールの表示部分) をクリックし、[プロパティ] ウィンドウを表示します。</span><span class="sxs-lookup"><span data-stu-id="04811-218">Click `lblDisplay` (the display portion of the control), and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04811-219">すべてのプロパティが表示されていますが、淡色表示になっています。</span><span class="sxs-lookup"><span data-stu-id="04811-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="04811-220">これは、これらのプロパティが `lblDisplay` に対してネイティブであり、[プロパティ] ウィンドウで変更したりアクセスしたりすることはできないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="04811-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="04811-221">既定では、複合コントロールに含まれているコントロールは `Private` であり、どのような方法でもプロパティにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="04811-221">By default, controls contained in a composite control are `Private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04811-222">複合コントロールを今後使用するユーザーが、その内部のコントロールにアクセスできるようにする場合は、内部のコントロールを `Public` または `Protected` として宣言します。</span><span class="sxs-lookup"><span data-stu-id="04811-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `Public` or `Protected`.</span></span> <span data-ttu-id="04811-223">これにより、適切なコードを使用して、複合コントロールに含まれているコントロールのプロパティの設定や変更が可能になります。</span><span class="sxs-lookup"><span data-stu-id="04811-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3.  <span data-ttu-id="04811-224">追加、<xref:System.Windows.Forms.Label>複合コントロールを制御します。</span><span class="sxs-lookup"><span data-stu-id="04811-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4.  <span data-ttu-id="04811-225">使用して、マウスをドラッグ、 <xref:System.Windows.Forms.Label> [表示] ボックスのすぐ下にあるコントロールです。</span><span class="sxs-lookup"><span data-stu-id="04811-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="04811-226">[プロパティ] ウィンドウで、次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="04811-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="04811-227">プロパティ</span><span class="sxs-lookup"><span data-stu-id="04811-227">Property</span></span>|<span data-ttu-id="04811-228">設定</span><span class="sxs-lookup"><span data-stu-id="04811-228">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="04811-229">**名前**</span><span class="sxs-lookup"><span data-stu-id="04811-229">**Name**</span></span>|`lblAlarm`|  
    |<span data-ttu-id="04811-230">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="04811-230">**Text**</span></span>|<span data-ttu-id="04811-231">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="04811-231">**Alarm!**</span></span>|  
    |<span data-ttu-id="04811-232">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="04811-232">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="04811-233">**Visible**</span><span class="sxs-lookup"><span data-stu-id="04811-233">**Visible**</span></span>|`False`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="04811-234">アラーム機能の追加</span><span class="sxs-lookup"><span data-stu-id="04811-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="04811-235">前の手順では、複合コントロールでアラーム機能を有効にするためのプロパティとコントロールを追加しました。</span><span class="sxs-lookup"><span data-stu-id="04811-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="04811-236">この手順では、現在の時刻をアラームの時刻と比較して、2 つの時刻が同じである場合にアラームを鳴らして点滅させるコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="04811-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to sound and flash an alarm.</span></span> <span data-ttu-id="04811-237">`ctlClock` の `Timer1_Tick` メソッドをオーバーライドし、コードを追加することで、`ctlClock` の固有の機能をすべて保持しながら、`ctlAlarmClock` の機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="04811-237">By overriding the `Timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="04811-238">ctlClock の Timer1_Tick メソッドをオーバーライドするには</span><span class="sxs-lookup"><span data-stu-id="04811-238">To override the Timer1_Tick method of ctlClock</span></span>  
  
1.  <span data-ttu-id="04811-239">ソリューション エクスプローラーで、**[ctlAlarmClock.vb]** を右クリックし、**[コードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-239">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="04811-240">`Private blnAlarmSet As Boolean` ステートメントを探します。</span><span class="sxs-lookup"><span data-stu-id="04811-240">Locate the `Private blnAlarmSet As Boolean` statement.</span></span> <span data-ttu-id="04811-241">このステートメントのすぐ下に、次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="04811-241">Immediately beneath it, add the following statement.</span></span>  
  
    ```vb  
    Dim blnColorTicker as Boolean  
    ```  
  
3.  <span data-ttu-id="04811-242">ページの下部にある `End Class` ステートメントを探します。</span><span class="sxs-lookup"><span data-stu-id="04811-242">Locate the `End Class` statement at the bottom of the page.</span></span> <span data-ttu-id="04811-243">`End Class` ステートメントの直前に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="04811-243">Just before the `End Class` statement, add the following code.</span></span>  
  
    ```vb  
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _  
        As System.EventArgs)  
        ' Calls the Timer1_Tick method of ctlClock.  
        MyBase.Timer1_Tick(sender, e)  
        ' Checks to see if the Alarm is set.  
        If AlarmSet = False Then  
            Exit Sub  
        End If  
        ' If the date, hour, and minute of the alarm time are the same as  
        ' now, flash and beep an alarm.   
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _  
            AlarmTime.Minute = Now.Minute Then  
            ' Sounds an audible beep.  
            Beep()  
            ' Sets lblAlarmVisible to True, and changes the background color based on the   
            ' value of blnColorTicker. The background color of the label will   
            ' flash once per tick of the clock.  
            lblAlarm.Visible = True  
            If blnColorTicker = False Then  
                lblAlarm.BackColor = Color.PeachPuff  
                blnColorTicker = True  
            Else  
                lblAlarm.BackColor = Color.Plum  
                blnColorTicker = False  
            End If  
        Else  
            ' Once the alarm has sounded for a minute, the label is made   
            ' invisible again.  
            lblAlarm.Visible = False  
        End If  
    End Sub  
    ```  
  
     <span data-ttu-id="04811-244">このコードを追加すると、いくつかのタスクが実行されます。</span><span class="sxs-lookup"><span data-stu-id="04811-244">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="04811-245">`Overrides` ステートメントは、基本コントロールから継承されたメソッドの代わりに、このメソッドを使用するようコントロールに指示します。</span><span class="sxs-lookup"><span data-stu-id="04811-245">The `Overrides` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="04811-246">このメソッドが呼び出されると、メソッドは `MyBase.Timer1_Tick` ステートメントを呼び出して、オーバーライドしたメソッドを呼び出します。これにより、元のコントロールに組み込まれたすべての機能がこのコントロールに継承されます。</span><span class="sxs-lookup"><span data-stu-id="04811-246">When this method is called, it calls the method it overrides by invoking the `MyBase.Timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="04811-247">その後、メソッドは追加のコードを実行してアラーム機能を組み込みます。</span><span class="sxs-lookup"><span data-stu-id="04811-247">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="04811-248">アラームが発生すると、点滅するラベル コントロールが表示され、ビープ音が聞こえます。</span><span class="sxs-lookup"><span data-stu-id="04811-248">A flashing label control will appear when the alarm occurs, and an audible beep will be heard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04811-249">継承されたイベント ハンドラーをオーバーライドしているので、`Handles` キーワードでイベントを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="04811-249">Because you are overriding an inherited event handler, you do not have to specify the event with the `Handles` keyword.</span></span> <span data-ttu-id="04811-250">イベントは既にフックされています。</span><span class="sxs-lookup"><span data-stu-id="04811-250">The event is already hooked up.</span></span> <span data-ttu-id="04811-251">オーバーライドしているのはハンドラーの実装です。</span><span class="sxs-lookup"><span data-stu-id="04811-251">All you are overriding is the implementation of the handler.</span></span>  
  
     <span data-ttu-id="04811-252">これで、アラーム時計コントロールはほぼ完成です。</span><span class="sxs-lookup"><span data-stu-id="04811-252">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="04811-253">あとはアラームを止める方法を実装するだけです。</span><span class="sxs-lookup"><span data-stu-id="04811-253">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="04811-254">これを行うには、`lblAlarm_Click` メソッドにコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="04811-254">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="04811-255">停止メソッドを実装するには</span><span class="sxs-lookup"><span data-stu-id="04811-255">To implement the shutoff method</span></span>  
  
1.  <span data-ttu-id="04811-256">ソリューション エクスプローラーで、**[ctlAlarmClock.vb]** を右クリックし、**[デザイナーの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-256">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="04811-257">デザイナーで **[lblAlarm]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-257">In the designer, double-click **lblAlarm**.</span></span> <span data-ttu-id="04811-258">**コード エディター**が開き、`Private Sub lblAlarm_Click` 行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="04811-258">The **Code Editor** opens to the `Private Sub lblAlarm_Click` line.</span></span>  
  
3.  <span data-ttu-id="04811-259">このメソッドを次のコードのように変更します。</span><span class="sxs-lookup"><span data-stu-id="04811-259">Modify this method so that it resembles the following code.</span></span>  
  
    ```vb  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4.  <span data-ttu-id="04811-260">**[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="04811-260">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="04811-261">フォームでの継承されたコントロールの使用</span><span class="sxs-lookup"><span data-stu-id="04811-261">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="04811-262">継承されたコントロールは、基本クラスのコントロールである `ctlClock` をテストしたときと同様にテストできます。F5 キーを押してプロジェクトをビルドし、**UserControl Test Container** でコントロールを実行します。</span><span class="sxs-lookup"><span data-stu-id="04811-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="04811-263">詳細については、「[方法: UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04811-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="04811-264">コントロールを使用するには、フォーム上でコントロールをホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="04811-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="04811-265">標準の複合コントロールと同様に、継承された複合コントロールをスタンドアロンにすることはできないので、フォームまたは他のコンテナー内でホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="04811-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="04811-266">`ctlAlarmClock` は機能が拡張されているため、テストするには追加のコードが必要となります。</span><span class="sxs-lookup"><span data-stu-id="04811-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="04811-267">次の手順では、`ctlAlarmClock` の機能をテストするための簡単なプログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="04811-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="04811-268">`ctlAlarmClock` の `AlarmTime` プロパティを設定して表示するコードを記述し、固有の機能をテストします。</span><span class="sxs-lookup"><span data-stu-id="04811-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="04811-269">コントロールをビルドしてテスト フォームに追加するには</span><span class="sxs-lookup"><span data-stu-id="04811-269">To build and add your control to a test form</span></span>  
  
1.  <span data-ttu-id="04811-270">ソリューション エクスプローラーで、**[ctlClockLib]** を右クリックし、**[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-270">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="04811-271">**[ファイル]** メニューの **[追加]**をポイントし、 **[新しいプロジェクト]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-271">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>  
  
3.  <span data-ttu-id="04811-272">新しい **Windows アプリケーション** プロジェクトをソリューションに追加し、`Test` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="04811-272">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
     <span data-ttu-id="04811-273">ソリューション エクスプローラーに **Test** プロジェクトが追加されます。</span><span class="sxs-lookup"><span data-stu-id="04811-273">The **Test** project is added to Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="04811-274">ソリューション エクスプローラーで、`Test` プロジェクト ノードを右クリックし、**[参照の追加]** をクリックして **[参照の追加]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="04811-274">In Solution Explorer, right-click the `Test` project node, and then click **Add Reference** to display the **Add Reference** dialog box.</span></span>  
  
5.  <span data-ttu-id="04811-275">**[プロジェクト]** というラベルのタブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-275">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="04811-276">**[プロジェクト名]** に **ctlClockLib** プロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="04811-276">The project **ctlClockLib** will be listed under **Project Name**.</span></span> <span data-ttu-id="04811-277">**[ctlClockLib]** をダブルクリックして、テスト プロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="04811-277">Double-click **ctlClockLib** to add the reference to the test project.</span></span>  
  
6.  <span data-ttu-id="04811-278">ソリューション エクスプローラーで、**[Test]** を右クリックし、**[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-278">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
7.  <span data-ttu-id="04811-279">**ツールボックス**で、**[ctlClockLib コンポーネント]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="04811-279">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
8.  <span data-ttu-id="04811-280">**[ctlAlarmClock]** をダブルクリックして、`ctlAlarmClock` のインスタンスをフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="04811-280">Double-click **ctlAlarmClock** to add an instance of `ctlAlarmClock` to your form.</span></span>  
  
9. <span data-ttu-id="04811-281">**ツールボックス**を特定し、ダブルクリック、 **DateTimePicker**を追加する、<xref:System.Windows.Forms.DateTimePicker>をフォームに制御し、追加、<xref:System.Windows.Forms.Label>コントロールをダブルクリックして**ラベル**.</span><span class="sxs-lookup"><span data-stu-id="04811-281">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
10. <span data-ttu-id="04811-282">マウスを使用して、各コントロールをフォーム上の使いやすい場所に配置します。</span><span class="sxs-lookup"><span data-stu-id="04811-282">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
11. <span data-ttu-id="04811-283">これらのコントロールのプロパティを次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="04811-283">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="04811-284">コントロール</span><span class="sxs-lookup"><span data-stu-id="04811-284">Control</span></span>|<span data-ttu-id="04811-285">プロパティ</span><span class="sxs-lookup"><span data-stu-id="04811-285">Property</span></span>|<span data-ttu-id="04811-286">値</span><span class="sxs-lookup"><span data-stu-id="04811-286">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|<span data-ttu-id="04811-287">**テキスト**</span><span class="sxs-lookup"><span data-stu-id="04811-287">**Text**</span></span>|`(blank space)`|  
    ||<span data-ttu-id="04811-288">**名前**</span><span class="sxs-lookup"><span data-stu-id="04811-288">**Name**</span></span>|`lblTest`|  
    |`dateTimePicker1`|<span data-ttu-id="04811-289">**名前**</span><span class="sxs-lookup"><span data-stu-id="04811-289">**Name**</span></span>|`dtpTest`|  
    ||<span data-ttu-id="04811-290">**Format**</span><span class="sxs-lookup"><span data-stu-id="04811-290">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
12. <span data-ttu-id="04811-291">デザイナーで **[dtpTest]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-291">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="04811-292">**コード エディター**が開き、`Private Sub dtpTest_ValueChanged` が表示されます。</span><span class="sxs-lookup"><span data-stu-id="04811-292">The **Code Editor** opens to `Private Sub dtpTest_ValueChanged`.</span></span>  
  
13. <span data-ttu-id="04811-293">コードを次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="04811-293">Modify the code so that it resembles the following.</span></span>  
  
    ```vb  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. <span data-ttu-id="04811-294">ソリューション エクスプローラーで、**[Test]** を右クリックし、**[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-294">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
15. <span data-ttu-id="04811-295">**[デバッグ]** メニューの **[デバッグの開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="04811-295">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="04811-296">テスト プログラムが起動します。</span><span class="sxs-lookup"><span data-stu-id="04811-296">The test program starts.</span></span> <span data-ttu-id="04811-297">現在の時刻が更新されるに注意してください、`ctlAlarmClock`制御、およびに開始時刻が表示されている、<xref:System.Windows.Forms.DateTimePicker>コントロール。</span><span class="sxs-lookup"><span data-stu-id="04811-297">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
16. <span data-ttu-id="04811-298">クリックして、<xref:System.Windows.Forms.DateTimePicker>時間 (分) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="04811-298">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
17. <span data-ttu-id="04811-299">キーボードを使用して、`ctlAlarmClock` に表示されている現在の時刻の 1 分後の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="04811-299">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="04811-300">アラーム設定の時刻が `lblTest` に表示されます。</span><span class="sxs-lookup"><span data-stu-id="04811-300">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="04811-301">表示時刻がアラーム設定時刻になるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="04811-301">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="04811-302">表示時刻がアラーム設定時刻になると、ビープ音が鳴り、`lblAlarm` が点滅します。</span><span class="sxs-lookup"><span data-stu-id="04811-302">When the displayed time reaches the time to which the alarm is set, the beep will sound and `lblAlarm` will flash.</span></span>  
  
18. <span data-ttu-id="04811-303">`lblAlarm` をクリックしてアラームを止めます。</span><span class="sxs-lookup"><span data-stu-id="04811-303">Turn off the alarm by clicking `lblAlarm`.</span></span> <span data-ttu-id="04811-304">これでアラームをリセットできます。</span><span class="sxs-lookup"><span data-stu-id="04811-304">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="04811-305">このチュートリアルでは、多数の重要な概念を取り上げました。</span><span class="sxs-lookup"><span data-stu-id="04811-305">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="04811-306">コントロールとコンポーネントを複合コントロール コンテナーに組み込んで複合コントロールを作成する方法を説明しました。</span><span class="sxs-lookup"><span data-stu-id="04811-306">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="04811-307">また、コントロールにプロパティを追加する方法と、カスタム機能を実装するコードを記述する方法も説明しました。</span><span class="sxs-lookup"><span data-stu-id="04811-307">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="04811-308">最後のセクションでは、継承によって特定の複合コントロールの機能を拡張する方法と、ホスト メソッドをオーバーライドすることでメソッドの機能を変更する方法を説明しました。</span><span class="sxs-lookup"><span data-stu-id="04811-308">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04811-309">関連項目</span><span class="sxs-lookup"><span data-stu-id="04811-309">See Also</span></span>  
 [<span data-ttu-id="04811-310">さまざまなカスタム コントロール</span><span class="sxs-lookup"><span data-stu-id="04811-310">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="04811-311">方法: 複合コントロールを作成する</span><span class="sxs-lookup"><span data-stu-id="04811-311">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 <span data-ttu-id="04811-312">[方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="04811-312">[How to: Display a Control in the Choose Toolbox Items Dialog Box](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span></span>  
 [<span data-ttu-id="04811-313">コンポーネント作成のチュートリアル</span><span class="sxs-lookup"><span data-stu-id="04811-313">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
