---
title: "Visual Basic でのコンポーネントの作成および使用"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
caps.latest.revision: 9
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 03929dd0dbb81a9efee5b69ede78ff0b4ab4d380
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="creating-and-using-components-in-visual-basic"></a><span data-ttu-id="c395b-102">Visual Basic でのコンポーネントの作成および使用</span><span class="sxs-lookup"><span data-stu-id="c395b-102">Creating and Using Components in Visual Basic</span></span>
<span data-ttu-id="c395b-103">*コンポーネント*は、<xref:System.ComponentModel.IComponent?displayProperty=fullName> インターフェイスを実装するか、<xref:System.ComponentModel.IComponent> を実装するクラスから直接的または間接的に派生するクラスです。</span><span class="sxs-lookup"><span data-stu-id="c395b-103">A *component* is a class that implements the <xref:System.ComponentModel.IComponent?displayProperty=fullName> interface or that derives directly or indirectly from a class that implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="c395b-104">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] のコンポーネントは、再利用可能なオブジェクトで、他のオブジェクトとやり取りでき、外部リソースの制御やデザイン時サポートが備わっています。</span><span class="sxs-lookup"><span data-stu-id="c395b-104">A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] component is an object that is reusable, can interact with other objects, and provides control over external resources and design-time support.</span></span>  
  
 <span data-ttu-id="c395b-105">コンポーネントの重要な特徴の 1 つは、コンポーネントがデザイン可能であるということです。つまり、コンポーネントであるクラスは [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 統合開発環境で使用できます。</span><span class="sxs-lookup"><span data-stu-id="c395b-105">An important feature of components is that they are designable, which means that a class that is a component can be used in the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Integrated Development Environment.</span></span> <span data-ttu-id="c395b-106">コンポーネントは、ツールボックスへの追加、フォームへのドラッグ アンド ドロップ、デザイン サーフェイスでの操作が可能です。</span><span class="sxs-lookup"><span data-stu-id="c395b-106">A component can be added to the Toolbox, dragged and dropped onto a form, and manipulated on a design surface.</span></span> <span data-ttu-id="c395b-107">コンポーネントの基本のデザイン時サポートは [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] に組み込まれているため、コンポーネント開発者は追加の作業を行わずに基本のデザイン時機能を利用できます。</span><span class="sxs-lookup"><span data-stu-id="c395b-107">Notice that base design-time support for components is built into the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]; a component developer does not have to do any additional work to take advantage of the base design-time functionality.</span></span>  
  
 <span data-ttu-id="c395b-108">デザイン可能という点では、"*コントロール*" もコンポーネントに似ています。</span><span class="sxs-lookup"><span data-stu-id="c395b-108">A *control* is similar to a component, as both are designable.</span></span> <span data-ttu-id="c395b-109">ただし、コントロールにはユーザー インターフェイスが用意されているのに対し、コンポーネントには用意されていません。</span><span class="sxs-lookup"><span data-stu-id="c395b-109">However, a control provides a user interface, while a component does not.</span></span> <span data-ttu-id="c395b-110">コントロールは基本コントロール クラスである <xref:System.Windows.Forms.Control> または <xref:System.Web.UI.Control> から派生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c395b-110">A control must derive from one of the base control classes: <xref:System.Windows.Forms.Control> or <xref:System.Web.UI.Control>.</span></span>  
  
