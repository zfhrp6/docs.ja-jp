---
title: 'チュートリアル : Visual C# による複合コントロールの作成'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c88a9b4786fd544d175243fedb56b5071c8990f6
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a><span data-ttu-id="f3e23-102">チュートリアル : Visual C# による複合コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="f3e23-102">Walkthrough: Authoring a Composite Control with Visual C#</span></span> #
<span data-ttu-id="f3e23-103">複合コントロールは、カスタム グラフィカル インターフェイスを作成し、再利用するための手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="f3e23-104">複合コントロールは、基本的には視覚的に表示されるコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="f3e23-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="f3e23-105">そのため、複合コントロールは、1 つ以上の Windows フォーム コントロール、コンポーネント、または機能を拡張できるコード ブロックで構成されます。コード ブロックでは、ユーザー入力の検証、表示プロパティの変更、作成者が必要とする他のタスクの実行などによって機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="f3e23-106">複合コントロールは、他のコントロールと同様に Windows フォームに配置できます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="f3e23-107">このチュートリアルの前半では、`ctlClock` という単純な複合コントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="f3e23-108">チュートリアルの後半では、継承によって `ctlClock` の機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3e23-109">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f3e23-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f3e23-110">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f3e23-111">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3e23-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="f3e23-112">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="f3e23-112">Creating the Project</span></span>  
 <span data-ttu-id="f3e23-113">新しいプロジェクトを作成するときは、ルート名前空間、アセンブリ名、プロジェクト名を設定し、既定のコンポーネントが適切な名前空間に含まれるようにするために、プロジェクトの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="f3e23-114">ctlClockLib コントロール ライブラリと ctlClock コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="f3e23-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1.  <span data-ttu-id="f3e23-115">**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックして **[新しいプロジェクト]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="f3e23-116">Visual c# プロジェクトのリストから、選択、 **Windows フォーム コントロール ライブラリ**プロジェクト テンプレート、型`ctlClockLib`で、**名前**ボックスし、をクリックして **[ok]** です。</span><span class="sxs-lookup"><span data-stu-id="f3e23-116">From the list of Visual C# projects, select the **Windows Forms Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="f3e23-117">プロジェクト名 `ctlClockLib` は、既定でルート名前空間にも割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="f3e23-118">ルート名前空間は、アセンブリ内のコンポーネント名の修飾に使用されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="f3e23-119">たとえば、`ctlClock` という名前のコンポーネントが 2 つのアセンブリに含まれている場合、`ctlClockLib.ctlClock.` を使用して目的の `ctlClock` コンポーネントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>  
  
