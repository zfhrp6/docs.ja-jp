---
title: 'チュートリアル : Visual Basic での COM オブジェクトの作成'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: caf0a071d65746f1027052e648ade538d62dc4bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="61353-102">チュートリアル : Visual Basic での COM オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="61353-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="61353-103">新しいアプリケーションまたはコンポーネントを作成する場合は、.NET Framework アセンブリを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="61353-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="61353-104">ただし、Visual Basic も簡単に COM に .NET Framework コンポーネントを公開するには</span><span class="sxs-lookup"><span data-stu-id="61353-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="61353-105">これにより、COM コンポーネントを必要とする以前のアプリケーション スイートの新しいコンポーネントを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="61353-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="61353-106">このチュートリアルは、Visual Basic を使用して公開する方法を示します[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]オブジェクトと COM クラス テンプレートを使用せず、COM オブジェクトとして。</span><span class="sxs-lookup"><span data-stu-id="61353-106">This walkthrough demonstrates how to use Visual Basic to expose [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="61353-107">COM オブジェクトを公開する最も簡単な方法は、COM クラス テンプレートを使用してです。</span><span class="sxs-lookup"><span data-stu-id="61353-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="61353-108">COM クラス テンプレートは、新しいクラスを作成し、構成、プロジェクトの COM オブジェクトとしてのクラスと相互運用性レイヤーを生成し、オペレーティング システムに登録します。</span><span class="sxs-lookup"><span data-stu-id="61353-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61353-109">Visual Basic で使用するアンマネージ コードの COM オブジェクトとして作成したクラスを公開することが true COM オブジェクトではないと、Visual Basic では使用できません。</span><span class="sxs-lookup"><span data-stu-id="61353-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="61353-110">詳細については、次を参照してください。 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)です。</span><span class="sxs-lookup"><span data-stu-id="61353-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="61353-111">COM クラス テンプレートを使用して COM オブジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="61353-111">To create a COM object by using the COM class template</span></span>  
  
