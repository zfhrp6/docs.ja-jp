---
title: "チュートリアル : 拡張性のあるアプリケーションの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [.NET Framework], add-in pipeline
- host-side adapters for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], creating
- add-in-side adapter [.NET Framework]
- contracts for add-in pipelines [.NET Framework]
ms.assetid: 694a33c5-a040-450d-aed5-ac49fc88ce61
caps.latest.revision: "32"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6609f30844421f94965fbe05114db96ed8edbb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-an-extensible-application"></a><span data-ttu-id="a0074-102">チュートリアル : 拡張性のあるアプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="a0074-102">Walkthrough: Creating an Extensible Application</span></span>
<span data-ttu-id="a0074-103">このチュートリアルでは、簡単な電卓の機能を実行するアドイン用のパイプラインを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a0074-103">This walkthrough describes how to create a pipeline for an add-in that performs simple calculator functions.</span></span> <span data-ttu-id="a0074-104">実際のシナリオでは; は示しません代わりに、パイプラインとどのように追加のサービスを提供できるホストの基本機能を示します。</span><span class="sxs-lookup"><span data-stu-id="a0074-104">It does not demonstrate a real-world scenario; rather, it demonstrates the basic functionality of a pipeline and how an add-in can provide services for a host.</span></span>  
  
 <span data-ttu-id="a0074-105">このチュートリアルでは、次のタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a0074-105">This walkthrough describes the following tasks:</span></span>  
  
-   <span data-ttu-id="a0074-106">Visual Studio ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0074-106">Creating a Visual Studio solution.</span></span>  
  
-   <span data-ttu-id="a0074-107">パイプライン ディレクトリ構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="a0074-107">Creating the pipeline directory structure.</span></span>  
  
-   <span data-ttu-id="a0074-108">コントラクトおよびビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0074-108">Creating the contract and views.</span></span>  
  
-   <span data-ttu-id="a0074-109">アドイン側アダプターを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0074-109">Creating the add-in-side adapter.</span></span>  
  
-   <span data-ttu-id="a0074-110">ホスト側のアダプターを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0074-110">Creating the host-side adapter.</span></span>  
  
-   <span data-ttu-id="a0074-111">ホストを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0074-111">Creating the host.</span></span>  
  
-   <span data-ttu-id="a0074-112">アドインを作成しています。</span><span class="sxs-lookup"><span data-stu-id="a0074-112">Creating the add-in.</span></span>  
  
-   <span data-ttu-id="a0074-113">パイプラインを展開します。</span><span class="sxs-lookup"><span data-stu-id="a0074-113">Deploying the pipeline.</span></span>  
  
-   <span data-ttu-id="a0074-114">ホスト アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="a0074-114">Running the host application.</span></span>  
  
 <span data-ttu-id="a0074-115">このパイプラインは、シリアル化できる型のみを渡します (<xref:System.Double>と<xref:System.String>)、ホストとアドインの間です。</span><span class="sxs-lookup"><span data-stu-id="a0074-115">This pipeline passes only serializable types (<xref:System.Double> and <xref:System.String>), between the host and the add-in.</span></span> <span data-ttu-id="a0074-116">例については複雑なデータ型のコレクションを渡す方法を示す、次を参照してください。[チュートリアル: コレクションのホスト間で渡すとアドイン](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5)です。</span><span class="sxs-lookup"><span data-stu-id="a0074-116">For an example that shows how to pass collections of complex data types, see [Walkthrough: Passing Collections Between Hosts and Add-Ins](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5).</span></span>  
  
 <span data-ttu-id="a0074-117">このパイプラインのコントラクトは、次の 4 つの算術演算のオブジェクト モデルを定義します。 追加、減算、乗算、および除算します。</span><span class="sxs-lookup"><span data-stu-id="a0074-117">The contract for this pipeline defines an object model of four arithmetic operations: add, subtract, multiply, and divide.</span></span> <span data-ttu-id="a0074-118">ホストから、アドイン + 2 + 2 などを計算する数式れ、アドインのホストに結果を返します。</span><span class="sxs-lookup"><span data-stu-id="a0074-118">The host provides the add-in with an equation to calculate, such as 2 + 2, and the add-in returns the result to the host.</span></span>  
  
 <span data-ttu-id="a0074-119">バージョン 2 の電卓を追加より高度を提供し、バージョン管理を示します。</span><span class="sxs-lookup"><span data-stu-id="a0074-119">Version 2 of the calculator add-in provides more calculating possibilities and demonstrates versioning.</span></span> <span data-ttu-id="a0074-120">説明されている、[チュートリアル: 変更のホストとしての旧バージョンとの互換性を有効にすると](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848)です。</span><span class="sxs-lookup"><span data-stu-id="a0074-120">It is described in [Walkthrough: Enabling Backward Compatibility as Your Host Changes](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a0074-121">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a0074-121">Prerequisites</span></span>  
 <span data-ttu-id="a0074-122">このチュートリアルを完了するための要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a0074-122">You need the following to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]<span data-ttu-id="a0074-123">。</span><span class="sxs-lookup"><span data-stu-id="a0074-123">.</span></span>  
  
## <a name="creating-a-visual-studio-solution"></a><span data-ttu-id="a0074-124">Visual Studio ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0074-124">Creating a Visual Studio Solution</span></span>  
 <span data-ttu-id="a0074-125">ソリューションを使用して[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]パイプライン セグメントのプロジェクトを格納します。</span><span class="sxs-lookup"><span data-stu-id="a0074-125">Use a solution in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] to contain the projects of your pipeline segments.</span></span>  
  
#### <a name="to-create-the-pipeline-solution"></a><span data-ttu-id="a0074-126">パイプライン ソリューションを作成するには</span><span class="sxs-lookup"><span data-stu-id="a0074-126">To create the pipeline solution</span></span>  
  
1.  <span data-ttu-id="a0074-127">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]、という名前の新しいプロジェクトを作成する`Calc1Contract`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-127">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], create a new project named `Calc1Contract`.</span></span> <span data-ttu-id="a0074-128">基になる、**クラス ライブラリ**テンプレート。</span><span class="sxs-lookup"><span data-stu-id="a0074-128">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="a0074-129">ソリューションの名前を付けます`CalculatorV1`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-129">Name the solution `CalculatorV1`.</span></span>  
  
