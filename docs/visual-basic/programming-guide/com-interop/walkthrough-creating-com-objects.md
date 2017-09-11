---
title: "チュートリアル: Visual Basic での COM オブジェクトの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- COM interop, creating COM objects
- COM objects, creating
- COM interop, walkthroughs
- object creation, COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 859a8fc7440eecc0cadbfa8ea236dad7cae99247
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="a4b79-102">チュートリアル : Visual Basic での COM オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="a4b79-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="a4b79-103">新しいアプリケーションまたはコンポーネントを作成する場合は、.NET Framework アセンブリを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a4b79-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="a4b79-104">ただし、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]も容易に COM に .NET Framework コンポーネントを公開するには</span><span class="sxs-lookup"><span data-stu-id="a4b79-104">However, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="a4b79-105">これにより、COM コンポーネントを必要とする以前のアプリケーション スイートに新しいコンポーネントを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="a4b79-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="a4b79-106">このチュートリアルを使用する方法について説明[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を公開する[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]COM オブジェクト、COM クラス テンプレートの有無にかかわらず、としてオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="a4b79-106">This walkthrough demonstrates how to use [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to expose [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="a4b79-107">COM オブジェクトを公開する最も簡単な方法は、COM クラス テンプレートを使用してです。</span><span class="sxs-lookup"><span data-stu-id="a4b79-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="a4b79-108">COM クラス テンプレートは、新しいクラスを作成し、COM オブジェクトとしてのクラスと相互運用性レイヤーを生成し、オペレーティング システムに登録するようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4b79-109">作成されたクラスを公開することもできます。 ただし[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を使用するアンマネージ コードの COM オブジェクトとして true COM オブジェクトではない、では使用できません[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-109">Although you can also expose a class created in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="a4b79-110">詳細については、次を参照してください。 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="a4b79-111">COM クラス テンプレートを使用して COM オブジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="a4b79-111">To create a COM object by using the COM class template</span></span>  
  
1.  <span data-ttu-id="a4b79-112">新しい Windows アプリケーション プロジェクトを開き、**ファイル**をクリックしてメニュー**新しいプロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2.  <span data-ttu-id="a4b79-113">**新しいプロジェクト**ダイアログ ボックスで 、**プロジェクトの種類**フィールドに、Windows が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="a4b79-114">選択**クラス ライブラリ**から、**テンプレート**一覧をクリックして**OK**します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="a4b79-115">新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4b79-115">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="a4b79-116">選択**新しい項目の追加**から、**プロジェクト**メニュー。</span><span class="sxs-lookup"><span data-stu-id="a4b79-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="a4b79-117">**新しい項目の追加** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4b79-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="a4b79-118">選択**COM クラス**から、**テンプレート**一覧をクリックして**追加**します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="a4b79-119">新しいクラスを追加し、COM 相互運用機能の新しいプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-119"> adds a new class and configures the new project for COM interop.</span></span>  
  
5.  <span data-ttu-id="a4b79-120">COM クラスには、プロパティ、メソッド、およびイベントのようなコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6.  <span data-ttu-id="a4b79-121">選択**ビルド ClassLibrary1**から、**ビルド**メニュー。</span><span class="sxs-lookup"><span data-stu-id="a4b79-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="a4b79-122">アセンブリがビルドされ、オペレーティング システムに COM オブジェクトを登録します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-122"> builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="a4b79-123">COM クラス テンプレートを使用せずに COM オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="a4b79-124">COM クラス テンプレートを使用する代わりに、手動での COM クラスを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a4b79-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="a4b79-125">コマンドラインから作業している場合、または COM オブジェクトの定義方法を制御する場合は、この手順をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a4b79-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="a4b79-126">COM オブジェクトを生成するプロジェクトを設定するには</span><span class="sxs-lookup"><span data-stu-id="a4b79-126">To set up your project to generate a COM object</span></span>  
  
1.  <span data-ttu-id="a4b79-127">新しい Windows アプリケーション プロジェクトを開き、**ファイル**をクリックしてメニュー **NewProject**します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2.  <span data-ttu-id="a4b79-128">**新しいプロジェクト**ダイアログ ボックスで 、**プロジェクトの種類**フィールドに、Windows が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="a4b79-129">選択**クラス ライブラリ**から、**テンプレート**一覧をクリックして**OK**します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="a4b79-130">新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4b79-130">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="a4b79-131">**ソリューション エクスプ ローラー**、プロジェクトを右クリックし、クリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="a4b79-132">**プロジェクト デザイナー**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4b79-132">The **Project Designer** is displayed.</span></span>  
  
4.  <span data-ttu-id="a4b79-133">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4b79-133">Click the **Compile** tab.</span></span>  
  
5.  <span data-ttu-id="a4b79-134">選択、 **COM 相互運用機能の登録**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="a4b79-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="a4b79-135">COM オブジェクトを作成する、クラスのコードを設定するには</span><span class="sxs-lookup"><span data-stu-id="a4b79-135">To set up the code in your class to create a COM object</span></span>  
  
1.  <span data-ttu-id="a4b79-136">**ソリューション エクスプ ローラー**をダブルクリックして**Class1.vb**そのコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2.  <span data-ttu-id="a4b79-137">クラスの名前を `ComClass1` に変更します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-137">Rename the class to `ComClass1`.</span></span>  
  
3.  <span data-ttu-id="a4b79-138">次の定数を追加`ComClass1`します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="a4b79-139">COM オブジェクトを持つ必要はグローバル一意識別子 (GUID) の定数が格納されます。</span><span class="sxs-lookup"><span data-stu-id="a4b79-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     <span data-ttu-id="a4b79-140">[!code-vb[VbVbalrInterop&#2;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a4b79-140">[!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]</span></span>  
  
4.  <span data-ttu-id="a4b79-141">**ツール** メニューのをクリックして**Guid の作成**します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-141">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="a4b79-142">**GUID の作成**ダイアログ ボックスで、をクリックして**レジストリ形式** をクリックし、**コピー**します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-142">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="a4b79-143">[ **終了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4b79-143">Click **Exit**.</span></span>  
  
5.  <span data-ttu-id="a4b79-144">空の文字列を置き換える、 `ClassId` 、guid を削除、先頭と末尾の右中かっこです。</span><span class="sxs-lookup"><span data-stu-id="a4b79-144">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="a4b79-145">たとえば、Guidgen で GUID が提供される場合は`"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"`コードは次のように表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4b79-145">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     <span data-ttu-id="a4b79-146">[!code-vb[VbVbalrInterop&#3;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a4b79-146">[!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]</span></span>  
  
6.  <span data-ttu-id="a4b79-147">前の手順を繰り返します、`InterfaceId`と`EventsId`定数は、次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="a4b79-147">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     <span data-ttu-id="a4b79-148">[!code-vb[VbVbalrInterop&4;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="a4b79-148">[!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a4b79-149">Guid は、新規および一意であるかどうかを確認します。それ以外の場合、COM コンポーネントは、他の COM コンポーネントと競合する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a4b79-149">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7.  <span data-ttu-id="a4b79-150">追加、`ComClass`属性を`ComClass1`、クラス ID、インターフェイス ID、およびイベント ID の Guid を指定する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-150">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     <span data-ttu-id="a4b79-151">[!code-vb[VbVbalrInterop&#5;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="a4b79-151">[!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]</span></span>  
  
8.  <span data-ttu-id="a4b79-152">COM クラスが必要で、パラメーターなし`Public Sub New()`コンス トラクター、またはクラスが正しく登録されません。</span><span class="sxs-lookup"><span data-stu-id="a4b79-152">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="a4b79-153">クラスには、パラメーターなしのコンス トラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-153">Add a parameterless constructor to the class:</span></span>  
  
     <span data-ttu-id="a4b79-154">[!code-vb[VbVbalrInterop&6;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="a4b79-154">[!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]</span></span>  
  
9. <span data-ttu-id="a4b79-155">プロパティ、メソッド、およびイベントを終了して、クラスに追加、`End Class`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="a4b79-155">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="a4b79-156">選択**ソリューションのビルド**から、**ビルド**メニュー。</span><span class="sxs-lookup"><span data-stu-id="a4b79-156">Select **Build Solution** from the **Build** menu.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="a4b79-157">アセンブリがビルドされ、オペレーティング システムに COM オブジェクトを登録します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-157"> builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a4b79-158">COM オブジェクトを使用して作成する[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]他では使用できません[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]アプリケーションは true。 COM オブジェクトではないためです。</span><span class="sxs-lookup"><span data-stu-id="a4b79-158">The COM objects you generate with [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot be used by other [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] applications because they are not true COM objects.</span></span> <span data-ttu-id="a4b79-159">このような COM オブジェクトへの参照の追加を試行によってエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-159">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="a4b79-160">詳細については、「 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)します。</span><span class="sxs-lookup"><span data-stu-id="a4b79-160">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b79-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4b79-161">See Also</span></span>  
 <span data-ttu-id="a4b79-162"><xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute></span><span class="sxs-lookup"><span data-stu-id="a4b79-162"><xref:Microsoft.VisualBasic.ComClassAttribute></span></span>   
<span data-ttu-id="a4b79-163"> [COM 相互運用機能](../../../visual-basic/programming-guide/com-interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="a4b79-163"> [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span></span>  
<span data-ttu-id="a4b79-164"> [チュートリアル: COM オブジェクトによる継承の実装](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span><span class="sxs-lookup"><span data-stu-id="a4b79-164"> [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span></span>  
<span data-ttu-id="a4b79-165"> [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md) </span><span class="sxs-lookup"><span data-stu-id="a4b79-165"> [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) </span></span>  
<span data-ttu-id="a4b79-166"> [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span><span class="sxs-lookup"><span data-stu-id="a4b79-166"> [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span></span>  
<span data-ttu-id="a4b79-167"> [相互運用性のトラブルシューティング](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)</span><span class="sxs-lookup"><span data-stu-id="a4b79-167"> [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)</span></span>