3.  <span data-ttu-id="f3e23-120">ソリューション エクスプローラーで、**[UserControl1.cs]** を右クリックし、**[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-120">In Solution Explorer, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="f3e23-121">ファイル名を `ctlClock.cs` に変更します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-121">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="f3e23-122">コード要素 "UserControl1" へのすべての参照の名前を変更するかどうかをたずねられたら、**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f3e23-123">既定では、複合コントロールを継承から、<xref:System.Windows.Forms.UserControl>システムによって提供されるクラスです。</span><span class="sxs-lookup"><span data-stu-id="f3e23-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="f3e23-124"><xref:System.Windows.Forms.UserControl>クラスは、すべての複合コントロールに必要な機能を提供し、標準的なメソッドとプロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4.  <span data-ttu-id="f3e23-125">**[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="f3e23-126">複合コントロールへの Windows コントロールとコンポーネントの追加</span><span class="sxs-lookup"><span data-stu-id="f3e23-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="f3e23-127">ビジュアル インターフェイスは、複合コントロールに不可欠な部分です。</span><span class="sxs-lookup"><span data-stu-id="f3e23-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="f3e23-128">このビジュアル インターフェイスは、デザイナー画面に 1 つ以上の Windows コントロールを追加することによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="f3e23-129">次の例では、複合コントロールに Windows コントロールを組み込み、機能を実装するコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="f3e23-130">複合コントロールに Label と Timer を追加するには</span><span class="sxs-lookup"><span data-stu-id="f3e23-130">To add a Label and a Timer to your composite control</span></span>  
  
1.  <span data-ttu-id="f3e23-131">ソリューション エクスプローラーで、**[ctlClock.cs]** を右クリックし、**[デザイナーの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-131">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="f3e23-132">**ツールボックス**の **[コモン コントロール]** ノードを展開し、**[Label]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-132">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="f3e23-133">A<xref:System.Windows.Forms.Label>という名前のコントロール`label1`デザイナー画面上のコントロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-133">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>  
  
3.  <span data-ttu-id="f3e23-134">デザイナーで **[label1]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-134">In the designer, click **label1**.</span></span> <span data-ttu-id="f3e23-135">[プロパティ] ウィンドウで、次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="f3e23-136">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f3e23-136">Property</span></span>|<span data-ttu-id="f3e23-137">変更後の値</span><span class="sxs-lookup"><span data-stu-id="f3e23-137">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="f3e23-138">**Name**</span><span class="sxs-lookup"><span data-stu-id="f3e23-138">**Name**</span></span>|`lblDisplay`|  
    |<span data-ttu-id="f3e23-139">**[テキスト]**</span><span class="sxs-lookup"><span data-stu-id="f3e23-139">**Text**</span></span>|`(blank space)`|  
    |<span data-ttu-id="f3e23-140">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="f3e23-140">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="f3e23-141">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="f3e23-141">**Font.Size**</span></span>|`14`|  
  
4.  <span data-ttu-id="f3e23-142">**ツールボックス**の **[コンポーネント]** ノードを展開し、**[Timer]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="f3e23-143"><xref:System.Windows.Forms.Timer>コンポーネントは、実行時に視覚的表現がありません。</span><span class="sxs-lookup"><span data-stu-id="f3e23-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="f3e23-144">そのため、コントロールと共にデザイナー画面に表示されるのではなく、**コンポーネント デザイナー** (デザイナー画面の下部にあるトレイ) に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-144">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>  
  
5.  <span data-ttu-id="f3e23-145">**コンポーネント デザイナー**、 をクリックして**timer1**、し、設定、<xref:System.Windows.Forms.Timer.Interval%2A>プロパティを`1000`と<xref:System.Windows.Forms.Timer.Enabled%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="f3e23-145">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="f3e23-146"><xref:System.Windows.Forms.Timer.Interval%2A>プロパティは、頻度を制御、<xref:System.Windows.Forms.Timer>コンポーネントのタイマー刻み。</span><span class="sxs-lookup"><span data-stu-id="f3e23-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="f3e23-147">`timer1` が時を刻むたびに、`timer1_Tick` イベントのコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-147">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="f3e23-148">このプロパティは、タイマーの刻み間隔をミリ秒単位で表します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6.  <span data-ttu-id="f3e23-149">**コンポーネント デザイナー**で **[timer1]** をダブルクリックして、`ctlClock` の `timer1_Tick` イベントに移動します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-149">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>  
  
7.  <span data-ttu-id="f3e23-150">コードを次のコード サンプルのように変更します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="f3e23-151">アクセス修飾子を `private` から `protected` に必ず変更してください。</span><span class="sxs-lookup"><span data-stu-id="f3e23-151">Be sure to change the access modifier from `private` to `protected`.</span></span>  
  
    ```csharp  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     <span data-ttu-id="f3e23-152">このコードにより、現在の時刻が `lblDisplay` に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="f3e23-153">`timer1` の間隔が `1000` に設定されているため、このイベントは 1000 ミリ秒ごとに発生します。したがって、現在の時刻が 1 秒ごとに更新されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-153">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8.  <span data-ttu-id="f3e23-154">`virtual` キーワードを使用して、メソッドをオーバーライド可能に変更します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-154">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="f3e23-155">詳細については、後述の「複合コントロールの継承」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3e23-155">For more information, see the  "Inheriting from a User Control" section below.</span></span>  
  
    ```csharp  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. <span data-ttu-id="f3e23-156">**[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="f3e23-157">複合コントロールへのプロパティの追加</span><span class="sxs-lookup"><span data-stu-id="f3e23-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="f3e23-158">時計コントロールを今すぐカプセル化、<xref:System.Windows.Forms.Label>コントロールと<xref:System.Windows.Forms.Timer>それぞれ固有のプロパティの独自のセットを持つコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="f3e23-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="f3e23-159">時計コントロールを今後使用するユーザーは、これらのコントロールの個々のプロパティにアクセスすることはできませんが、適切なコード ブロックを記述することで、カスタム プロパティを作成して公開できます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="f3e23-160">次の手順では、ユーザーが背景とテキストの色を変更できるようにするプロパティをコントロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="f3e23-161">複合コントロールにプロパティを追加するには</span><span class="sxs-lookup"><span data-stu-id="f3e23-161">To add a property to your composite control</span></span>  
  
1.  <span data-ttu-id="f3e23-162">ソリューション エクスプローラーで、**[ctlClock.cs]** を右クリックし、**[コードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-162">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="f3e23-163">コントロールの**コード エディター**が開きます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-163">The **Code Editor** for your control opens.</span></span>  
  
2.  <span data-ttu-id="f3e23-164">`public partial class ctlClock` ステートメントを探します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-164">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="f3e23-165">左中かっこ (`{)` の下に次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-165">Beneath the opening brace (`{)`, type the following code.</span></span>  
  
    ```csharp  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     <span data-ttu-id="f3e23-166">これらのステートメントにより、作成するプロパティの値の格納に使用するプライベート変数が作成されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3.  <span data-ttu-id="f3e23-167">手順 2. の変数の宣言の下に次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-167">Type the following code beneath the variable declarations from step 2.</span></span>  
  
    ```csharp  
    // Declares the name and type of the property.  
    public Color ClockBackColor  
    {  
        // Retrieves the value of the private variable colBColor.  
        get  
        {  
            return colBColor;  
        }  
        // Stores the selected value in the private variable colBColor, and   
        // updates the background color of the label control lblDisplay.  
        set  
        {  
            colBColor = value;  
            lblDisplay.BackColor = colBColor;     
        }  
    }  
    // Provides a similar set of instructions for the foreground color.  
    public Color ClockForeColor  
    {  
        get  
        {  
            return colFColor;  
        }  
        set  
        {  
            colFColor = value;  
            lblDisplay.ForeColor = colFColor;  
        }  
    }  
    ```  
  
     <span data-ttu-id="f3e23-168">上記のコードは、このコントロールを今後使用するユーザーが、`ClockForeColor` と `ClockBackColor` の 2 つのカスタム プロパティを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="f3e23-169">`get` ステートメントと `set` ステートメントは、プロパティ値を格納および取得できるようにし、そのプロパティに適した機能を実装するコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-169">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4.  <span data-ttu-id="f3e23-170">**[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="f3e23-171">コントロールのテスト</span><span class="sxs-lookup"><span data-stu-id="f3e23-171">Testing the Control</span></span>  
 <span data-ttu-id="f3e23-172">コントロールはスタンドアロン アプリケーションではないため、コンテナー内でホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3e23-172">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="f3e23-173">**UserControl Test Container** でコントロールの実行時の動作をテストし、プロパティを実行します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="f3e23-174">詳細については、「[方法: UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3e23-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="f3e23-175">コントロールをテストするには</span><span class="sxs-lookup"><span data-stu-id="f3e23-175">To test your control</span></span>  
  
1.  <span data-ttu-id="f3e23-176">F5 キーを押してプロジェクトをビルドし、**UserControl Test Container** でコントロールを実行します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="f3e23-177">テスト コンテナーのプロパティ グリッドで、`ClockBackColor` プロパティを探し、このプロパティを選択してカラー パレットを表示します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-177">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>  
  
3.  <span data-ttu-id="f3e23-178">任意の色をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="f3e23-179">コントロールの背景色が選択した色に変更されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-179">The background color of your control changes to the color you selected.</span></span>  
  
4.  <span data-ttu-id="f3e23-180">同様のイベント シーケンスを使用して、`ClockForeColor` プロパティが予想どおりに機能していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
     <span data-ttu-id="f3e23-181">このセクションとこれまでのセクションでは、コンポーネントと Windows コントロールをコードと組み合わせてパッケージ化し、複合コントロールの形でカスタム機能を提供する方法を説明しました。</span><span class="sxs-lookup"><span data-stu-id="f3e23-181">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="f3e23-182">また、複合コントロールのプロパティを公開し、完了後にコントロールをテストする方法も説明しました。</span><span class="sxs-lookup"><span data-stu-id="f3e23-182">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="f3e23-183">次のセクションでは、`ctlClock` をベースとして使用して、継承された複合コントロールを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-183">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="f3e23-184">複合コントロールの継承</span><span class="sxs-lookup"><span data-stu-id="f3e23-184">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="f3e23-185">これまでのセクションでは、Windows コントロール、コンポーネント、コードを組み合わせて、再利用可能な複合コントロールを作成する方法を説明しました。</span><span class="sxs-lookup"><span data-stu-id="f3e23-185">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="f3e23-186">作成した複合コントロールをベースとして使用して、他のコントロールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-186">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="f3e23-187">基本クラスからクラスを派生するプロセスは "*継承*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-187">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="f3e23-188">このセクションでは、`ctlAlarmClock` という複合コントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-188">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="f3e23-189">このコントロールは、親コントロールである `ctlClock` から派生します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-189">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="f3e23-190">ここでは、親のメソッドをオーバーライドし、新しいメソッドとプロパティを追加して、`ctlClock` の機能を拡張する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-190">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="f3e23-191">継承されたコントロールを作成するには、まず、親から派生します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-191">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="f3e23-192">これにより、親コントロールのプロパティ、メソッド、グラフィカル特性をすべて備えた新しいコントロールが作成されます。このコントロールをベースとして使用して、新しい機能や変更された機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-192">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="f3e23-193">継承されたコントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="f3e23-193">To create the inherited control</span></span>  
  
1.  <span data-ttu-id="f3e23-194">ソリューション エクスプローラーで、**[ctlClockLib]** を右クリックし、**[追加]** をポイントして、**[ユーザー コントロール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-194">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="f3e23-195">**[新しい項目の追加]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-195">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="f3e23-196">**[継承されたユーザー コントロール]** テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-196">Select the **Inherited User Control** template.</span></span>  
  
3.  <span data-ttu-id="f3e23-197">**[名前]** ボックスに「`ctlAlarmClock.cs`」と入力し、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-197">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="f3e23-198">**[継承ピッカー]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-198">The **Inheritance Picker** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="f3e23-199">**[コンポーネント名]** の **[ctlClock]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-199">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5.  <span data-ttu-id="f3e23-200">ソリューション エクスプローラーで、現在のプロジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-200">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f3e23-201">現在のプロジェクトに、**ctlAlarmClock.cs** というファイルが追加されています。</span><span class="sxs-lookup"><span data-stu-id="f3e23-201">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="f3e23-202">アラームのプロパティの追加</span><span class="sxs-lookup"><span data-stu-id="f3e23-202">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="f3e23-203">複合コントロールにプロパティを追加する場合と同様に、継承されたコントロールにプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-203">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="f3e23-204">ここでは、プロパティ宣言の構文を使用して、コントロールに 2 つのプロパティを追加します。`AlarmTime` プロパティは、アラームを鳴らす日時の値を格納し、`AlarmSet` プロパティは、アラームが設定されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-204">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="f3e23-205">複合コントロールにプロパティを追加するには</span><span class="sxs-lookup"><span data-stu-id="f3e23-205">To add properties to your composite control</span></span>  
  
1.  <span data-ttu-id="f3e23-206">ソリューション エクスプローラーで、**[ctlAlarmClock]** を右クリックし、**[コードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-206">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="f3e23-207">`public class` ステートメントを探します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-207">Locate the `public class` statement.</span></span> <span data-ttu-id="f3e23-208">コントロールは `ctlClockLib.ctlClock` から継承されています。</span><span class="sxs-lookup"><span data-stu-id="f3e23-208">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="f3e23-209">左中かっこ (`{)` ステートメントの下に次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-209">Beneath the opening brace (`{)` statement, type the following code.</span></span>  
  
    ```csharp  
    private DateTime dteAlarmTime;  
    private bool blnAlarmSet;  
    // These properties will be declared as public to allow future   
    // developers to access them.  
    public DateTime AlarmTime  
    {  
        get  
        {  
            return dteAlarmTime;  
        }  
        set  
        {  
            dteAlarmTime = value;  
        }  
    }  
    public bool AlarmSet  
    {  
        get  
        {  
            return blnAlarmSet;  
        }  
        set  
        {  
            blnAlarmSet = value;  
        }  
    }  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="f3e23-210">コントロールのグラフィカル インターフェイスへの追加</span><span class="sxs-lookup"><span data-stu-id="f3e23-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="f3e23-211">継承されたコントロールには、継承元のコントロールと同じビジュアル インターフェイスがあります。</span><span class="sxs-lookup"><span data-stu-id="f3e23-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="f3e23-212">継承されたコントロールは親コントロールと同じ内在コントロールを持ちますが、内在コントロールのプロパティは、明確に公開されていない限り使用できません。</span><span class="sxs-lookup"><span data-stu-id="f3e23-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="f3e23-213">複合コントロールに追加する場合と同様に、継承された複合コントロールのグラフィカル インターフェイスに追加できます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="f3e23-214">引き続き、アラーム時計のビジュアル インターフェイスに、アラームが鳴っているときに点滅するラベル コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="f3e23-215">ラベル コントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="f3e23-215">To add the label control</span></span>  
  
1.  <span data-ttu-id="f3e23-216">ソリューション エクスプローラーで、**[ctlAlarmClock]** を右クリックし、**[デザイナーの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-216">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="f3e23-217">メイン ウィンドウに、`ctlAlarmClock` のデザイナーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2.  <span data-ttu-id="f3e23-218">コントロールの表示部分をクリックし、[プロパティ] ウィンドウを表示します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-218">Click the display portion of the control, and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f3e23-219">すべてのプロパティが表示されていますが、淡色表示になっています。</span><span class="sxs-lookup"><span data-stu-id="f3e23-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="f3e23-220">これは、これらのプロパティが `lblDisplay` に対してネイティブであり、[プロパティ] ウィンドウで変更したりアクセスしたりすることはできないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="f3e23-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="f3e23-221">既定では、複合コントロールに含まれているコントロールは `private` であり、どのような方法でもプロパティにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="f3e23-221">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f3e23-222">複合コントロールを今後使用するユーザーが、その内部のコントロールにアクセスできるようにする場合は、内部のコントロールを `public` または `protected` として宣言します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="f3e23-223">これにより、適切なコードを使用して、複合コントロールに含まれているコントロールのプロパティの設定や変更が可能になります。</span><span class="sxs-lookup"><span data-stu-id="f3e23-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3.  <span data-ttu-id="f3e23-224">追加、<xref:System.Windows.Forms.Label>複合コントロールを制御します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4.  <span data-ttu-id="f3e23-225">使用して、マウスをドラッグ、 <xref:System.Windows.Forms.Label> [表示] ボックスのすぐ下にあるコントロールです。</span><span class="sxs-lookup"><span data-stu-id="f3e23-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="f3e23-226">[プロパティ] ウィンドウで、次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="f3e23-227">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f3e23-227">Property</span></span>|<span data-ttu-id="f3e23-228">設定</span><span class="sxs-lookup"><span data-stu-id="f3e23-228">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="f3e23-229">**Name**</span><span class="sxs-lookup"><span data-stu-id="f3e23-229">**Name**</span></span>|`lblAlarm`|  
    |<span data-ttu-id="f3e23-230">**[テキスト]**</span><span class="sxs-lookup"><span data-stu-id="f3e23-230">**Text**</span></span>|<span data-ttu-id="f3e23-231">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="f3e23-231">**Alarm!**</span></span>|  
    |<span data-ttu-id="f3e23-232">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="f3e23-232">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="f3e23-233">**Visible**</span><span class="sxs-lookup"><span data-stu-id="f3e23-233">**Visible**</span></span>|`false`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="f3e23-234">アラーム機能の追加</span><span class="sxs-lookup"><span data-stu-id="f3e23-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="f3e23-235">前の手順では、複合コントロールでアラーム機能を有効にするためのプロパティとコントロールを追加しました。</span><span class="sxs-lookup"><span data-stu-id="f3e23-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="f3e23-236">この手順では、現在の時刻をアラームの時刻と比較して、2 つの時刻が同じである場合にアラームを点滅させるコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="f3e23-237">`ctlClock` の `timer1_Tick` メソッドをオーバーライドし、コードを追加することで、`ctlClock` の固有の機能をすべて保持しながら、`ctlAlarmClock` の機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-237">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="f3e23-238">ctlClock の timer1_Tick メソッドをオーバーライドするには</span><span class="sxs-lookup"><span data-stu-id="f3e23-238">To override the timer1_Tick method of ctlClock</span></span>  
  
1.  <span data-ttu-id="f3e23-239">**コード エディター**で、`private bool blnAlarmSet;` ステートメントを探します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-239">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="f3e23-240">このステートメントのすぐ下に、次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-240">Immediately beneath it, add the following statement.</span></span>  
  
    ```csharp  
    private bool blnColorTicker;  
    ```  
  
2.  <span data-ttu-id="f3e23-241">**コード エディター**で、クラスの末尾にある右中かっこ (`})` を探します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-241">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="f3e23-242">中かっこの直前に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-242">Just before the brace, add the following code.</span></span>  
  
    ```csharp  
    protected override void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Calls the Timer1_Tick method of ctlClock.  
        base.timer1_Tick(sender, e);  
        // Checks to see if the alarm is set.  
        if (AlarmSet == false)  
            return;  
        else  
            // If the date, hour, and minute of the alarm time are the same as  
            // the current time, flash an alarm.   
        {  
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==   
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)  
            {  
                // Sets lblAlarmVisible to true, and changes the background color based on  
                // the value of blnColorTicker. The background color of the label   
                // will flash once per tick of the clock.  
                lblAlarm.Visible = true;  
                if (blnColorTicker == false)   
                {  
                    lblAlarm.BackColor = Color.Red;  
                    blnColorTicker = true;  
                }  
                else  
                {  
                    lblAlarm.BackColor = Color.Blue;  
                    blnColorTicker = false;  
                }  
            }  
            else  
            {  
                // Once the alarm has sounded for a minute, the label is made   
                // invisible again.  
                lblAlarm.Visible = false;  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="f3e23-243">このコードを追加すると、いくつかのタスクが実行されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-243">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="f3e23-244">`override` ステートメントは、基本コントロールから継承されたメソッドの代わりに、このメソッドを使用するようコントロールに指示します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-244">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="f3e23-245">このメソッドが呼び出されると、メソッドは `base.timer1_Tick` ステートメントを呼び出して、オーバーライドしたメソッドを呼び出します。これにより、元のコントロールに組み込まれたすべての機能がこのコントロールに継承されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-245">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="f3e23-246">その後、メソッドは追加のコードを実行してアラーム機能を組み込みます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-246">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="f3e23-247">アラームが発生すると、点滅するラベル コントロールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-247">A flashing label control will appear when the alarm occurs.</span></span>  
  
     <span data-ttu-id="f3e23-248">これで、アラーム時計コントロールはほぼ完成です。</span><span class="sxs-lookup"><span data-stu-id="f3e23-248">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="f3e23-249">あとはアラームを止める方法を実装するだけです。</span><span class="sxs-lookup"><span data-stu-id="f3e23-249">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="f3e23-250">これを行うには、`lblAlarm_Click` メソッドにコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-250">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="f3e23-251">停止メソッドを実装するには</span><span class="sxs-lookup"><span data-stu-id="f3e23-251">To implement the shutoff method</span></span>  
  
1.  <span data-ttu-id="f3e23-252">ソリューション エクスプローラーで、**[ctlAlarmClock.cs]** を右クリックし、**[デザイナーの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-252">In Solution Explorer, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="f3e23-253">デザイナーが開きます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-253">The designer opens.</span></span>  
  
2.  <span data-ttu-id="f3e23-254">コントロールにボタンを追加します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-254">Add a button to the control.</span></span> <span data-ttu-id="f3e23-255">ボタンのプロパティを次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-255">Set the properties of the button as follows.</span></span>  
  
    |<span data-ttu-id="f3e23-256">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f3e23-256">Property</span></span>|<span data-ttu-id="f3e23-257">[値]</span><span class="sxs-lookup"><span data-stu-id="f3e23-257">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="f3e23-258">**Name**</span><span class="sxs-lookup"><span data-stu-id="f3e23-258">**Name**</span></span>|`btnAlarmOff`|  
    |<span data-ttu-id="f3e23-259">**[テキスト]**</span><span class="sxs-lookup"><span data-stu-id="f3e23-259">**Text**</span></span>|<span data-ttu-id="f3e23-260">**Disable Alarm**</span><span class="sxs-lookup"><span data-stu-id="f3e23-260">**Disable Alarm**</span></span>|  
  
3.  <span data-ttu-id="f3e23-261">デザイナーで **[btnAlarmOff]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-261">In the designer, double-click **btnAlarmOff**.</span></span>  
  
     <span data-ttu-id="f3e23-262">**コード エディター**が開き、`private void btnAlarmOff_Click` 行が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-262">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>  
  
4.  <span data-ttu-id="f3e23-263">このメソッドを次のコードのように変更します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-263">Modify this method so that it resembles the following code.</span></span>  
  
    ```csharp  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5.  <span data-ttu-id="f3e23-264">**[ファイル]** メニューの **[すべて保存]** をクリックして、プロジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-264">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="f3e23-265">フォームでの継承されたコントロールの使用</span><span class="sxs-lookup"><span data-stu-id="f3e23-265">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="f3e23-266">継承されたコントロールは、基本クラスのコントロールである `ctlClock` をテストしたときと同様にテストできます。F5 キーを押してプロジェクトをビルドし、**UserControl Test Container** でコントロールを実行します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-266">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="f3e23-267">詳細については、「[方法: UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3e23-267">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="f3e23-268">コントロールを使用するには、フォーム上でコントロールをホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3e23-268">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="f3e23-269">標準の複合コントロールと同様に、継承された複合コントロールをスタンドアロンにすることはできないので、フォームまたは他のコンテナー内でホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3e23-269">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="f3e23-270">`ctlAlarmClock` は機能が拡張されているため、テストするには追加のコードが必要となります。</span><span class="sxs-lookup"><span data-stu-id="f3e23-270">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="f3e23-271">次の手順では、`ctlAlarmClock` の機能をテストするための簡単なプログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-271">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="f3e23-272">`ctlAlarmClock` の `AlarmTime` プロパティを設定して表示するコードを記述し、固有の機能をテストします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-272">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="f3e23-273">コントロールをビルドしてテスト フォームに追加するには</span><span class="sxs-lookup"><span data-stu-id="f3e23-273">To build and add your control to a test form</span></span>  
  
1.  <span data-ttu-id="f3e23-274">ソリューション エクスプローラーで、**[ctlClockLib]** を右クリックし、**[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-274">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="f3e23-275">新しい **Windows アプリケーション** プロジェクトをソリューションに追加し、`Test` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-275">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
3.  <span data-ttu-id="f3e23-276">ソリューション エクスプローラーで、テスト プロジェクトの **[参照設定]** ノードを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-276">In Solution Explorer, right-click the **References** node for your test project.</span></span> <span data-ttu-id="f3e23-277">**[参照の追加]** をクリックして、**[参照の追加]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-277">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="f3e23-278">**[プロジェクト]** というラベルのタブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-278">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="f3e23-279">**[プロジェクト名]** に `ctlClockLib` プロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-279">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="f3e23-280">プロジェクトをダブルクリックして、テスト プロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-280">Double-click the project to add the reference to the test project.</span></span>  
  
4.  <span data-ttu-id="f3e23-281">ソリューション エクスプローラーで、**[Test]** を右クリックし、**[ビルド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-281">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="f3e23-282">**ツールボックス**で、**[ctlClockLib コンポーネント]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-282">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
6.  <span data-ttu-id="f3e23-283">**[ctlAlarmClock]** をダブルクリックして、`ctlAlarmClock` のコピーをフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-283">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>  
  
7.  <span data-ttu-id="f3e23-284">**ツールボックス**を特定し、ダブルクリック、 **DateTimePicker**を追加する、<xref:System.Windows.Forms.DateTimePicker>をフォームに制御し、追加、<xref:System.Windows.Forms.Label>コントロールをダブルクリックして**ラベル**.</span><span class="sxs-lookup"><span data-stu-id="f3e23-284">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
8.  <span data-ttu-id="f3e23-285">マウスを使用して、各コントロールをフォーム上の使いやすい場所に配置します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-285">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
9. <span data-ttu-id="f3e23-286">これらのコントロールのプロパティを次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-286">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="f3e23-287">コントロール</span><span class="sxs-lookup"><span data-stu-id="f3e23-287">Control</span></span>|<span data-ttu-id="f3e23-288">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f3e23-288">Property</span></span>|<span data-ttu-id="f3e23-289">[値]</span><span class="sxs-lookup"><span data-stu-id="f3e23-289">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|<span data-ttu-id="f3e23-290">**[テキスト]**</span><span class="sxs-lookup"><span data-stu-id="f3e23-290">**Text**</span></span>|`(blank space)`|  
    ||<span data-ttu-id="f3e23-291">**Name**</span><span class="sxs-lookup"><span data-stu-id="f3e23-291">**Name**</span></span>|`lblTest`|  
    |`dateTimePicker1`|<span data-ttu-id="f3e23-292">**Name**</span><span class="sxs-lookup"><span data-stu-id="f3e23-292">**Name**</span></span>|`dtpTest`|  
    ||<span data-ttu-id="f3e23-293">**Format**</span><span class="sxs-lookup"><span data-stu-id="f3e23-293">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
10. <span data-ttu-id="f3e23-294">デザイナーで **[dtpTest]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-294">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="f3e23-295">**コード エディター**が開き、`private void dtpTest_ValueChanged` が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-295">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>  
  
11. <span data-ttu-id="f3e23-296">コードを次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-296">Modify the code so that it resembles the following.</span></span>  
  
    ```csharp  
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)  
    {  
        ctlAlarmClock1.AlarmTime = dtpTest.Value;  
        ctlAlarmClock1.AlarmSet = true;  
        lblTest.Text = "Alarm Time is " +  
            ctlAlarmClock1.AlarmTime.ToShortTimeString();  
    }  
    ```  
  
12. <span data-ttu-id="f3e23-297">ソリューション エクスプローラーで、**[Test]** を右クリックし、**[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-297">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
13. <span data-ttu-id="f3e23-298">**[デバッグ]** メニューの **[デバッグの開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3e23-298">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="f3e23-299">テスト プログラムが起動します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-299">The test program starts.</span></span> <span data-ttu-id="f3e23-300">現在の時刻が更新されるに注意してください、`ctlAlarmClock`制御、およびに開始時刻が表示されている、<xref:System.Windows.Forms.DateTimePicker>コントロール。</span><span class="sxs-lookup"><span data-stu-id="f3e23-300">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
14. <span data-ttu-id="f3e23-301">クリックして、<xref:System.Windows.Forms.DateTimePicker>時間 (分) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-301">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
15. <span data-ttu-id="f3e23-302">キーボードを使用して、`ctlAlarmClock` に表示されている現在の時刻の 1 分後の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-302">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="f3e23-303">アラーム設定の時刻が `lblTest` に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-303">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="f3e23-304">表示時刻がアラーム設定時刻になるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-304">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="f3e23-305">表示時刻がアラーム設定時刻になると、`lblAlarm` が点滅します。</span><span class="sxs-lookup"><span data-stu-id="f3e23-305">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>  
  
16. <span data-ttu-id="f3e23-306">`btnAlarmOff` をクリックしてアラームを止めます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-306">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="f3e23-307">これでアラームをリセットできます。</span><span class="sxs-lookup"><span data-stu-id="f3e23-307">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="f3e23-308">このチュートリアルでは、多数の重要な概念を取り上げました。</span><span class="sxs-lookup"><span data-stu-id="f3e23-308">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="f3e23-309">コントロールとコンポーネントを複合コントロール コンテナーに組み込んで複合コントロールを作成する方法を説明しました。</span><span class="sxs-lookup"><span data-stu-id="f3e23-309">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="f3e23-310">また、コントロールにプロパティを追加する方法と、カスタム機能を実装するコードを記述する方法も説明しました。</span><span class="sxs-lookup"><span data-stu-id="f3e23-310">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="f3e23-311">最後のセクションでは、継承によって特定の複合コントロールの機能を拡張する方法と、ホスト メソッドをオーバーライドすることでメソッドの機能を変更する方法を説明しました。</span><span class="sxs-lookup"><span data-stu-id="f3e23-311">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e23-312">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3e23-312">See Also</span></span>  
 [<span data-ttu-id="f3e23-313">さまざまなカスタム コントロール</span><span class="sxs-lookup"><span data-stu-id="f3e23-313">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="f3e23-314">コンポーネントによるプログラミング</span><span class="sxs-lookup"><span data-stu-id="f3e23-314">Programming with Components</span></span>](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [<span data-ttu-id="f3e23-315">コンポーネント作成のチュートリアル</span><span class="sxs-lookup"><span data-stu-id="f3e23-315">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 <span data-ttu-id="f3e23-316">[方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="f3e23-316">[How to: Display a Control in the Choose Toolbox Items Dialog Box](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span></span>  
 [<span data-ttu-id="f3e23-317">チュートリアル: Visual C# による Windows フォーム コントロールからの継承</span><span class="sxs-lookup"><span data-stu-id="f3e23-317">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