## <a name="when-to-create-a-component"></a><span data-ttu-id="c395b-111">コンポーネントを作成する状況</span><span class="sxs-lookup"><span data-stu-id="c395b-111">When to Create a Component</span></span>  
 <span data-ttu-id="c395b-112">デザイン サーフェイス (Windows フォーム デザイナーや Web フォーム デザイナーなど) で使用するクラスにユーザー インターフェイスがない場合、そのクラスは、コンポーネントにして、<xref:System.ComponentModel.IComponent> を実装するか、<xref:System.ComponentModel.IComponent> を直接または間接的に実装するクラスから派生させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="c395b-112">If your class will be used on a design surface (such as the Windows Forms or Web Forms Designer) but has no user interface, it should be a component and implement <xref:System.ComponentModel.IComponent>, or derive from a class that directly or indirectly implements <xref:System.ComponentModel.IComponent>.</span></span>  
  
 <span data-ttu-id="c395b-113"><xref:System.ComponentModel.Component> クラスと <xref:System.ComponentModel.MarshalByValueComponent> クラスは、<xref:System.ComponentModel.IComponent> インターフェイスの基本実装です。</span><span class="sxs-lookup"><span data-stu-id="c395b-113">The <xref:System.ComponentModel.Component> and <xref:System.ComponentModel.MarshalByValueComponent> classes are base implementations of the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="c395b-114">これらのクラスの主な違いは、<xref:System.ComponentModel.Component> クラスは参照渡しでマーシャリングされ、<xref:System.ComponentModel.IComponent> は値渡しでマーシャリングされることにあります。</span><span class="sxs-lookup"><span data-stu-id="c395b-114">The main difference between these classes is that the <xref:System.ComponentModel.Component> class is marshaled by reference, while <xref:System.ComponentModel.IComponent> is marshaled by value.</span></span> <span data-ttu-id="c395b-115">実装のためのガイドラインを次に示します。</span><span class="sxs-lookup"><span data-stu-id="c395b-115">The following list provides broad guidelines for implementers.</span></span>  
  
-   <span data-ttu-id="c395b-116">コンポーネントを参照渡しでマーシャリングする必要がある場合は、<xref:System.ComponentModel.Component> から派生させます。</span><span class="sxs-lookup"><span data-stu-id="c395b-116">If your component needs to be marshaled by reference, derive from <xref:System.ComponentModel.Component>.</span></span>  
  
