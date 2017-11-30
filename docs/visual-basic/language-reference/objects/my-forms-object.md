---
title: "My.Forms オブジェクト"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords: My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a5aa7af1f07a29660335d968c1ecc17be5f8beec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="myforms-object"></a><span data-ttu-id="13b1a-102">My.Forms オブジェクト</span><span class="sxs-lookup"><span data-stu-id="13b1a-102">My.Forms Object</span></span>
<span data-ttu-id="13b1a-103">現在のプロジェクトで宣言されている各 Windows フォームのインスタンスにアクセスするためには、プロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="13b1a-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13b1a-104">コメント</span><span class="sxs-lookup"><span data-stu-id="13b1a-104">Remarks</span></span>  
 <span data-ttu-id="13b1a-105">`My.Forms`オブジェクトが現在のプロジェクト内の各フォームのインスタンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="13b1a-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="13b1a-106">プロパティの名前は、プロパティにアクセスするフォームの名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="13b1a-106">The name of the property is the same as the name of the form that the property accesses.</span></span> <span data-ttu-id="13b1a-107">プロジェクトにフォームを追加する方法の詳細については、次を参照してください。[する方法: Windows フォームをプロジェクトに追加](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)です。</span><span class="sxs-lookup"><span data-stu-id="13b1a-107">For information about adding forms to a project, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="13b1a-108">によって提供されるフォームにアクセスすることができます、`My.Forms`修飾なし、フォームの名前を使用してオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="13b1a-108">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="13b1a-109">プロパティ名がフォームの型名と同じであるため、これにより、既定のインスタンスがあった場合、フォームにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="13b1a-109">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="13b1a-110">たとえば、`My.Forms.Form1.Show` は、`Form1.Show` と同じです。</span><span class="sxs-lookup"><span data-stu-id="13b1a-110">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="13b1a-111">`My.Forms`オブジェクトは、現在のプロジェクトに関連付けられているフォームのみを公開します。</span><span class="sxs-lookup"><span data-stu-id="13b1a-111">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="13b1a-112">参照された Dll で宣言されているフォームへのアクセスは提供されません。</span><span class="sxs-lookup"><span data-stu-id="13b1a-112">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="13b1a-113">DLL を提供するフォームにアクセスするには、として書き込まれる、フォームの修飾名を使用する必要があります*DllName*.*フォーム名*です。</span><span class="sxs-lookup"><span data-stu-id="13b1a-113">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="13b1a-114">使用することができます、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>アプリケーションのすべての開いているフォームのコレクションを取得するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="13b1a-114">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="13b1a-115">オブジェクトとそのプロパティは、Windows アプリケーションでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="13b1a-115">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="13b1a-116">プロパティ</span><span class="sxs-lookup"><span data-stu-id="13b1a-116">Properties</span></span>  
 <span data-ttu-id="13b1a-117">各プロパティ、`My.Forms`オブジェクトが現在のプロジェクトにフォームのインスタンスへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="13b1a-117">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="13b1a-118">プロパティの名前は、プロパティにアクセスする、フォームの名前と同じとプロパティの型が、フォームの型と同じです。</span><span class="sxs-lookup"><span data-stu-id="13b1a-118">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13b1a-119">名前の競合がある場合、フォームにアクセスするプロパティ名は*RootNamespace*_*Namespace*\_*フォーム*です。</span><span class="sxs-lookup"><span data-stu-id="13b1a-119">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="13b1a-120">たとえば、という 2 つのフォーム`Form1.`かどうか、ルート名前空間でこれらの形式の 1 つは`WindowsApplication1`と名前空間に`Namespace1`、通じてそのフォームにアクセス`My.Forms.WindowsApplication1_Namespace1_Form1`です。</span><span class="sxs-lookup"><span data-stu-id="13b1a-120">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="13b1a-121">`My.Forms`オブジェクトは、スタートアップ時に作成されたアプリケーションのメイン フォームのインスタンスへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="13b1a-121">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="13b1a-122">その他のすべてのフォーム、`My.Forms`へのアクセスがおよび格納時にオブジェクトをフォームの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="13b1a-122">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="13b1a-123">そのプロパティにアクセスしようとするとは、フォームのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="13b1a-123">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="13b1a-124">割り当てることによって、フォームの破棄する`Nothing`そのフォームのプロパティにします。</span><span class="sxs-lookup"><span data-stu-id="13b1a-124">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="13b1a-125">プロパティ set アクセス操作子の呼び出し、<xref:System.Windows.Forms.Form.Close%2A>フォーム、し、割り当てますメソッド`Nothing`に格納されている値。</span><span class="sxs-lookup"><span data-stu-id="13b1a-125">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="13b1a-126">以外の任意の値を割り当てる場合`Nothing`プロパティの setter がスローされます、<xref:System.ArgumentException>例外。</span><span class="sxs-lookup"><span data-stu-id="13b1a-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="13b1a-127">プロパティかどうかをテストすることができます、`My.Forms`オブジェクトを使用して、フォームのインスタンスが格納されて、`Is`または`IsNot`演算子。</span><span class="sxs-lookup"><span data-stu-id="13b1a-127">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="13b1a-128">これらの演算子を使用するには、プロパティの値をチェックする`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="13b1a-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13b1a-129">通常、`Is`または`IsNot`オペレーターが、比較を実行するプロパティの値を読み取ることがあります。</span><span class="sxs-lookup"><span data-stu-id="13b1a-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="13b1a-130">ただし場合、プロパティが現在格納`Nothing`プロパティ、フォームの新しいインスタンスを作成し、そのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="13b1a-130">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="13b1a-131">ただし、Visual Basic コンパイラがのプロパティを処理、`My.Forms`オブジェクトが異なることができ、`Is`または`IsNot`演算子をその値を変更することがなく、プロパティの状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="13b1a-131">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13b1a-132">例</span><span class="sxs-lookup"><span data-stu-id="13b1a-132">Example</span></span>  
 <span data-ttu-id="13b1a-133">この例は、既定のタイトルを変更`SidebarMenu`フォーム。</span><span class="sxs-lookup"><span data-stu-id="13b1a-133">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 <span data-ttu-id="13b1a-134">この例を実行するため、プロジェクトがという名前のフォーム`SidebarMenu`です。</span><span class="sxs-lookup"><span data-stu-id="13b1a-134">For this example to work, your project must have a form named `SidebarMenu`.</span></span> <span data-ttu-id="13b1a-135">詳細については、次を参照してください。[する方法: Windows フォームをプロジェクトに追加](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)です。</span><span class="sxs-lookup"><span data-stu-id="13b1a-135">For more information, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="13b1a-136">このコードは、Windows アプリケーション プロジェクトでのみ動作します。</span><span class="sxs-lookup"><span data-stu-id="13b1a-136">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13b1a-137">要件</span><span class="sxs-lookup"><span data-stu-id="13b1a-137">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="13b1a-138">プロジェクトの種類別の可用性</span><span class="sxs-lookup"><span data-stu-id="13b1a-138">Availability by Project Type</span></span>  
  
|<span data-ttu-id="13b1a-139">プロジェクトの種類</span><span class="sxs-lookup"><span data-stu-id="13b1a-139">Project type</span></span>|<span data-ttu-id="13b1a-140">使用可能</span><span class="sxs-lookup"><span data-stu-id="13b1a-140">Available</span></span>|  
|---|---|  
|<span data-ttu-id="13b1a-141">Windows アプリケーション</span><span class="sxs-lookup"><span data-stu-id="13b1a-141">Windows Application</span></span>|<span data-ttu-id="13b1a-142">**はい**</span><span class="sxs-lookup"><span data-stu-id="13b1a-142">**Yes**</span></span>|  
|<span data-ttu-id="13b1a-143">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="13b1a-143">Class Library</span></span>|<span data-ttu-id="13b1a-144">いいえ</span><span class="sxs-lookup"><span data-stu-id="13b1a-144">No</span></span>|  
|<span data-ttu-id="13b1a-145">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="13b1a-145">Console Application</span></span>|<span data-ttu-id="13b1a-146">いいえ</span><span class="sxs-lookup"><span data-stu-id="13b1a-146">No</span></span>|  
|<span data-ttu-id="13b1a-147">Windows コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="13b1a-147">Windows Control Library</span></span>|<span data-ttu-id="13b1a-148">いいえ</span><span class="sxs-lookup"><span data-stu-id="13b1a-148">No</span></span>|  
|<span data-ttu-id="13b1a-149">Web コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="13b1a-149">Web Control Library</span></span>|<span data-ttu-id="13b1a-150">いいえ</span><span class="sxs-lookup"><span data-stu-id="13b1a-150">No</span></span>|  
|<span data-ttu-id="13b1a-151">Windows サービス</span><span class="sxs-lookup"><span data-stu-id="13b1a-151">Windows Service</span></span>|<span data-ttu-id="13b1a-152">いいえ</span><span class="sxs-lookup"><span data-stu-id="13b1a-152">No</span></span>|  
|<span data-ttu-id="13b1a-153">Web サイト</span><span class="sxs-lookup"><span data-stu-id="13b1a-153">Web Site</span></span>|<span data-ttu-id="13b1a-154">いいえ</span><span class="sxs-lookup"><span data-stu-id="13b1a-154">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13b1a-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="13b1a-155">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [<span data-ttu-id="13b1a-156">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="13b1a-156">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)  
 [<span data-ttu-id="13b1a-157">方法: Windows フォームをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="13b1a-157">How to: Add Windows Forms to a Project</span></span>](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)  
 [<span data-ttu-id="13b1a-158">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="13b1a-158">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="13b1a-159">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="13b1a-159">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="13b1a-160">アプリケーション フォームへのアクセス</span><span class="sxs-lookup"><span data-stu-id="13b1a-160">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
