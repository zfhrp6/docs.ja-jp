---
title: '方法 : シンプルな Windows フォーム コントロールを開発する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 04cedc0df60ef95acb79b651ddcbcbb34ae5e920
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a><span data-ttu-id="533e1-102">方法 : シンプルな Windows フォーム コントロールを開発する</span><span class="sxs-lookup"><span data-stu-id="533e1-102">How to: Develop a Simple Windows Forms Control</span></span>
<span data-ttu-id="533e1-103">ここでは、カスタム Windows フォーム コントロールの主な作成手順を紹介します。</span><span class="sxs-lookup"><span data-stu-id="533e1-103">This section walks you through the key steps for authoring a custom Windows Forms control.</span></span> <span data-ttu-id="533e1-104">このチュートリアルで開発された単純なコントロールでの配置は、その<xref:System.Windows.Forms.Control.Text%2A>プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="533e1-104">The simple control developed in this walkthrough allows the alignment of its <xref:System.Windows.Forms.Control.Text%2A> property to be changed.</span></span> <span data-ttu-id="533e1-105">イベントを発生させたり処理したりすることはありません。</span><span class="sxs-lookup"><span data-stu-id="533e1-105">It does not raise or handle events.</span></span>  
  
### <a name="to-create-a-simple-custom-control"></a><span data-ttu-id="533e1-106">シンプルなカスタム コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="533e1-106">To create a simple custom control</span></span>  
  