-   <span data-ttu-id="c395b-117">コンポーネントを値渡しでマーシャリングする必要がある場合は、<xref:System.ComponentModel.MarshalByValueComponent> から派生させます。</span><span class="sxs-lookup"><span data-stu-id="c395b-117">If your component needs to be marshaled by value, derive from <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
-   <span data-ttu-id="c395b-118">単一継承が原因でいずれかの基本実装からコンポーネントを派生できない場合は、<xref:System.ComponentModel.IComponent> を実装します。</span><span class="sxs-lookup"><span data-stu-id="c395b-118">If your component cannot derive from one of the base implementations due to single inheritance, implement <xref:System.ComponentModel.IComponent>.</span></span>  
  
 <span data-ttu-id="c395b-119">デザイン時サポートの詳細については、「[コンポーネントのデザイン時属性](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)」および「[デザイン時サポートの拡張](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c395b-119">For more information about design-time support, see [Design-Time Attributes for Components](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3) and [Extending Design-Time Support](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).</span></span>  
  
## <a name="component-classes"></a><span data-ttu-id="c395b-120">コンポーネントのクラス</span><span class="sxs-lookup"><span data-stu-id="c395b-120">Component Classes</span></span>  
 <span data-ttu-id="c395b-121"><xref:System.ComponentModel> 名前空間は、コンポーネントとコントロールの実行時およびデザイン時の動作を実装するために使用できるクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="c395b-121">The <xref:System.ComponentModel> namespace provides classes that are used to implement the run-time and design-time behavior of components and controls.</span></span> <span data-ttu-id="c395b-122">この名前空間には、属性と型コンバーターの実装、データ ソースへのバインド、コンポーネントのライセンス処理のための基底クラスと基底インターフェイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c395b-122">This namespace includes the base classes and interfaces for implementing attributes and type converters, binding to data sources, and licensing components.</span></span>  
  
 <span data-ttu-id="c395b-123">核となるコンポーネント クラスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c395b-123">The core component classes are:</span></span>  
  
-   <span data-ttu-id="c395b-124"><xref:System.ComponentModel.Component>。</span><span class="sxs-lookup"><span data-stu-id="c395b-124"><xref:System.ComponentModel.Component>.</span></span> <span data-ttu-id="c395b-125"><xref:System.ComponentModel.IComponent> インターフェイスの基本実装。</span><span class="sxs-lookup"><span data-stu-id="c395b-125">A base implementation for the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="c395b-126">このクラスにより、アプリケーション間でオブジェクトの共有が可能になります。</span><span class="sxs-lookup"><span data-stu-id="c395b-126">This class enables object sharing between applications.</span></span>  
  
-   <span data-ttu-id="c395b-127"><xref:System.ComponentModel.MarshalByValueComponent>。</span><span class="sxs-lookup"><span data-stu-id="c395b-127"><xref:System.ComponentModel.MarshalByValueComponent>.</span></span> <span data-ttu-id="c395b-128"><xref:System.ComponentModel.IComponent> インターフェイスの基本実装。</span><span class="sxs-lookup"><span data-stu-id="c395b-128">A base implementation for the <xref:System.ComponentModel.IComponent> interface.</span></span>  
  
-   <span data-ttu-id="c395b-129"><xref:System.ComponentModel.Container>。</span><span class="sxs-lookup"><span data-stu-id="c395b-129"><xref:System.ComponentModel.Container>.</span></span> <span data-ttu-id="c395b-130"><xref:System.ComponentModel.IContainer> インターフェイスの基本実装。</span><span class="sxs-lookup"><span data-stu-id="c395b-130">The base implementation for the <xref:System.ComponentModel.IContainer> interface.</span></span> <span data-ttu-id="c395b-131">このクラスは、0 個以上のコンポーネントをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="c395b-131">This class encapsulates zero or more components.</span></span>  
  
 <span data-ttu-id="c395b-132">コンポーネントのライセンス処理に使用するクラスのいくつかを次に示します。</span><span class="sxs-lookup"><span data-stu-id="c395b-132">Some of the classes used for component licensing are:</span></span>  
  
-   <span data-ttu-id="c395b-133"><xref:System.ComponentModel.License>。</span><span class="sxs-lookup"><span data-stu-id="c395b-133"><xref:System.ComponentModel.License>.</span></span> <span data-ttu-id="c395b-134">すべてのライセンスの抽象基底クラスです。</span><span class="sxs-lookup"><span data-stu-id="c395b-134">The abstract base class for all licenses.</span></span> <span data-ttu-id="c395b-135">ライセンスは、コンポーネントの特定のインスタンスに付与されます。</span><span class="sxs-lookup"><span data-stu-id="c395b-135">A license is granted to a specific instance of a component.</span></span>  
  
-   <span data-ttu-id="c395b-136"><xref:System.ComponentModel.LicenseManager>。</span><span class="sxs-lookup"><span data-stu-id="c395b-136"><xref:System.ComponentModel.LicenseManager>.</span></span> <span data-ttu-id="c395b-137">コンポーネントにライセンスを追加し、<xref:System.ComponentModel.LicenseProvider> を管理するためのプロパティとメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c395b-137">Provides properties and methods to add a license to a component and to manage a <xref:System.ComponentModel.LicenseProvider>.</span></span>  
  
-   <span data-ttu-id="c395b-138"><xref:System.ComponentModel.LicenseProvider>。</span><span class="sxs-lookup"><span data-stu-id="c395b-138"><xref:System.ComponentModel.LicenseProvider>.</span></span> <span data-ttu-id="c395b-139">ライセンス プロバイダーを実装するための抽象基底クラスです。</span><span class="sxs-lookup"><span data-stu-id="c395b-139">The abstract base class for implementing a license provider.</span></span>  
  
-   <span data-ttu-id="c395b-140"><xref:System.ComponentModel.LicenseProviderAttribute>。</span><span class="sxs-lookup"><span data-stu-id="c395b-140"><xref:System.ComponentModel.LicenseProviderAttribute>.</span></span> <span data-ttu-id="c395b-141">クラスで使用する <xref:System.ComponentModel.LicenseProvider> クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="c395b-141">Specifies the <xref:System.ComponentModel.LicenseProvider> class to use with a class.</span></span>  
  
 <span data-ttu-id="c395b-142">コンポーネントの説明や永続化に一般的に使用するクラスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="c395b-142">Classes commonly used for describing and persisting components.</span></span>  
  
-   <span data-ttu-id="c395b-143"><xref:System.ComponentModel.TypeDescriptor>。</span><span class="sxs-lookup"><span data-stu-id="c395b-143"><xref:System.ComponentModel.TypeDescriptor>.</span></span> <span data-ttu-id="c395b-144">属性、プロパティ、イベントなど、コンポーネントの特性に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c395b-144">Provides information about the characteristics for a component, such as its attributes, properties, and events.</span></span>  
  
-   <span data-ttu-id="c395b-145"><xref:System.ComponentModel.EventDescriptor>。</span><span class="sxs-lookup"><span data-stu-id="c395b-145"><xref:System.ComponentModel.EventDescriptor>.</span></span> <span data-ttu-id="c395b-146">イベントに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c395b-146">Provides information about an event.</span></span>  
  
-   <span data-ttu-id="c395b-147"><xref:System.ComponentModel.PropertyDescriptor>。</span><span class="sxs-lookup"><span data-stu-id="c395b-147"><xref:System.ComponentModel.PropertyDescriptor>.</span></span> <span data-ttu-id="c395b-148">プロパティに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c395b-148">Provides information about a property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c395b-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="c395b-149">Related Sections</span></span>  
 [<span data-ttu-id="c395b-150">クラス、コンポーネント、コントロール</span><span class="sxs-lookup"><span data-stu-id="c395b-150">Class vs. Component vs. Control</span></span>](http://msdn.microsoft.com/library/db8b842e-44d9-40cc-a0f8-70fd189632c3)  
 <span data-ttu-id="c395b-151">"*コンポーネント*" と "*コントロール*" を定義し、それらとクラスの違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c395b-151">Defines *component* and *control*, and discusses the differences between them and classes.</span></span>  
  
 [<span data-ttu-id="c395b-152">コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="c395b-152">Component Authoring</span></span>](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 <span data-ttu-id="c395b-153">コンポーネントの使用を始めるためのロードマップです。</span><span class="sxs-lookup"><span data-stu-id="c395b-153">Roadmap for getting started with components.</span></span>  
  
 [<span data-ttu-id="c395b-154">コンポーネント作成のチュートリアル</span><span class="sxs-lookup"><span data-stu-id="c395b-154">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 <span data-ttu-id="c395b-155">コンポーネント プログラミングの詳細な手順について説明するトピックへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="c395b-155">Links to topics that provide step-by-step instruction for component programming.</span></span>  
  
 [<span data-ttu-id="c395b-156">コンポーネントのクラス</span><span class="sxs-lookup"><span data-stu-id="c395b-156">Component Classes</span></span>](http://msdn.microsoft.com/library/ce2e5647-e673-4c2b-8125-ffebbd9d71bc)  
 <span data-ttu-id="c395b-157">クラスをコンポーネントにするために必要な要素、コンポーネントの機能を公開する方法、コンポーネントへのアクセスの制御、コンポーネントのインスタンスの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c395b-157">Describes what makes a class a component, ways to expose component functionality, controlling access to components, and controlling how component instances are created.</span></span>  
  
 [<span data-ttu-id="c395b-158">コントロールとコンポーネントの作成時のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c395b-158">Troubleshooting Control and Component Authoring</span></span>](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="c395b-159">一般的な問題に対処する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c395b-159">Explains how to fix common problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c395b-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="c395b-160">See Also</span></span>  
 <span data-ttu-id="c395b-161">[方法: Windows フォームでデザイン時サポートにアクセスする](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09) </span><span class="sxs-lookup"><span data-stu-id="c395b-161">[How to: Access Design-Time Support in Windows Forms](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09) </span></span>  
 <span data-ttu-id="c395b-162">[方法: デザイン モードでコントロールの外観と動作を拡張する](http://msdn.microsoft.com/library/68f85054-2253-47f5-a4f2-3f1ac8c9f27b) </span><span class="sxs-lookup"><span data-stu-id="c395b-162">[How to: Extend the Appearance and Behavior of Controls in Design Mode](http://msdn.microsoft.com/library/68f85054-2253-47f5-a4f2-3f1ac8c9f27b) </span></span>  
 [<span data-ttu-id="c395b-163">方法: デザイン モードでコントロールのカスタム初期化を行う</span><span class="sxs-lookup"><span data-stu-id="c395b-163">How to: Perform Custom Initialization for Controls in Design Mode</span></span>](http://msdn.microsoft.com/library/914eaa03-092f-4556-9160-b8a2a40641d9)