## <a name="creating-the-pipeline-directory-structure"></a><span data-ttu-id="a0074-130">パイプライン ディレクトリ構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="a0074-130">Creating the Pipeline Directory Structure</span></span>  
 <span data-ttu-id="a0074-131">アドイン モデルでは、指定したディレクトリ構造に配置するのにパイプライン セグメントのアセンブリが必要です。</span><span class="sxs-lookup"><span data-stu-id="a0074-131">The add-in model requires the pipeline segment assemblies to be placed in a specified directory structure.</span></span> <span data-ttu-id="a0074-132">パイプラインの構造に関する詳細については、次を参照してください。[パイプラインの開発要件](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5)です。</span><span class="sxs-lookup"><span data-stu-id="a0074-132">For more information about the pipeline structure, see [Pipeline Development Requirements](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
#### <a name="to-create-the-pipeline-directory-structure"></a><span data-ttu-id="a0074-133">パイプライン ディレクトリ構造を作成するには</span><span class="sxs-lookup"><span data-stu-id="a0074-133">To create the pipeline directory structure</span></span>  
  
1.  <span data-ttu-id="a0074-134">コンピューターの任意の場所、アプリケーションのフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0074-134">Create an application folder anywhere on your computer.</span></span>  
  
2.  <span data-ttu-id="a0074-135">そのフォルダー内には、次のような構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="a0074-135">In that folder, create the following structure:</span></span>  
  
    ```  
    Pipeline  
      AddIns  
        CalcV1  
        CalcV2  
      AddInSideAdapters  
      AddInViews  
      Contracts  
      HostSideAdapters  
    ```  
  
     <span data-ttu-id="a0074-136">アプリケーション フォルダーにパイプラインのフォルダー構造を配置する必要はありません。関数は、のみ、便宜上、ここで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a0074-136">It is not necessary to put the pipeline folder structure in your application folder; it is done here only for convenience.</span></span> <span data-ttu-id="a0074-137">該当の手順では、このチュートリアルは、パイプラインのフォルダー構造が別の場所である場合は、コードを変更する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a0074-137">At the appropriate step, the walkthrough explains how to change the code if the pipeline folder structure is in a different location.</span></span> <span data-ttu-id="a0074-138">パイプライン ディレクトリの必要条件の説明を参照して[パイプラインの開発要件](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5)です。</span><span class="sxs-lookup"><span data-stu-id="a0074-138">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0074-139">`CalcV2`フォルダーは、このチュートリアルでは使用されません。 のプレース ホルダーは[チュートリアル: 変更のホストとしての旧バージョンとの互換性を有効にすると](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848)です。</span><span class="sxs-lookup"><span data-stu-id="a0074-139">The `CalcV2` folder is not used in this walkthrough; it is a placeholder for [Walkthrough: Enabling Backward Compatibility as Your Host Changes](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="creating-the-contract-and-views"></a><span data-ttu-id="a0074-140">コントラクトとビューの作成</span><span class="sxs-lookup"><span data-stu-id="a0074-140">Creating the Contract and Views</span></span>  
 <span data-ttu-id="a0074-141">このパイプラインのコントラクト セグメントの定義、`ICalc1Contract`を 4 つのメソッドを定義するインターフェイス: `add`、 `subtract`、 `multiply`、および`divide`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-141">The contract segment for this pipeline defines the `ICalc1Contract` interface, which defines four methods: `add`, `subtract`, `multiply`, and `divide`.</span></span>  
  
#### <a name="to-create-the-contract"></a><span data-ttu-id="a0074-142">コントラクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="a0074-142">To create the contract</span></span>  
  
1.  <span data-ttu-id="a0074-143">という名前の Visual Studio ソリューションで`CalculatorV1`を開き、`Calc1Contract`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="a0074-143">In the Visual Studio solution named `CalculatorV1`, open the `Calc1Contract` project.</span></span>  
  
2.  <span data-ttu-id="a0074-144">**ソリューション エクスプ ローラー**、以下のアセンブリへの参照を追加、`Calc1Contract`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="a0074-144">In **Solution Explorer**, add references to the following assemblies to the `Calc1Contract` project:</span></span>  
  
     <span data-ttu-id="a0074-145">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="a0074-145">System.AddIn.Contract.dll</span></span>  
  
     <span data-ttu-id="a0074-146">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="a0074-146">System.AddIn.dll</span></span>  
  
3.  <span data-ttu-id="a0074-147">**ソリューション エクスプ ローラー**、新規に追加される既定のクラスを除外する**クラス ライブラリ**プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="a0074-147">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects.</span></span>  
  
4.  <span data-ttu-id="a0074-148">**ソリューション エクスプ ローラー**、新しい項目をプロジェクトに追加を使用して、**インターフェイス**テンプレート。</span><span class="sxs-lookup"><span data-stu-id="a0074-148">In **Solution Explorer**, add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="a0074-149">**新しい項目の追加** ダイアログ ボックスに、名前、インターフェイス`ICalc1Contract`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-149">In the **Add New Item** dialog box, name the interface `ICalc1Contract`.</span></span>  
  
5.  <span data-ttu-id="a0074-150">インターフェイス ファイルで名前空間参照を追加<xref:System.AddIn.Contract>と<xref:System.AddIn.Pipeline>です。</span><span class="sxs-lookup"><span data-stu-id="a0074-150">In the interface file, add namespace references to <xref:System.AddIn.Contract> and <xref:System.AddIn.Pipeline>.</span></span>  
  
6.  <span data-ttu-id="a0074-151">このコントラクト セグメントを完了するのにには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0074-151">Use the following code to complete this contract segment.</span></span> <span data-ttu-id="a0074-152">このインターフェイスが必要です、<xref:System.AddIn.Pipeline.AddInContractAttribute>属性。</span><span class="sxs-lookup"><span data-stu-id="a0074-152">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInContractAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  <span data-ttu-id="a0074-153">必要に応じて、Visual Studio ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="a0074-153">Optionally, build the Visual Studio solution.</span></span> <span data-ttu-id="a0074-154">最後の手順が各手順は、各プロジェクトがあることを確認した後にビルドし、解決されるまでは、ソリューションを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="a0074-154">The solution cannot be run until the final procedure, but building it after each procedure ensures that each project is correct.</span></span>  
  
 <span data-ttu-id="a0074-155">追加のビューと、ホスト ビューのためアドインをアドインの最初のバージョンで特に通常、同じコードがある、同時に、ビューを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="a0074-155">Because the add-in view and the host view of the add-in usually have the same code, especially in the first version of an add-in, you can easily create the views at the same time.</span></span> <span data-ttu-id="a0074-156">1 つだけの要素が異なる: 追加のビューが必要です、<xref:System.AddIn.Pipeline.AddInBaseAttribute>属性がアドインのホスト ビューでは、属性は必要ありませんが、します。</span><span class="sxs-lookup"><span data-stu-id="a0074-156">They differ by only one factor: the add-in view requires the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute, while the host view of the add-in does not require any attributes.</span></span>  
  
#### <a name="to-create-the-add-in-view"></a><span data-ttu-id="a0074-157">追加のビューを作成するには</span><span class="sxs-lookup"><span data-stu-id="a0074-157">To create the add-in view</span></span>  
  
1.  <span data-ttu-id="a0074-158">という名前の新しいプロジェクトを追加`Calc1AddInView`を`CalculatorV1`ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="a0074-158">Add a new project named `Calc1AddInView` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="a0074-159">基になる、**クラス ライブラリ**テンプレート。</span><span class="sxs-lookup"><span data-stu-id="a0074-159">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="a0074-160">**ソリューション エクスプ ローラー**に System.AddIn.dll への参照を追加、`Calc1AddInView`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="a0074-160">In **Solution Explorer**, add a reference to System.AddIn.dll to the `Calc1AddInView` project.</span></span>  
  
3.  <span data-ttu-id="a0074-161">**ソリューション エクスプ ローラー**、新規に追加される既定のクラスを除外する**クラス ライブラリ**プロジェクト、およびプロジェクトへの新しい項目の追加を使用して、**インターフェイス**テンプレート。</span><span class="sxs-lookup"><span data-stu-id="a0074-161">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="a0074-162">**新しい項目の追加** ダイアログ ボックスに、名前、インターフェイス`ICalculator`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-162">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
4.  <span data-ttu-id="a0074-163">インターフェイス ファイルに名前空間参照を追加<xref:System.AddIn.Pipeline>です。</span><span class="sxs-lookup"><span data-stu-id="a0074-163">In the interface file, add a namespace reference to <xref:System.AddIn.Pipeline>.</span></span>  
  
5.  <span data-ttu-id="a0074-164">このアドインでは、ビューを完了するのにには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0074-164">Use the following code to complete this add-in view.</span></span> <span data-ttu-id="a0074-165">このインターフェイスが必要です、<xref:System.AddIn.Pipeline.AddInBaseAttribute>属性。</span><span class="sxs-lookup"><span data-stu-id="a0074-165">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  <span data-ttu-id="a0074-166">必要に応じて、Visual Studio ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="a0074-166">Optionally, build the Visual Studio solution.</span></span>  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a><span data-ttu-id="a0074-167">アドインのホスト ビューを作成するには</span><span class="sxs-lookup"><span data-stu-id="a0074-167">To create the host view of the add-in</span></span>  
  
1.  <span data-ttu-id="a0074-168">という名前の新しいプロジェクトを追加`Calc1HVA`を`CalculatorV1`ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="a0074-168">Add a new project named `Calc1HVA` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="a0074-169">基になる、**クラス ライブラリ**テンプレート。</span><span class="sxs-lookup"><span data-stu-id="a0074-169">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="a0074-170">**ソリューション エクスプ ローラー**、新規に追加される既定のクラスを除外する**クラス ライブラリ**プロジェクト、およびプロジェクトへの新しい項目の追加を使用して、**インターフェイス**テンプレート。</span><span class="sxs-lookup"><span data-stu-id="a0074-170">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="a0074-171">**新しい項目の追加** ダイアログ ボックスに、名前、インターフェイス`ICalculator`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-171">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
3.  <span data-ttu-id="a0074-172">インターフェイス ファイルでは、アドインのホスト ビューを完了するのに、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0074-172">In the interface file, use the following code to complete the host view of the add-in.</span></span>  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  <span data-ttu-id="a0074-173">必要に応じて、Visual Studio ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="a0074-173">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in-side-adapter"></a><span data-ttu-id="a0074-174">追加側アダプターを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0074-174">Creating the Add-in-side Adapter</span></span>  
 <span data-ttu-id="a0074-175">この追加側アダプターは、1 つのビューからコントラクトのアダプターで構成されます。</span><span class="sxs-lookup"><span data-stu-id="a0074-175">This add-in-side adapter consists of one view-to-contract adapter.</span></span> <span data-ttu-id="a0074-176">このパイプライン セグメントは、コントラクトにアドインをビューから型を変換します。</span><span class="sxs-lookup"><span data-stu-id="a0074-176">This pipeline segment converts the types from the add-in view to the contract.</span></span>  
  
 <span data-ttu-id="a0074-177">このパイプラインでは、アドインによって、ホストにサービスを提供方向で、種類からアドインをホストにします。</span><span class="sxs-lookup"><span data-stu-id="a0074-177">In this pipeline, the add-in provides a service to the host, and the types flow from the add-in to the host.</span></span> <span data-ttu-id="a0074-178">アドインのホストからの種類がフローありません、ためにがありません側アドインでこのパイプラインのコントラクトのビューへのアダプターを含める。</span><span class="sxs-lookup"><span data-stu-id="a0074-178">Because no types flow from the host to the add-in, you do not have to include a contract-to-view adapter on the add-in side of this pipeline.</span></span>  
  
#### <a name="to-create-the-add-in-side-adapter"></a><span data-ttu-id="a0074-179">アドイン側アダプターを作成するには</span><span class="sxs-lookup"><span data-stu-id="a0074-179">To create the add-in-side adapter</span></span>  
  
1.  <span data-ttu-id="a0074-180">という名前の新しいプロジェクトを追加`Calc1AddInSideAdapter`を`CalculatorV1`ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="a0074-180">Add a new project named `Calc1AddInSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="a0074-181">基になる、**クラス ライブラリ**テンプレート。</span><span class="sxs-lookup"><span data-stu-id="a0074-181">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="a0074-182">**ソリューション エクスプ ローラー**、以下のアセンブリへの参照を追加、`Calc1AddInSideAdapter`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="a0074-182">In **Solution Explorer**, add references to the following assemblies to the `Calc1AddInSideAdapter` project:</span></span>  
  
     <span data-ttu-id="a0074-183">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="a0074-183">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="a0074-184">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="a0074-184">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="a0074-185">隣接するパイプライン セグメントのプロジェクトへのプロジェクト参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="a0074-185">Add project references to the projects for the adjacent pipeline segments:</span></span>  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  <span data-ttu-id="a0074-186">各プロジェクト参照を選択し、**プロパティ**設定**ローカル コピー**に**False**です。</span><span class="sxs-lookup"><span data-stu-id="a0074-186">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="a0074-187">Visual Basic を使用して、**参照**のタブ**プロジェクトのプロパティ**を設定する**ローカル コピー**に**False** 2 つのプロジェクト参照のです。</span><span class="sxs-lookup"><span data-stu-id="a0074-187">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="a0074-188">プロジェクトの既定のクラスの名前を変更`CalculatorViewToContractAddInSideAdapter`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-188">Rename the project's default class `CalculatorViewToContractAddInSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="a0074-189">クラス ファイルで名前空間参照を追加<xref:System.AddIn.Pipeline>です。</span><span class="sxs-lookup"><span data-stu-id="a0074-189">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="a0074-190">クラス ファイルで、隣接するセグメントの名前空間参照を追加:`CalcAddInViews`と`CalculatorContracts`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-190">In the class file, add namespace references for the adjacent segments: `CalcAddInViews` and `CalculatorContracts`.</span></span> <span data-ttu-id="a0074-191">(この名前空間の参照は、Visual basic で`Calc1AddInView.CalcAddInViews`と`Calc1Contract.CalculatorContracts`Visual Basic プロジェクトで既定の名前空間を無効にしている場合を除き、します)。</span><span class="sxs-lookup"><span data-stu-id="a0074-191">(In Visual Basic, these namespace references are `Calc1AddInView.CalcAddInViews` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="a0074-192">適用、<xref:System.AddIn.Pipeline.AddInAdapterAttribute>属性を`CalculatorViewToContractAddInSideAdapter`クラスに追加側アダプターとして識別します。</span><span class="sxs-lookup"><span data-stu-id="a0074-192">Apply the <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribute to the `CalculatorViewToContractAddInSideAdapter` class, to identify it as the add-in-side adapter.</span></span>  
  
9. <span data-ttu-id="a0074-193">ように、`CalculatorViewToContractAddInSideAdapter`クラスは継承<xref:System.AddIn.Pipeline.ContractBase>の既定の実装を提供する、<xref:System.AddIn.Contract.IContract>インターフェイス、および、パイプラインのコントラクト インターフェイスを実装して`ICalc1Contract`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-193">Make the `CalculatorViewToContractAddInSideAdapter` class inherit <xref:System.AddIn.Pipeline.ContractBase>, which provides a default implementation of the <xref:System.AddIn.Contract.IContract> interface, and implement the contract interface for the pipeline, `ICalc1Contract`.</span></span>  
  
10. <span data-ttu-id="a0074-194">受け取るパブリック コンス トラクターを追加、`ICalculator`プライベート フィールドでキャッシュ、および基本クラス コンス トラクターを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a0074-194">Add a public constructor that accepts an `ICalculator`, caches it in a private field, and calls the base class constructor.</span></span>  
  
11. <span data-ttu-id="a0074-195">メンバーを実装する`ICalc1Contract`の対応するメンバーを呼び出すだけ、`ICalculator`インスタンスをコンス トラクターに渡され、結果を返します。</span><span class="sxs-lookup"><span data-stu-id="a0074-195">To implement the members of `ICalc1Contract`, simply call the corresponding members of the `ICalculator` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="a0074-196">これは、ビューを適合させます (`ICalculator`) をコントラクト (`ICalc1Contract`)。</span><span class="sxs-lookup"><span data-stu-id="a0074-196">This adapts the view (`ICalculator`) to the contract (`ICalc1Contract`).</span></span>  
  
     <span data-ttu-id="a0074-197">次のコードには、完了した追加側アダプターが示されています。</span><span class="sxs-lookup"><span data-stu-id="a0074-197">The following code shows the completed add-in-side adapter.</span></span>  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. <span data-ttu-id="a0074-198">必要に応じて、Visual Studio ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="a0074-198">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host-side-adapter"></a><span data-ttu-id="a0074-199">ホスト側のアダプターを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0074-199">Creating the Host-side Adapter</span></span>  
 <span data-ttu-id="a0074-200">このホスト側のアダプターは、1 つのコントラクトのビューへのアダプターで構成されます。</span><span class="sxs-lookup"><span data-stu-id="a0074-200">This host-side adapter consists of one contract-to-view adapter.</span></span> <span data-ttu-id="a0074-201">このセグメントは、アドインのホスト ビューにコントラクトを適合させます。</span><span class="sxs-lookup"><span data-stu-id="a0074-201">This segment adapts the contract to the host view of the add-in.</span></span>  
  
 <span data-ttu-id="a0074-202">このパイプラインのアドインのホストと型フローにサービスをアドインをホストから提供します。</span><span class="sxs-lookup"><span data-stu-id="a0074-202">In this pipeline, the add-in provides a service to the host and the types flow from the add-in to the host.</span></span> <span data-ttu-id="a0074-203">型が、アドインをホストからフローないため、ビューからコントラクトのアダプターが含まするはありません。</span><span class="sxs-lookup"><span data-stu-id="a0074-203">Because no types flow from the host to the add-in, you do not have to include a view-to-contract adapter.</span></span>  
  
 <span data-ttu-id="a0074-204">有効期間の管理を実装するには、使用、<xref:System.AddIn.Pipeline.ContractHandle>コントラクトに有効期間トークンをアタッチするオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a0074-204">To implement lifetime management, use a <xref:System.AddIn.Pipeline.ContractHandle> object to attach a lifetime token to the contract.</span></span> <span data-ttu-id="a0074-205">有効期間の管理が機能するために、このハンドルへの参照を維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0074-205">You must keep a reference to this handle in order for lifetime management to work.</span></span> <span data-ttu-id="a0074-206">トークンが適用されると、追加のプログラミングは必要ありませんが使用されていないガベージ コレクションで利用できるようにすると、アドイン システムがオブジェクトの破棄できます。</span><span class="sxs-lookup"><span data-stu-id="a0074-206">After the token is applied, no additional programming is required because the add-in system can dispose of objects when they are no longer being used and make them available for garbage collection.</span></span> <span data-ttu-id="a0074-207">詳細については、「 [有効期間管理](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0074-207">For more information, see [Lifetime Management](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
#### <a name="to-create-the-host-side-adapter"></a><span data-ttu-id="a0074-208">ホスト側のアダプターを作成するには</span><span class="sxs-lookup"><span data-stu-id="a0074-208">To create the host-side adapter</span></span>  
  
1.  <span data-ttu-id="a0074-209">という名前の新しいプロジェクトを追加`Calc1HostSideAdapter`を`CalculatorV1`ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="a0074-209">Add a new project named `Calc1HostSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="a0074-210">基になる、**クラス ライブラリ**テンプレート。</span><span class="sxs-lookup"><span data-stu-id="a0074-210">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="a0074-211">**ソリューション エクスプ ローラー**、以下のアセンブリへの参照を追加、`Calc1HostSideAdapter`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="a0074-211">In **Solution Explorer**, add references to the following assemblies to the `Calc1HostSideAdapter` project:</span></span>  
  
     <span data-ttu-id="a0074-212">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="a0074-212">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="a0074-213">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="a0074-213">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="a0074-214">隣接するセグメントのプロジェクトへのプロジェクト参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="a0074-214">Add project references to the projects for the adjacent segments:</span></span>  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  <span data-ttu-id="a0074-215">各プロジェクト参照を選択し、**プロパティ**設定**ローカル コピー**に**False**です。</span><span class="sxs-lookup"><span data-stu-id="a0074-215">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="a0074-216">Visual Basic を使用して、**参照**のタブ**プロジェクトのプロパティ**を設定する**ローカル コピー**に**False** 2 つのプロジェクト参照のです。</span><span class="sxs-lookup"><span data-stu-id="a0074-216">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="a0074-217">プロジェクトの既定のクラスの名前を変更`CalculatorContractToViewHostSideAdapter`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-217">Rename the project's default class `CalculatorContractToViewHostSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="a0074-218">クラス ファイルで名前空間参照を追加<xref:System.AddIn.Pipeline>です。</span><span class="sxs-lookup"><span data-stu-id="a0074-218">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="a0074-219">クラス ファイルで、隣接するセグメントの名前空間参照を追加:`CalcHVAs`と`CalculatorContracts`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-219">In the class file, add namespace references for the adjacent segments: `CalcHVAs` and `CalculatorContracts`.</span></span> <span data-ttu-id="a0074-220">(この名前空間の参照は、Visual basic で`Calc1HVA.CalcHVAs`と`Calc1Contract.CalculatorContracts`Visual Basic プロジェクトで既定の名前空間を無効にしている場合を除き、します)。</span><span class="sxs-lookup"><span data-stu-id="a0074-220">(In Visual Basic, these namespace references are `Calc1HVA.CalcHVAs` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="a0074-221">適用、<xref:System.AddIn.Pipeline.HostAdapterAttribute>属性を`CalculatorContractToViewHostSideAdapter`クラス、ホスト側のアダプター セグメントとして識別します。</span><span class="sxs-lookup"><span data-stu-id="a0074-221">Apply the <xref:System.AddIn.Pipeline.HostAdapterAttribute> attribute to the `CalculatorContractToViewHostSideAdapter` class, to identify it as the host-side adapter segment.</span></span>  
  
9. <span data-ttu-id="a0074-222">ように、`CalculatorContractToViewHostSideAdapter`クラスは、アドインのホスト ビューを表すインターフェイスを実装して: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` Visual Basic で)。</span><span class="sxs-lookup"><span data-stu-id="a0074-222">Make the `CalculatorContractToViewHostSideAdapter` class implement the interface that represents the host view of the add-in: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` in Visual Basic).</span></span>  
  
10. <span data-ttu-id="a0074-223">パイプラインのコントラクトの型を受け取るパブリック コンス トラクターを追加`ICalc1Contract`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-223">Add a public constructor that accepts the pipeline contract type, `ICalc1Contract`.</span></span> <span data-ttu-id="a0074-224">コンス トラクターは、コントラクトへの参照をキャッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0074-224">The constructor must cache the reference to the contract.</span></span> <span data-ttu-id="a0074-225">作成し、新しいキャッシュ<xref:System.AddIn.Pipeline.ContractHandle>アドインの有効期間を管理する、コントラクトです。</span><span class="sxs-lookup"><span data-stu-id="a0074-225">It must also create and cache a new <xref:System.AddIn.Pipeline.ContractHandle> for the contract, to manage the lifetime of the add-in.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a0074-226"><xref:System.AddIn.Pipeline.ContractHandle>有効期間の管理に不可欠です。</span><span class="sxs-lookup"><span data-stu-id="a0074-226">The <xref:System.AddIn.Pipeline.ContractHandle> is critical to lifetime management.</span></span> <span data-ttu-id="a0074-227">参照を保持に失敗した場合、<xref:System.AddIn.Pipeline.ContractHandle>オブジェクト、ガベージ コレクションによって回収がおよび、プログラムで想定されていないときに、パイプラインはシャット ダウンします。</span><span class="sxs-lookup"><span data-stu-id="a0074-227">If you fail to keep a reference to the <xref:System.AddIn.Pipeline.ContractHandle> object, garbage collection will reclaim it, and the pipeline will shut down when your program does not expect it.</span></span> <span data-ttu-id="a0074-228">これがなど、診断が困難なエラーにつながる<xref:System.AppDomainUnloadedException>です。</span><span class="sxs-lookup"><span data-stu-id="a0074-228">This can lead to errors that are difficult to diagnose, such as <xref:System.AppDomainUnloadedException>.</span></span> <span data-ttu-id="a0074-229">シャット ダウンは、パイプラインの有効期間のステージは通常は、この条件は、エラーを検出するために、有効期間管理コードの方法はありません。</span><span class="sxs-lookup"><span data-stu-id="a0074-229">Shutdown is a normal stage in the life of a pipeline, so there is no way for the lifetime management code to detect that this condition is an error.</span></span>  
  
11. <span data-ttu-id="a0074-230">メンバーを実装する`ICalculator`の対応するメンバーを呼び出すだけ、`ICalc1Contract`インスタンスをコンス トラクターに渡され、結果を返します。</span><span class="sxs-lookup"><span data-stu-id="a0074-230">To implement the members of `ICalculator`, simply call the corresponding members of the `ICalc1Contract` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="a0074-231">これは、コントラクトを適合させます (`ICalc1Contract`) ビューに (`ICalculator`)。</span><span class="sxs-lookup"><span data-stu-id="a0074-231">This adapts the contract (`ICalc1Contract`) to the view (`ICalculator`).</span></span>  
  
     <span data-ttu-id="a0074-232">次のコードには、完了のホスト側アダプターが示されています。</span><span class="sxs-lookup"><span data-stu-id="a0074-232">The following code shows the completed host-side adapter.</span></span>  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. <span data-ttu-id="a0074-233">必要に応じて、Visual Studio ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="a0074-233">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host"></a><span data-ttu-id="a0074-234">ホストの作成</span><span class="sxs-lookup"><span data-stu-id="a0074-234">Creating the Host</span></span>  
 <span data-ttu-id="a0074-235">ホスト アプリケーションは、アドインのホスト ビュー アドインと対話します。</span><span class="sxs-lookup"><span data-stu-id="a0074-235">A host application interacts with the add-in through the host view of the add-in.</span></span> <span data-ttu-id="a0074-236">アドインでは、検出とアクティブ化によって提供されるメソッドを使用して、<xref:System.AddIn.Hosting.AddInStore>と<xref:System.AddIn.Hosting.AddInToken>クラスを次を行うには。</span><span class="sxs-lookup"><span data-stu-id="a0074-236">It uses add-in discovery and activation methods provided by the <xref:System.AddIn.Hosting.AddInStore> and <xref:System.AddIn.Hosting.AddInToken> classes to do the following:</span></span>  
  
-   <span data-ttu-id="a0074-237">パイプラインとアドインでは、情報のキャッシュを更新します。</span><span class="sxs-lookup"><span data-stu-id="a0074-237">Update the cache of pipeline and add-in information.</span></span>  
  
-   <span data-ttu-id="a0074-238">ホスト ビューの種類のアドインの検索`ICalculator`、指定したパイプラインのルート ディレクトリの下。</span><span class="sxs-lookup"><span data-stu-id="a0074-238">Find add-ins of the host view type, `ICalculator`, under the specified pipeline root directory.</span></span>  
  
-   <span data-ttu-id="a0074-239">アドインを使用する指定を求めるボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="a0074-239">Prompt the user to specify which add-in to use.</span></span>  
  
-   <span data-ttu-id="a0074-240">選択したアドインの指定したセキュリティの信頼レベルで新しいアプリケーション ドメインで有効にします。</span><span class="sxs-lookup"><span data-stu-id="a0074-240">Activate the selected add-in in a new application domain with a specified security trust level.</span></span>  
  
-   <span data-ttu-id="a0074-241">カスタムの実行`RunCalculator`メソッドで、アドインのホスト ビューで指定されたアドインのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a0074-241">Run the custom `RunCalculator` method, which calls the add-in's methods as specified by the host view of the add-in.</span></span>  
  
#### <a name="to-create-the-host"></a><span data-ttu-id="a0074-242">ホストを作成するには</span><span class="sxs-lookup"><span data-stu-id="a0074-242">To create the host</span></span>  
  
1.  <span data-ttu-id="a0074-243">という名前の新しいプロジェクトを追加`Calc1Host`を`CalculatorV1`ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="a0074-243">Add a new project named `Calc1Host` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="a0074-244">基になる、**コンソール アプリケーション**テンプレート。</span><span class="sxs-lookup"><span data-stu-id="a0074-244">Base it on the **Console Application** template.</span></span>  
  
2.  <span data-ttu-id="a0074-245">**ソリューション エクスプ ローラー**、System.AddIn.dll アセンブリへの参照を追加、`Calc1Host`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="a0074-245">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the `Calc1Host` project.</span></span>  
  
3.  <span data-ttu-id="a0074-246">プロジェクト参照を追加、`Calc1HVA`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="a0074-246">Add a project reference to the `Calc1HVA` project.</span></span> <span data-ttu-id="a0074-247">プロジェクト参照を選択し、**プロパティ**設定**ローカル コピー**に**False**です。</span><span class="sxs-lookup"><span data-stu-id="a0074-247">Select the project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="a0074-248">Visual Basic を使用して、**参照**のタブ**プロジェクト プロパティ**を設定する**ローカル コピー**に**False**です。</span><span class="sxs-lookup"><span data-stu-id="a0074-248">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False**.</span></span>  
  
4.  <span data-ttu-id="a0074-249">クラス ファイル (Visual Basic でのモジュール) の名前を変更`MathHost1`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-249">Rename the class file (module in Visual Basic) `MathHost1`.</span></span>  
  
5.  <span data-ttu-id="a0074-250">Visual Basic を使用して、**アプリケーション**のタブ、**プロジェクト プロパティ**を設定する ダイアログ ボックス**スタートアップ オブジェクト**に**Sub Main**です。</span><span class="sxs-lookup"><span data-stu-id="a0074-250">In Visual Basic, use the **Application** tab of the **Project Properties** dialog box to set **Startup object** to **Sub Main**.</span></span>  
  
6.  <span data-ttu-id="a0074-251">クラスまたはモジュールのファイルに名前空間参照を追加<xref:System.AddIn.Hosting>です。</span><span class="sxs-lookup"><span data-stu-id="a0074-251">In the class or module file, add a namespace reference to <xref:System.AddIn.Hosting>.</span></span>  
  
7.  <span data-ttu-id="a0074-252">クラスまたはモジュールのファイルで、アドインのホスト ビューの名前空間参照を追加:`CalcHVAs`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-252">In the class or module file, add a namespace reference for the host view of the add-in: `CalcHVAs`.</span></span> <span data-ttu-id="a0074-253">(Visual Basic の場合は、この名前空間の参照は`Calc1HVA.CalcHVAs`Visual Basic プロジェクトで既定の名前空間を無効にしている場合を除き、します)。</span><span class="sxs-lookup"><span data-stu-id="a0074-253">(In Visual Basic, this namespace reference is `Calc1HVA.CalcHVAs`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="a0074-254">**ソリューション エクスプ ローラー**、ソリューションを選択してから、**プロジェクト**メニューを**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="a0074-254">In **Solution Explorer**, select the solution and from the **Project** menu choose **Properties**.</span></span> <span data-ttu-id="a0074-255">**ソリューション プロパティ ページ**ダイアログ ボックスで、設定、**シングル スタートアップ プロジェクト**をこのホスト アプリケーション プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="a0074-255">In the **Solution Property Pages** dialog box, set the **Single Startup Project** to be this host application project.</span></span>  
  
9. <span data-ttu-id="a0074-256">クラスまたはモジュールのファイルで使用して、<xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType>キャッシュを更新するメソッド。</span><span class="sxs-lookup"><span data-stu-id="a0074-256">In the class or module file, use the <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> method to update the cache.</span></span> <span data-ttu-id="a0074-257">使用して、 <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> 、トークンのコレクションを取得および使用するメソッド、<xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType>アドインをアクティブ化するメソッド。</span><span class="sxs-lookup"><span data-stu-id="a0074-257">Use the <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> method to get a collection of tokens, and use the <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> method to activate an add-in.</span></span>  
  
     <span data-ttu-id="a0074-258">次のコードでは、完全なホスト アプリケーションを示します。</span><span class="sxs-lookup"><span data-stu-id="a0074-258">The following code shows the completed host application.</span></span>  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="a0074-259">このコードでは、パイプラインのフォルダー構造が、アプリケーションのフォルダーにあることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="a0074-259">This code assumes that the pipeline folder structure is located in the application folder.</span></span> <span data-ttu-id="a0074-260">他の場所で配置する場合を設定するコードの行を変更、`addInRoot`変数、変数が、パイプライン ディレクトリ構造へのパスが含まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="a0074-260">If you located it elsewhere, change the line of code that sets the `addInRoot` variable, so that the variable contains the path to your pipeline directory structure.</span></span>  
  
     <span data-ttu-id="a0074-261">コードを使用して、`ChooseCalculator`メソッド トークンを一覧表示して、アドインを選択するユーザー入力を求めます。</span><span class="sxs-lookup"><span data-stu-id="a0074-261">The code uses a `ChooseCalculator` method to list the tokens and to prompt the user to choose an add-in.</span></span> <span data-ttu-id="a0074-262">`RunCalculator`メソッドは、単純な数式を求めるを使用して式を解析して、`Parser`クラス、および、アドインによって返される結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a0074-262">The `RunCalculator` method prompts the user for simple math expressions, parses the expressions using the `Parser` class, and displays the results returned by the add-in.</span></span>  
  
10. <span data-ttu-id="a0074-263">必要に応じて、Visual Studio ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="a0074-263">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in"></a><span data-ttu-id="a0074-264">アドインを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0074-264">Creating the Add-In</span></span>  
 <span data-ttu-id="a0074-265">アドインでは、追加のビューで指定されたメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="a0074-265">An add-in implements the methods specified by the add-in view.</span></span> <span data-ttu-id="a0074-266">このアドインを実装する、 `Add`、 `Subtract`、 `Multiply`、および`Divide`操作と、ホストに、結果を返します。</span><span class="sxs-lookup"><span data-stu-id="a0074-266">This add-in implements the `Add`, `Subtract`, `Multiply`, and `Divide` operations and returns the results to the host.</span></span>  
  
#### <a name="to-create-the-add-in"></a><span data-ttu-id="a0074-267">アドインを作成するには</span><span class="sxs-lookup"><span data-stu-id="a0074-267">To create the add-in</span></span>  
  
1.  <span data-ttu-id="a0074-268">という名前の新しいプロジェクトを追加`AddInCalcV1`を`CalculatorV1`ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="a0074-268">Add a new project named `AddInCalcV1` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="a0074-269">基になる、**クラス ライブラリ**テンプレート。</span><span class="sxs-lookup"><span data-stu-id="a0074-269">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="a0074-270">**ソリューション エクスプ ローラー**、System.AddIn.dll アセンブリへの参照をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="a0074-270">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the project.</span></span>  
  
3.  <span data-ttu-id="a0074-271">プロジェクト参照を追加、`Calc1AddInView`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="a0074-271">Add a project reference to the `Calc1AddInView` project.</span></span> <span data-ttu-id="a0074-272">プロジェクト参照を選択し、**プロパティ**設定、**ローカル コピー**に**False**です。</span><span class="sxs-lookup"><span data-stu-id="a0074-272">Select the project reference, and in **Properties**, set **Copy Local** to **False**.</span></span> <span data-ttu-id="a0074-273">Visual Basic を使用して、**参照**のタブ**プロジェクト プロパティ**を設定する**ローカル コピー**に**False**プロジェクト参照のです。</span><span class="sxs-lookup"><span data-stu-id="a0074-273">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the project reference.</span></span>  
  
4.  <span data-ttu-id="a0074-274">クラスの名前を変更`AddInCalcV1`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-274">Rename the class `AddInCalcV1`.</span></span>  
  
5.  <span data-ttu-id="a0074-275">クラス ファイルに名前空間参照を追加<xref:System.AddIn>および追加のビュー セグメント: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` Visual Basic で)。</span><span class="sxs-lookup"><span data-stu-id="a0074-275">In the class file, add a namespace reference to <xref:System.AddIn> and the add-in view segment: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` in Visual Basic).</span></span>  
  