1.  <span data-ttu-id="61353-112">新しい Windows アプリケーション プロジェクトを開き、**ファイル** をクリックしてメニュー**新しいプロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="61353-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2.  <span data-ttu-id="61353-113">**新しいプロジェクト**ダイアログ ボックスの 、**プロジェクトの種類**フィールドに、Windows が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="61353-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="61353-114">選択**クラス ライブラリ**から、**テンプレート**一覧をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="61353-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="61353-115">新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="61353-115">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="61353-116">選択**新しい項目の追加**から、**プロジェクト**メニュー。</span><span class="sxs-lookup"><span data-stu-id="61353-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="61353-117">**[新しい項目の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="61353-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="61353-118">選択**COM クラス**から、**テンプレート**一覧をクリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="61353-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="61353-119">Visual Basic では、新しいクラスを追加し、COM 相互運用機能の新しいプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="61353-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5.  <span data-ttu-id="61353-120">COM クラスには、プロパティ、メソッド、およびイベントのようなコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="61353-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6.  <span data-ttu-id="61353-121">選択**ビルド ClassLibrary1**から、**ビルド**メニュー。</span><span class="sxs-lookup"><span data-stu-id="61353-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="61353-122">Visual Basic では、アセンブリがビルドされ、オペレーティング システムと COM オブジェクトを登録します。</span><span class="sxs-lookup"><span data-stu-id="61353-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="61353-123">COM クラス テンプレートを使用せず、COM オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="61353-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="61353-124">COM クラス テンプレートを使用する代わりに、手動での COM クラスを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="61353-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="61353-125">コマンドラインから作業している場合、または COM オブジェクトの定義方法を制御する場合は、この手順をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="61353-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="61353-126">COM オブジェクトを生成するプロジェクトを設定するには</span><span class="sxs-lookup"><span data-stu-id="61353-126">To set up your project to generate a COM object</span></span>  
  
1.  <span data-ttu-id="61353-127">新しい Windows アプリケーション プロジェクトを開き、**ファイル** をクリックしてメニュー**プロジェクトに新しい**です。</span><span class="sxs-lookup"><span data-stu-id="61353-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2.  <span data-ttu-id="61353-128">**新しいプロジェクト**ダイアログ ボックスの 、**プロジェクトの種類**フィールドに、Windows が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="61353-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="61353-129">選択**クラス ライブラリ**から、**テンプレート**一覧をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="61353-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="61353-130">新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="61353-130">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="61353-131">**ソリューション エクスプ ローラー**、プロジェクトを右クリックし、クリックして**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="61353-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="61353-132">**プロジェクト デザイナー**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="61353-132">The **Project Designer** is displayed.</span></span>  
  
4.  <span data-ttu-id="61353-133">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="61353-133">Click the **Compile** tab.</span></span>  
  
5.  <span data-ttu-id="61353-134">選択、 **COM 相互運用機能の登録**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="61353-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="61353-135">COM オブジェクトを作成する、クラスのコードを設定するには</span><span class="sxs-lookup"><span data-stu-id="61353-135">To set up the code in your class to create a COM object</span></span>  
  
1.  <span data-ttu-id="61353-136">**ソリューション エクスプ ローラー**をダブルクリックして**Class1.vb**そのコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="61353-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2.  <span data-ttu-id="61353-137">クラスの名前を `ComClass1` に変更します。</span><span class="sxs-lookup"><span data-stu-id="61353-137">Rename the class to `ComClass1`.</span></span>  
  
3.  <span data-ttu-id="61353-138">次の定数を追加`ComClass1`です。</span><span class="sxs-lookup"><span data-stu-id="61353-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="61353-139">COM オブジェクトを必要とされる定数をグローバル一意識別子 (GUID) が格納されます。</span><span class="sxs-lookup"><span data-stu-id="61353-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  <span data-ttu-id="61353-140">**[ツール]** メニューの **[GUID の作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61353-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="61353-141">**[GUID の作成]** ダイアログ ボックスで、**[レジストリ形式]** をクリックし、**[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61353-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="61353-142">**[終了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61353-142">Click **Exit**.</span></span>  
  
5.  <span data-ttu-id="61353-143">空の文字列を置き換える、 `ClassId` GUID を持つ削除、先頭と末尾の右中かっこです。</span><span class="sxs-lookup"><span data-stu-id="61353-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="61353-144">たとえば、GUID が Guidgen によって提供される場合は`"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"`コードは次のように表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61353-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  <span data-ttu-id="61353-145">前の手順を繰り返します、`InterfaceId`と`EventsId`定数は、次の例のようにします。</span><span class="sxs-lookup"><span data-stu-id="61353-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="61353-146">Guid は、新規および一意であることを確認してください。それ以外の場合、COM コンポーネントは、他の COM コンポーネントと競合する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="61353-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7.  <span data-ttu-id="61353-147">追加、`ComClass`属性を`ComClass1`、次の例のように、クラス ID、インターフェイス ID、およびイベント ID の Guid を指定します。</span><span class="sxs-lookup"><span data-stu-id="61353-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  <span data-ttu-id="61353-148">COM クラスは、パラメーターなしである必要があります`Public Sub New()`コンス トラクター、またはクラスが正しく登録できません。</span><span class="sxs-lookup"><span data-stu-id="61353-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="61353-149">クラスには、パラメーターなしのコンス トラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="61353-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. <span data-ttu-id="61353-150">終了して、クラスのプロパティ、メソッド、およびイベントに追加、`End Class`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="61353-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="61353-151">選択**ソリューションのビルド**から、**ビルド**メニュー。</span><span class="sxs-lookup"><span data-stu-id="61353-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="61353-152">Visual Basic では、アセンブリがビルドされ、オペレーティング システムと COM オブジェクトを登録します。</span><span class="sxs-lookup"><span data-stu-id="61353-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="61353-153">Visual basic を生成する COM オブジェクトは、true の COM オブジェクトではないために、他の Visual Basic アプリケーションで使用できません。</span><span class="sxs-lookup"><span data-stu-id="61353-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="61353-154">このような COM オブジェクトへの参照を追加する操作には、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="61353-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="61353-155">詳細については、「 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)です。</span><span class="sxs-lookup"><span data-stu-id="61353-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61353-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="61353-156">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ComClassAttribute>  
 [<span data-ttu-id="61353-157">COM 相互運用</span><span class="sxs-lookup"><span data-stu-id="61353-157">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="61353-158">チュートリアル : COM オブジェクトによる継承の実装</span><span class="sxs-lookup"><span data-stu-id="61353-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [<span data-ttu-id="61353-159">#Region ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="61353-159">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)  
 [<span data-ttu-id="61353-160">.NET Framework アプリケーションにおける COM 相互運用性</span><span class="sxs-lookup"><span data-stu-id="61353-160">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [<span data-ttu-id="61353-161">相互運用性のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="61353-161">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
