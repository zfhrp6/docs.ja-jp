---
title: "Model-View-View Model を利用した汎用性のあるクラス ライブラリの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cc12a90025a1862fc6c588fe4425f3f8341da313
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="81094-102">Model-View-View Model を利用した汎用性のあるクラス ライブラリの使用</span><span class="sxs-lookup"><span data-stu-id="81094-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="81094-103">.NET Framework を使用して[ポータブル クラス ライブラリ](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)モデル-ビュー-ビュー モデル (MVVM) パターンを実装し、複数のプラットフォーム間でアセンブリを共有します。</span><span class="sxs-lookup"><span data-stu-id="81094-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>  
  
 <span data-ttu-id="81094-104">MVVM は、基になるビジネス ロジックからユーザー インターフェイスを分離するアプリケーション パターンです。</span><span class="sxs-lookup"><span data-stu-id="81094-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="81094-105">モデルとビューのモデル クラスを実装することができます、[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]プロジェクト[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、し、さまざまなプラットフォーム用にカスタマイズされたビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="81094-105">You can implement the model and view model classes in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], and then create views that are customized for different platforms.</span></span> <span data-ttu-id="81094-106">この方法では、データを記述することができますのモデルとビジネス ロジックを 1 回だけ、.NET Framework、Silverlight、Windows Phone からのコードを使用して[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリの場合、次の図に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="81094-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="81094-107">![MVVM ダイアグラムを含むポータブル](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")</span><span class="sxs-lookup"><span data-stu-id="81094-107">![Portable with MVVM diagram](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")</span></span>  
  
 <span data-ttu-id="81094-108">このトピックには、一般的なパターンについては、MVVM は行いません。</span><span class="sxs-lookup"><span data-stu-id="81094-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="81094-109">のみを使用する方法に関する情報を提供[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]MVVM を実装します。</span><span class="sxs-lookup"><span data-stu-id="81094-109">It only provides information about how to use [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] to implement MVVM.</span></span> <span data-ttu-id="81094-110">MVVM の詳細については、次を参照してください。、 [MVVM クイック スタート](https://msdn.microsoft.com/library/gg430869(v=PandP.40).aspx)です。</span><span class="sxs-lookup"><span data-stu-id="81094-110">For more information about MVVM, see the [MVVM Quickstart](https://msdn.microsoft.com/library/gg430869(v=PandP.40).aspx).</span></span>  
  
## <a name="classes-that-support-mvvm"></a><span data-ttu-id="81094-111">MVVM をサポートするクラス</span><span class="sxs-lookup"><span data-stu-id="81094-111">Classes That Support MVVM</span></span>  
 <span data-ttu-id="81094-112">対象にする場合、 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]、 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]、Silverlight、または Windows Phone 7.5 用、[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]プロジェクトでは、次のクラスは MVVM パターンを実装するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="81094-112">When you target the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, or Windows Phone 7.5 for your [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, the following classes are available for implementing the MVVM pattern:</span></span>  
  
-   <span data-ttu-id="81094-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="81094-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="81094-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="81094-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="81094-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="81094-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="81094-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="81094-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="81094-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="81094-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="81094-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="81094-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="81094-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="81094-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="81094-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="81094-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="81094-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="81094-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="81094-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="81094-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="81094-123">すべてのクラス、<xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType>名前空間</span><span class="sxs-lookup"><span data-stu-id="81094-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>  
  
## <a name="implementing-mvvm"></a><span data-ttu-id="81094-124">MVVM を実装します。</span><span class="sxs-lookup"><span data-stu-id="81094-124">Implementing MVVM</span></span>  
 <span data-ttu-id="81094-125">MVVM を実装するには、通常を作成するモデルとでは、ビュー モデルの両方、[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]ために、プロジェクト、[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]プロジェクトは、移植性のないプロジェクトを参照できません。</span><span class="sxs-lookup"><span data-stu-id="81094-125">To implement MVVM, you typically create both the model and the view model in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, because a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project cannot reference a non-portable project.</span></span> <span data-ttu-id="81094-126">モデルとビューのモデルは、同じプロジェクト内、またはそれぞれ別のプロジェクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="81094-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="81094-127">個別のプロジェクトを使用する場合は、モデル プロジェクトをビュー モデル プロジェクトからの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="81094-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>  
  
 <span data-ttu-id="81094-128">モデルをコンパイルして、モデル プロジェクトを表示すると後、は、ビューを含むアプリでそれらのアセンブリを参照します。</span><span class="sxs-lookup"><span data-stu-id="81094-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="81094-129">をビュー モデルにのみ、ビューが操作する場合のみ、ビュー モデルを含むアセンブリを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81094-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>  
  
### <a name="model"></a><span data-ttu-id="81094-130">モデル</span><span class="sxs-lookup"><span data-stu-id="81094-130">Model</span></span>  
 <span data-ttu-id="81094-131">次の例にある単純なモデル クラスを示しています、[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="81094-131">The following example shows a simplified model class that could reside in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]  
  
 <span data-ttu-id="81094-132">次の例は、設定、取得、およびデータの更新を簡単な方法を示しています、[!INCLUDE[net_portable](../../../includes/net-portable-md.md)]プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="81094-132">The following example shows a simple way to populate, retrieve, and update the data in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span> <span data-ttu-id="81094-133">実際のアプリでは、Windows Communication Foundation (WCF) サービスなどのソースからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="81094-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]  
  
### <a name="view-model"></a><span data-ttu-id="81094-134">ビュー モデル</span><span class="sxs-lookup"><span data-stu-id="81094-134">View Model</span></span>  
 <span data-ttu-id="81094-135">MVVM パターンを実装するときに、モデルの表示の基本クラスが頻繁に追加されます。</span><span class="sxs-lookup"><span data-stu-id="81094-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="81094-136">次の例では、基本クラスを示します。</span><span class="sxs-lookup"><span data-stu-id="81094-136">The following example shows a base class.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]  
  
 <span data-ttu-id="81094-137">実装、<xref:System.Windows.Input.ICommand>インターフェイスは MVVM パターンでよく使用します。</span><span class="sxs-lookup"><span data-stu-id="81094-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="81094-138"><xref:System.Windows.Input.ICommand> インターフェイスを実装する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="81094-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]  
  
 <span data-ttu-id="81094-139">次の例は、簡略化されたビュー モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="81094-139">The following example shows a simplified view model.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="81094-140">表示</span><span class="sxs-lookup"><span data-stu-id="81094-140">View</span></span>  
 <span data-ttu-id="81094-141">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]アプリ、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリ、Silverlight ベースのアプリまたは Windows Phone 7.5 アプリの場合は、モデルとビューのモデル プロジェクトを含むアセンブリを参照することができます。</span><span class="sxs-lookup"><span data-stu-id="81094-141">From a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] app, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="81094-142">連携するビューを作成するには、ビュー モデルにします。</span><span class="sxs-lookup"><span data-stu-id="81094-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="81094-143">次の例を取得し、ビュー モデルからデータを更新するシンプルな Windows Presentation Foundation (WPF) アプリを示します。</span><span class="sxs-lookup"><span data-stu-id="81094-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="81094-144">Silverlight では、Windows Phone のようなビューを作成する可能性がありますまたは[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリ。</span><span class="sxs-lookup"><span data-stu-id="81094-144">You could create similar views in Silverlight, Windows Phone, or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="81094-145">参照</span><span class="sxs-lookup"><span data-stu-id="81094-145">See Also</span></span>  
 [<span data-ttu-id="81094-146">ポータブル クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="81094-146">Portable Class Library</span></span>](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