6.  <span data-ttu-id="a0074-276">適用、<xref:System.AddIn.AddInAttribute>属性を`AddInCalcV1`クラスに、アドインとしてクラスを識別します。</span><span class="sxs-lookup"><span data-stu-id="a0074-276">Apply the <xref:System.AddIn.AddInAttribute> attribute to the `AddInCalcV1` class, to identify the class as an add-in.</span></span>  
  
7.  <span data-ttu-id="a0074-277">ように、`AddInCalcV1`クラスは、追加のビューを表すインターフェイスを実装して: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` Visual Basic で)。</span><span class="sxs-lookup"><span data-stu-id="a0074-277">Make the `AddInCalcV1` class implement the interface that represents the add-in view: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` in Visual Basic).</span></span>  
  
8.  <span data-ttu-id="a0074-278">メンバーを実装`ICalculator`適切な計算の結果を返すことによってです。</span><span class="sxs-lookup"><span data-stu-id="a0074-278">Implement the members of `ICalculator` by returning the results of the appropriate calculations.</span></span>  
  
     <span data-ttu-id="a0074-279">完了したアドインの次のコードを示しています。</span><span class="sxs-lookup"><span data-stu-id="a0074-279">The following code shows the completed add-in.</span></span>  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. <span data-ttu-id="a0074-280">必要に応じて、Visual Studio ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="a0074-280">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="deploying-the-pipeline"></a><span data-ttu-id="a0074-281">パイプラインを展開します。</span><span class="sxs-lookup"><span data-stu-id="a0074-281">Deploying the Pipeline</span></span>  
 <span data-ttu-id="a0074-282">ビルドし、必要なパイプライン ディレクトリ構造にアドイン セグメントを配置する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="a0074-282">You are now ready to build and deploy the add-in segments to the required pipeline directory structure.</span></span>  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a><span data-ttu-id="a0074-283">パイプライン、セグメントの配置</span><span class="sxs-lookup"><span data-stu-id="a0074-283">To deploy the segments to the pipeline</span></span>  
  
