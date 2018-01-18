---
title: "Visual Basic でのコンポーネントの作成および使用"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 17c9b7440d60c38ba30d230f8412c3ca1a21830a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="creating-and-using-components-in-visual-basic"></a><span data-ttu-id="4eeaa-102">Visual Basic でのコンポーネントの作成および使用</span><span class="sxs-lookup"><span data-stu-id="4eeaa-102">Creating and Using Components in Visual Basic</span></span>
<span data-ttu-id="4eeaa-103">*コンポーネント*は、<xref:System.ComponentModel.IComponent?displayProperty=nameWithType> インターフェイスを実装するか、<xref:System.ComponentModel.IComponent> を実装するクラスから直接的または間接的に派生するクラスです。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-103">A *component* is a class that implements the <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> interface or that derives directly or indirectly from a class that implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="4eeaa-104">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] のコンポーネントは、再利用可能なオブジェクトで、他のオブジェクトとやり取りでき、外部リソースの制御やデザイン時サポートが備わっています。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-104">A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] component is an object that is reusable, can interact with other objects, and provides control over external resources and design-time support.</span></span>  
  
 <span data-ttu-id="4eeaa-105">コンポーネントの重要な特徴の 1 つは、コンポーネントがデザイン可能であるということです。つまり、コンポーネントであるクラスは [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 統合開発環境で使用できます。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-105">An important feature of components is that they are designable, which means that a class that is a component can be used in the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Integrated Development Environment.</span></span> <span data-ttu-id="4eeaa-106">コンポーネントは、ツールボックスへの追加、フォームへのドラッグ アンド ドロップ、デザイン サーフェイスでの操作が可能です。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-106">A component can be added to the Toolbox, dragged and dropped onto a form, and manipulated on a design surface.</span></span> <span data-ttu-id="4eeaa-107">コンポーネントの基本のデザイン時サポートは [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] に組み込まれているため、コンポーネント開発者は追加の作業を行わずに基本のデザイン時機能を利用できます。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-107">Notice that base design-time support for components is built into the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]; a component developer does not have to do any additional work to take advantage of the base design-time functionality.</span></span>  
  
 <span data-ttu-id="4eeaa-108">デザイン可能という点では、"*コントロール*" もコンポーネントに似ています。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-108">A *control* is similar to a component, as both are designable.</span></span> <span data-ttu-id="4eeaa-109">ただし、コントロールにはユーザー インターフェイスが用意されているのに対し、コンポーネントには用意されていません。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-109">However, a control provides a user interface, while a component does not.</span></span> <span data-ttu-id="4eeaa-110">コントロールは基本コントロール クラスである <xref:System.Windows.Forms.Control> または <xref:System.Web.UI.Control> から派生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-110">A control must derive from one of the base control classes: <xref:System.Windows.Forms.Control> or <xref:System.Web.UI.Control>.</span></span>  
  
## <a name="when-to-create-a-component"></a><span data-ttu-id="4eeaa-111">コンポーネントを作成する状況</span><span class="sxs-lookup"><span data-stu-id="4eeaa-111">When to Create a Component</span></span>  
 <span data-ttu-id="4eeaa-112">デザイン サーフェイス (Windows フォーム デザイナーや Web フォーム デザイナーなど) で使用するクラスにユーザー インターフェイスがない場合、そのクラスは、コンポーネントにして、<xref:System.ComponentModel.IComponent> を実装するか、<xref:System.ComponentModel.IComponent> を直接または間接的に実装するクラスから派生させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-112">If your class will be used on a design surface (such as the Windows Forms or Web Forms Designer) but has no user interface, it should be a component and implement <xref:System.ComponentModel.IComponent>, or derive from a class that directly or indirectly implements <xref:System.ComponentModel.IComponent>.</span></span>  
  
 <span data-ttu-id="4eeaa-113"><xref:System.ComponentModel.Component> クラスと <xref:System.ComponentModel.MarshalByValueComponent> クラスは、<xref:System.ComponentModel.IComponent> インターフェイスの基本実装です。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-113">The <xref:System.ComponentModel.Component> and <xref:System.ComponentModel.MarshalByValueComponent> classes are base implementations of the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="4eeaa-114">これらのクラスの主な違いは、<xref:System.ComponentModel.Component> クラスは参照渡しでマーシャリングされ、<xref:System.ComponentModel.IComponent> は値渡しでマーシャリングされることにあります。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-114">The main difference between these classes is that the <xref:System.ComponentModel.Component> class is marshaled by reference, while <xref:System.ComponentModel.IComponent> is marshaled by value.</span></span> <span data-ttu-id="4eeaa-115">実装のためのガイドラインを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-115">The following list provides broad guidelines for implementers.</span></span>  
  
-   <span data-ttu-id="4eeaa-116">コンポーネントを参照渡しでマーシャリングする必要がある場合は、<xref:System.ComponentModel.Component> から派生させます。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-116">If your component needs to be marshaled by reference, derive from <xref:System.ComponentModel.Component>.</span></span>  
  
-   <span data-ttu-id="4eeaa-117">コンポーネントを値渡しでマーシャリングする必要がある場合は、<xref:System.ComponentModel.MarshalByValueComponent> から派生させます。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-117">If your component needs to be marshaled by value, derive from <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
-   <span data-ttu-id="4eeaa-118">単一継承が原因でいずれかの基本実装からコンポーネントを派生できない場合は、<xref:System.ComponentModel.IComponent> を実装します。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-118">If your component cannot derive from one of the base implementations due to single inheritance, implement <xref:System.ComponentModel.IComponent>.</span></span>  
  
## <a name="component-classes"></a><span data-ttu-id="4eeaa-119">コンポーネントのクラス</span><span class="sxs-lookup"><span data-stu-id="4eeaa-119">Component Classes</span></span>  
 <span data-ttu-id="4eeaa-120"><xref:System.ComponentModel> 名前空間は、コンポーネントとコントロールの実行時およびデザイン時の動作を実装するために使用できるクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-120">The <xref:System.ComponentModel> namespace provides classes that are used to implement the run-time and design-time behavior of components and controls.</span></span> <span data-ttu-id="4eeaa-121">この名前空間には、属性と型コンバーターの実装、データ ソースへのバインド、コンポーネントのライセンス処理のための基底クラスと基底インターフェイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-121">This namespace includes the base classes and interfaces for implementing attributes and type converters, binding to data sources, and licensing components.</span></span>  
  
 <span data-ttu-id="4eeaa-122">核となるコンポーネント クラスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-122">The core component classes are:</span></span>  
  
-   <span data-ttu-id="4eeaa-123"><xref:System.ComponentModel.Component>。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-123"><xref:System.ComponentModel.Component>.</span></span> <span data-ttu-id="4eeaa-124"><xref:System.ComponentModel.IComponent> インターフェイスの基本実装。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-124">A base implementation for the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="4eeaa-125">このクラスにより、アプリケーション間でオブジェクトの共有が可能になります。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-125">This class enables object sharing between applications.</span></span>  
  
-   <span data-ttu-id="4eeaa-126"><xref:System.ComponentModel.MarshalByValueComponent>。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-126"><xref:System.ComponentModel.MarshalByValueComponent>.</span></span> <span data-ttu-id="4eeaa-127"><xref:System.ComponentModel.IComponent> インターフェイスの基本実装。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-127">A base implementation for the <xref:System.ComponentModel.IComponent> interface.</span></span>  
  
-   <span data-ttu-id="4eeaa-128"><xref:System.ComponentModel.Container>。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-128"><xref:System.ComponentModel.Container>.</span></span> <span data-ttu-id="4eeaa-129"><xref:System.ComponentModel.IContainer> インターフェイスの基本実装。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-129">The base implementation for the <xref:System.ComponentModel.IContainer> interface.</span></span> <span data-ttu-id="4eeaa-130">このクラスは、0 個以上のコンポーネントをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-130">This class encapsulates zero or more components.</span></span>  
  
 <span data-ttu-id="4eeaa-131">コンポーネントのライセンス処理に使用するクラスのいくつかを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-131">Some of the classes used for component licensing are:</span></span>  
  
-   <span data-ttu-id="4eeaa-132"><xref:System.ComponentModel.License>。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-132"><xref:System.ComponentModel.License>.</span></span> <span data-ttu-id="4eeaa-133">すべてのライセンスの抽象基底クラスです。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-133">The abstract base class for all licenses.</span></span> <span data-ttu-id="4eeaa-134">ライセンスは、コンポーネントの特定のインスタンスに付与されます。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-134">A license is granted to a specific instance of a component.</span></span>  
  
-   <span data-ttu-id="4eeaa-135"><xref:System.ComponentModel.LicenseManager>。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-135"><xref:System.ComponentModel.LicenseManager>.</span></span> <span data-ttu-id="4eeaa-136">コンポーネントにライセンスを追加し、<xref:System.ComponentModel.LicenseProvider> を管理するためのプロパティとメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-136">Provides properties and methods to add a license to a component and to manage a <xref:System.ComponentModel.LicenseProvider>.</span></span>  
  
-   <span data-ttu-id="4eeaa-137"><xref:System.ComponentModel.LicenseProvider>。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-137"><xref:System.ComponentModel.LicenseProvider>.</span></span> <span data-ttu-id="4eeaa-138">ライセンス プロバイダーを実装するための抽象基底クラスです。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-138">The abstract base class for implementing a license provider.</span></span>  
  
-   <span data-ttu-id="4eeaa-139"><xref:System.ComponentModel.LicenseProviderAttribute>。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-139"><xref:System.ComponentModel.LicenseProviderAttribute>.</span></span> <span data-ttu-id="4eeaa-140">クラスで使用する <xref:System.ComponentModel.LicenseProvider> クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-140">Specifies the <xref:System.ComponentModel.LicenseProvider> class to use with a class.</span></span>  
  
 <span data-ttu-id="4eeaa-141">コンポーネントの説明や永続化に一般的に使用するクラスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-141">Classes commonly used for describing and persisting components.</span></span>  
  
-   <span data-ttu-id="4eeaa-142"><xref:System.ComponentModel.TypeDescriptor>。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-142"><xref:System.ComponentModel.TypeDescriptor>.</span></span> <span data-ttu-id="4eeaa-143">属性、プロパティ、イベントなど、コンポーネントの特性に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-143">Provides information about the characteristics for a component, such as its attributes, properties, and events.</span></span>  
  
-   <span data-ttu-id="4eeaa-144"><xref:System.ComponentModel.EventDescriptor>。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-144"><xref:System.ComponentModel.EventDescriptor>.</span></span> <span data-ttu-id="4eeaa-145">イベントに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-145">Provides information about an event.</span></span>  
  
-   <span data-ttu-id="4eeaa-146"><xref:System.ComponentModel.PropertyDescriptor>。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-146"><xref:System.ComponentModel.PropertyDescriptor>.</span></span> <span data-ttu-id="4eeaa-147">プロパティに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-147">Provides information about a property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4eeaa-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="4eeaa-148">Related Sections</span></span>  
 [<span data-ttu-id="4eeaa-149">コントロールとコンポーネントの作成時のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="4eeaa-149">Troubleshooting Control and Component Authoring</span></span>](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="4eeaa-150">一般的な問題に対処する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4eeaa-150">Explains how to fix common problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eeaa-151">参照</span><span class="sxs-lookup"><span data-stu-id="4eeaa-151">See Also</span></span>  
 [<span data-ttu-id="4eeaa-152">方法: Windows フォームでデザイン時サポートにアクセスする</span><span class="sxs-lookup"><span data-stu-id="4eeaa-152">How to: Access Design-Time Support in Windows Forms</span></span>](../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 