1.  <span data-ttu-id="533e1-107"><xref:System.Windows.Forms.Control?displayProperty=nameWithType> から派生するクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="533e1-107">Define a class that derives from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control{}  
    ```  
  
2.  <span data-ttu-id="533e1-108">プロパティを定義します </span><span class="sxs-lookup"><span data-stu-id="533e1-108">Define properties.</span></span> <span data-ttu-id="533e1-109">(コントロールから多くのプロパティを継承しているために、プロパティを定義する必要はありません、<xref:System.Windows.Forms.Control>追加のプロパティを定義して、通常、クラスが、ほとんどのカスタム コントロールです)。次のコード フラグメントは、という名前のプロパティを定義`TextAlignment`を`FirstControl`の表示形式を使用して、<xref:System.Windows.Forms.Control.Text%2A>プロパティから継承<xref:System.Windows.Forms.Control>です。</span><span class="sxs-lookup"><span data-stu-id="533e1-109">(You are not required to define properties, because a control inherits many properties from the <xref:System.Windows.Forms.Control> class, but most custom controls generally do define additional properties.) The following code fragment defines a property named `TextAlignment` that `FirstControl` uses to format the display of the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="533e1-110">プロパティの定義の詳細については、「[プロパティの概要](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="533e1-110">For more information about defining properties, see [Properties Overview](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     <span data-ttu-id="533e1-111">コントロールのビジュアル表示を変更するプロパティを設定するときに呼び出す必要があります、<xref:System.Windows.Forms.Control.Invalidate%2A>コントロールを再描画するためです。</span><span class="sxs-lookup"><span data-stu-id="533e1-111">When you set a property that changes the visual display of the control, you must invoke the <xref:System.Windows.Forms.Control.Invalidate%2A> method to redraw the control.</span></span> <span data-ttu-id="533e1-112"><xref:System.Windows.Forms.Control.Invalidate%2A> 基本クラスで定義された<xref:System.Windows.Forms.Control>です。</span><span class="sxs-lookup"><span data-stu-id="533e1-112"><xref:System.Windows.Forms.Control.Invalidate%2A> is defined in the base class <xref:System.Windows.Forms.Control>.</span></span>  
  
3.  <span data-ttu-id="533e1-113">保護されたオーバーライド<xref:System.Windows.Forms.Control.OnPaint%2A>から継承されたメソッド<xref:System.Windows.Forms.Control>をコントロールにレンダリング ロジックを提供します。</span><span class="sxs-lookup"><span data-stu-id="533e1-113">Override the protected <xref:System.Windows.Forms.Control.OnPaint%2A> method inherited from <xref:System.Windows.Forms.Control> to provide rendering logic to your control.</span></span> <span data-ttu-id="533e1-114">オーバーライドしていない場合<xref:System.Windows.Forms.Control.OnPaint%2A>コントロールでは、自身で描画できません。</span><span class="sxs-lookup"><span data-stu-id="533e1-114">If you do not override <xref:System.Windows.Forms.Control.OnPaint%2A>, your control will not be able to draw itself.</span></span> <span data-ttu-id="533e1-115">次のコード フラグメントで、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドが表示されます、<xref:System.Windows.Forms.Control.Text%2A>プロパティから継承<xref:System.Windows.Forms.Control>で指定された配置された、`alignmentValue`フィールドです。</span><span class="sxs-lookup"><span data-stu-id="533e1-115">In the following code fragment, the <xref:System.Windows.Forms.Control.OnPaint%2A> method displays the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control> with the alignment specified by the `alignmentValue` field.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  <span data-ttu-id="533e1-116">コントロールの属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="533e1-116">Provide attributes for your control.</span></span> <span data-ttu-id="533e1-117">ビジュアル デザイナーでは、デザイン時に属性を使用することで、コントロール、コントロールのプロパティ、およびイベントを適切に表示します。</span><span class="sxs-lookup"><span data-stu-id="533e1-117">Attributes enable a visual designer to display your control and its properties and events appropriately at design time.</span></span> <span data-ttu-id="533e1-118">次のコード フラグメントでは、属性が `TextAlignment` プロパティに適用されます。</span><span class="sxs-lookup"><span data-stu-id="533e1-118">The following code fragment applies attributes to the `TextAlignment` property.</span></span> <span data-ttu-id="533e1-119">Visual Studio などのデザイナーで、<xref:System.ComponentModel.CategoryAttribute.Category%2A>属性 (のコード フラグメントに示す) が論理カテゴリの下に表示するプロパティをによりします。</span><span class="sxs-lookup"><span data-stu-id="533e1-119">In a designer such as Visual Studio, the <xref:System.ComponentModel.CategoryAttribute.Category%2A> attribute (shown in the code fragment) causes the property to be displayed under a logical category.</span></span> <span data-ttu-id="533e1-120"><xref:System.ComponentModel.DescriptionAttribute.Description%2A>属性によりの下部に表示される説明の文字列、**プロパティ**ウィンドウと、`TextAlignment`プロパティが選択されています。</span><span class="sxs-lookup"><span data-stu-id="533e1-120">The <xref:System.ComponentModel.DescriptionAttribute.Description%2A> attribute causes a descriptive string to be displayed at the bottom of the **Properties** window when the `TextAlignment` property is selected.</span></span> <span data-ttu-id="533e1-121">属性の詳細については、「[コンポーネントのデザイン時属性](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="533e1-121">For more information about attributes, see [Design-Time Attributes for Components](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  <span data-ttu-id="533e1-122">(省略可能) コントロールに対してリソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="533e1-122">(optional) Provide resources for your control.</span></span> <span data-ttu-id="533e1-123">コントロールに対してビットマップなどのリソースを指定するには、コンパイラ オプション (C# の場合は `/res`) を使用して、リソースをコントロールと共にパッケージ化します。</span><span class="sxs-lookup"><span data-stu-id="533e1-123">You can provide a resource, such as a bitmap, for your control by using a compiler option (`/res` for C#) to package resources with your control.</span></span> <span data-ttu-id="533e1-124">実行時に、リソースを取得できるのメソッドを使用して、<xref:System.Resources.ResourceManager>クラスです。</span><span class="sxs-lookup"><span data-stu-id="533e1-124">At run time, the resource can be retrieved using the methods of the <xref:System.Resources.ResourceManager> class.</span></span> <span data-ttu-id="533e1-125">リソースの作成と使用の詳細については、「[デスクトップ アプリケーションのリソース](../../../../docs/framework/resources/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="533e1-125">For more information about creating and using resources, see the [Resources in Desktop Apps](../../../../docs/framework/resources/index.md).</span></span>  
  
6.  <span data-ttu-id="533e1-126">コンパイルしてコントロールを配置します。</span><span class="sxs-lookup"><span data-stu-id="533e1-126">Compile and deploy your control.</span></span> <span data-ttu-id="533e1-127">`FirstControl,` をコンパイルして配置するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="533e1-127">To compile and deploy `FirstControl,` execute the following steps:</span></span>  
  
    1.  <span data-ttu-id="533e1-128">次のサンプル コードをソース ファイル (FirstControl.cs、FirstControl.vb など) に保存します。</span><span class="sxs-lookup"><span data-stu-id="533e1-128">Save the code in the following sample to a source file (such as FirstControl.cs or FirstControl.vb).</span></span>  
  
    2.  <span data-ttu-id="533e1-129">ソース コードをコンパイルして、アセンブリを生成し、アプリケーションのディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="533e1-129">Compile the source code into an assembly and save it in your application's directory.</span></span> <span data-ttu-id="533e1-130">それには、ソース ファイルが格納されているディレクトリで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="533e1-130">To accomplish this, execute the following command from the directory that contains the source file.</span></span>  
  
        ```console  
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```console 
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs  
        ```  
  
         <span data-ttu-id="533e1-131">`/t:library` コンパイラ オプションは、作成しているアセンブリが (実行可能ファイルではなく) ライブラリであることをコンパイラに伝えます。</span><span class="sxs-lookup"><span data-stu-id="533e1-131">The `/t:library` compiler option tells the compiler that the assembly you are creating is a library (and not an executable).</span></span> <span data-ttu-id="533e1-132">`/out` オプションでは、アセンブリの名前とパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="533e1-132">The `/out` option specifies the path and name of the assembly.</span></span> <span data-ttu-id="533e1-133">`/r` オプションでは、コードが参照するアセンブリの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="533e1-133">The`/r` option provides the name of the assemblies that are referenced by your code.</span></span> <span data-ttu-id="533e1-134">この例では、ご自身のアプリケーションのみが使用できるプライベート アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="533e1-134">In this example, you create a private assembly that only your applications can use.</span></span> <span data-ttu-id="533e1-135">このため、アセンブリはご自身のアプリケーションのディレクトリに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="533e1-135">Hence, you have to save it in your application's directory.</span></span> <span data-ttu-id="533e1-136">配布用コントロールのパッケージ化と配置の詳細については、[配置](../../../../docs/framework/deployment/index.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="533e1-136">For more information about packaging and deploying a control for distribution, see [Deployment](../../../../docs/framework/deployment/index.md).</span></span>  
  
 <span data-ttu-id="533e1-137">次のサンプルは、`FirstControl` のコードを示しています。</span><span class="sxs-lookup"><span data-stu-id="533e1-137">The following sample shows the code for `FirstControl`.</span></span> <span data-ttu-id="533e1-138">このコントロールは、`CustomWinControls` 名前空間に囲まれています。</span><span class="sxs-lookup"><span data-stu-id="533e1-138">The control is enclosed in the namespace `CustomWinControls`.</span></span> <span data-ttu-id="533e1-139">名前空間では、関連する型を論理的にグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="533e1-139">A namespace provides a logical grouping of related types.</span></span> <span data-ttu-id="533e1-140">コントロールは、新しい名前空間または既存の名前空間に作成できます。</span><span class="sxs-lookup"><span data-stu-id="533e1-140">You can create your control in a new or existing namespace.</span></span> <span data-ttu-id="533e1-141">C# では、`using` 宣言 (Visual Basic の場合は `Imports`) を使用すると、名前空間から型へアクセスするときに、型の完全修飾名を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="533e1-141">In C#, the `using` declaration (in Visual Basic, `Imports`) allows types to be accessed from a namespace without using the fully qualified name of the type.</span></span> <span data-ttu-id="533e1-142">次の例で、`using`宣言により、クラスにアクセスするためのコード<xref:System.Windows.Forms.Control>から<xref:System.Windows.Forms?displayProperty=nameWithType>単に<xref:System.Windows.Forms.Control>を完全修飾名を使用することではなく<xref:System.Windows.Forms.Control?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="533e1-142">In the following example, the `using` declaration allows code to access the class <xref:System.Windows.Forms.Control> from <xref:System.Windows.Forms?displayProperty=nameWithType> as simply <xref:System.Windows.Forms.Control> instead of having to use the fully qualified name <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a><span data-ttu-id="533e1-143">フォームでのカスタム コントロールの使用</span><span class="sxs-lookup"><span data-stu-id="533e1-143">Using the Custom Control on a Form</span></span>  
 <span data-ttu-id="533e1-144">`FirstControl` を使用するシンプルなフォームの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="533e1-144">The following example shows a simple form that uses `FirstControl`.</span></span> <span data-ttu-id="533e1-145">この例では、`FirstControl` のインスタンスを 3 つ作成します。それぞれのインスタンスで、`TextAlignment` プロパティに異なる値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="533e1-145">It creates three instances of `FirstControl`, each with a different value for the `TextAlignment` property.</span></span>  
  