1.  <span data-ttu-id="a0074-284">ソリューション内の各プロジェクトを使用して、**ビルド**のタブ**プロジェクト プロパティ**(、**コンパイル**Visual Basic でのタブ) の値を設定する、**出力パス** (、**ビルド出力パス**Visual Basic で)。</span><span class="sxs-lookup"><span data-stu-id="a0074-284">For each project in the solution, use the **Build** tab of **Project Properties** (the **Compile** tab in Visual Basic) to set the value of the **Output path** (the **Build output path** in Visual Basic).</span></span> <span data-ttu-id="a0074-285">アプリケーションのフォルダーの名前を付けた場合`MyApp`、次のフォルダーには、プロジェクトでビルドなど。</span><span class="sxs-lookup"><span data-stu-id="a0074-285">If you named your application folder `MyApp`, for example, your projects would build into the following folders:</span></span>  
  
    |<span data-ttu-id="a0074-286">プロジェクト</span><span class="sxs-lookup"><span data-stu-id="a0074-286">Project</span></span>|<span data-ttu-id="a0074-287">パス</span><span class="sxs-lookup"><span data-stu-id="a0074-287">Path</span></span>|  
    |-------------|----------|  
    |<span data-ttu-id="a0074-288">AddInCalcV1</span><span class="sxs-lookup"><span data-stu-id="a0074-288">AddInCalcV1</span></span>|<span data-ttu-id="a0074-289">MyApp\Pipeline\AddIns\CalcV1</span><span class="sxs-lookup"><span data-stu-id="a0074-289">MyApp\Pipeline\AddIns\CalcV1</span></span>|  
    |<span data-ttu-id="a0074-290">Calc1AddInSideAdapter</span><span class="sxs-lookup"><span data-stu-id="a0074-290">Calc1AddInSideAdapter</span></span>|<span data-ttu-id="a0074-291">MyApp\Pipeline\AddInSideAdapters</span><span class="sxs-lookup"><span data-stu-id="a0074-291">MyApp\Pipeline\AddInSideAdapters</span></span>|  
    |<span data-ttu-id="a0074-292">Calc1AddInView</span><span class="sxs-lookup"><span data-stu-id="a0074-292">Calc1AddInView</span></span>|<span data-ttu-id="a0074-293">MyApp\Pipeline\AddInViews</span><span class="sxs-lookup"><span data-stu-id="a0074-293">MyApp\Pipeline\AddInViews</span></span>|  
    |<span data-ttu-id="a0074-294">Calc1Contract</span><span class="sxs-lookup"><span data-stu-id="a0074-294">Calc1Contract</span></span>|<span data-ttu-id="a0074-295">MyApp\Pipeline\Contracts</span><span class="sxs-lookup"><span data-stu-id="a0074-295">MyApp\Pipeline\Contracts</span></span>|  
    |<span data-ttu-id="a0074-296">Calc1Host</span><span class="sxs-lookup"><span data-stu-id="a0074-296">Calc1Host</span></span>|<span data-ttu-id="a0074-297">MyApp</span><span class="sxs-lookup"><span data-stu-id="a0074-297">MyApp</span></span>|  
    |<span data-ttu-id="a0074-298">Calc1HostSideAdapter</span><span class="sxs-lookup"><span data-stu-id="a0074-298">Calc1HostSideAdapter</span></span>|<span data-ttu-id="a0074-299">MyApp\Pipeline\HostSideAdapters</span><span class="sxs-lookup"><span data-stu-id="a0074-299">MyApp\Pipeline\HostSideAdapters</span></span>|  
    |<span data-ttu-id="a0074-300">Calc1HVA</span><span class="sxs-lookup"><span data-stu-id="a0074-300">Calc1HVA</span></span>|<span data-ttu-id="a0074-301">MyApp</span><span class="sxs-lookup"><span data-stu-id="a0074-301">MyApp</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="a0074-302">パイプライン フォルダー構造をアプリケーション フォルダー以外の場所に配置することを決定する場合は、それに応じて、テーブルのパスを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0074-302">If you decided to put your pipeline folder structure in a location other than your application folder, you must modify the paths shown in the table accordingly.</span></span> <span data-ttu-id="a0074-303">パイプライン ディレクトリの必要条件の説明を参照して[パイプラインの開発要件](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5)です。</span><span class="sxs-lookup"><span data-stu-id="a0074-303">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
2.  <span data-ttu-id="a0074-304">Visual Studio ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="a0074-304">Build the Visual Studio solution.</span></span>  
  
3.  <span data-ttu-id="a0074-305">アセンブリが適切なディレクトリにコピーされたことと、余分なアセンブリのコピーが正しくないフォルダーにインストールされていないことを確認するアプリケーションとパイプラインのディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a0074-305">Check the application and pipeline directories to ensure that the assemblies were copied to the correct directories and that no extra copies of assemblies were installed in the wrong folders.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0074-306">変更しなかった場合**ローカル コピー**に**False**の`Calc1AddInView`プロジェクトの参照、`AddInCalcV1`プロジェクト、ローダー コンテキストの問題により、アドインを配置されているからです。</span><span class="sxs-lookup"><span data-stu-id="a0074-306">If you did not change **Copy Local** to **False** for the `Calc1AddInView` project reference in the `AddInCalcV1` project, loader context problems will prevent the add-in from being located.</span></span>  
  
     <span data-ttu-id="a0074-307">パイプラインを展開する方法の詳細については、次を参照してください。[パイプラインの開発要件](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5)です。</span><span class="sxs-lookup"><span data-stu-id="a0074-307">For information about deploying to the pipeline, see [Pipeline Development Requirements](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
## <a name="running-the-host-application"></a><span data-ttu-id="a0074-308">ホスト アプリケーションの実行</span><span class="sxs-lookup"><span data-stu-id="a0074-308">Running the Host Application</span></span>  
 <span data-ttu-id="a0074-309">ホストを実行し、アドインを操作する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="a0074-309">You are now ready to run the host and interact with the add-in.</span></span>  
  
#### <a name="to-run-the-host-application"></a><span data-ttu-id="a0074-310">ホスト アプリケーションを実行するには</span><span class="sxs-lookup"><span data-stu-id="a0074-310">To run the host application</span></span>  
  
1.  <span data-ttu-id="a0074-311">コマンド プロンプトで アプリケーション ディレクトリに移動し、ホスト アプリケーションを実行`Calc1Host.exe`です。</span><span class="sxs-lookup"><span data-stu-id="a0074-311">At the command prompt, go to the application directory and run the host application, `Calc1Host.exe`.</span></span>  
  
2.  <span data-ttu-id="a0074-312">ホストは、すべて使用可能なアドインの型を検索し、アドインを選択するように求められます。</span><span class="sxs-lookup"><span data-stu-id="a0074-312">The host finds all available add-ins of its type and prompts you to select an add-in.</span></span> <span data-ttu-id="a0074-313">入力**1** for のみ使用できるアドインです。</span><span class="sxs-lookup"><span data-stu-id="a0074-313">Enter **1** for the only available add-in.</span></span>  
  
3.  <span data-ttu-id="a0074-314">など、電卓の式を入力**2 + 2**です。</span><span class="sxs-lookup"><span data-stu-id="a0074-314">Enter an equation for the calculator, such as **2 + 2**.</span></span> <span data-ttu-id="a0074-315">数字、および、演算子間のスペースを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0074-315">There must be spaces between the numbers and the operator.</span></span>  
  
4.  <span data-ttu-id="a0074-316">型**終了**キーを押すと、 **Enter**アプリケーションを閉じるにはキー。</span><span class="sxs-lookup"><span data-stu-id="a0074-316">Type **exit** and press the **Enter** key to close the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0074-317">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0074-317">See Also</span></span>  
 [<span data-ttu-id="a0074-318">チュートリアル: ホスト変更時の旧バージョンとの互換性を有効にします。</span><span class="sxs-lookup"><span data-stu-id="a0074-318">Walkthrough: Enabling Backward Compatibility as Your Host Changes</span></span>](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [<span data-ttu-id="a0074-319">チュートリアル: アドインとホスト間でのコレクションの受け渡し</span><span class="sxs-lookup"><span data-stu-id="a0074-319">Walkthrough: Passing Collections Between Hosts and Add-Ins</span></span>](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [<span data-ttu-id="a0074-320">パイプラインの開発要件</span><span class="sxs-lookup"><span data-stu-id="a0074-320">Pipeline Development Requirements</span></span>](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [<span data-ttu-id="a0074-321">コントラクト、ビュー、およびアダプター</span><span class="sxs-lookup"><span data-stu-id="a0074-321">Contracts, Views, and Adapters</span></span>](http://msdn.microsoft.com/en-us/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [<span data-ttu-id="a0074-322">Pipeline Development</span><span class="sxs-lookup"><span data-stu-id="a0074-322">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)