#### <a name="to-compile-and-run-this-sample"></a><span data-ttu-id="533e1-146">このサンプルをコンパイルして実行するには</span><span class="sxs-lookup"><span data-stu-id="533e1-146">To compile and run this sample</span></span>  
  
1.  <span data-ttu-id="533e1-147">このサンプルをコンパイルして実行するには、次に示すサンプルのコードをソース ファイル (SimpleForm.cs または SimpleForms.vb) に保存します。</span><span class="sxs-lookup"><span data-stu-id="533e1-147">Save the code in the following example to a source file (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
2.  <span data-ttu-id="533e1-148">ソース ファイルが格納されているディレクトリから次のコマンドを実行して、ソース コードを実行可能アセンブリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="533e1-148">Compile the source code into an executable assembly by executing the following command from the directory that contains the source file.</span></span>  
  
    ```console  
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```console 
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     <span data-ttu-id="533e1-149">CustomWinControls.dll は、クラスを含むアセンブリ`FirstControl`です。</span><span class="sxs-lookup"><span data-stu-id="533e1-149">CustomWinControls.dll is the assembly that contains the class `FirstControl`.</span></span> <span data-ttu-id="533e1-150">フォームがアセンブリにアクセスできるように、そのアセンブリはソース ファイル (SimpleForm.cs または SimpleForms.vb) と同じディレクトリに格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="533e1-150">This assembly must be in the same directory as the source file for the form that accesses it (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
3.  <span data-ttu-id="533e1-151">次のコマンドで SimpleForm.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="533e1-151">Execute SimpleForm.exe using the following command.</span></span>  
  
    ```console
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="533e1-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="533e1-152">See Also</span></span>  
 [<span data-ttu-id="533e1-153">Windows フォーム コントロールのプロパティ</span><span class="sxs-lookup"><span data-stu-id="533e1-153">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="533e1-154">Windows フォーム コントロールのイベント</span><span class="sxs-lookup"><span data-stu-id="533e1-154">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
