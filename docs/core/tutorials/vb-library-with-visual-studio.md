---
title: "Visual Studio 2017 で Visual Basic と .NET Core を使用したクラス ライブラリの構築"
description: "Visual Studio 2017 を使用して Visual Basic で記述されたクラス ライブラリを構築する方法について"
keywords: ".NET Core、.NET Standard クラス ライブラリ、Visual Studio 2017、Visual Basic"
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-vb
dev_langs:
- vb
ms.workload:
- dotnetcore
ms.openlocfilehash: b8d87e3a97e2ffeb8e8712bfa5d178bb855f402d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="building-a-class-library-with-visual-basic-and-net-core-in-visual-studio-2017"></a><span data-ttu-id="48b39-104">Visual Studio 2017 で Visual Basic と .NET Core を使用したクラス ライブラリの構築</span><span class="sxs-lookup"><span data-stu-id="48b39-104">Building a class library with Visual Basic and .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="48b39-105">"*クラス ライブラリ*" は、アプリケーションから呼び出される型とメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="48b39-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="48b39-106">.NET Standard 2.0 をターゲットとするクラス ライブラリでは、お使いのライブラリを、そのバージョンの .NET Standard をサポートする任意の .NET 実装によって呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="48b39-106">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="48b39-107">クラス ライブラリを完了させたら、サードパーティ製のコンポーネントとして配布するかどうか、あるいは 1 つまたは複数のアプリケーションにバンドルされたコンポーネントとして含めるかどうかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="48b39-107">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="48b39-108">.NET Standard のバージョンとサポート対象のプラットフォームの一覧は、[「.NET Standard」](../../standard/net-standard.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48b39-108">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="48b39-109">このトピックでは、1 つの文字列処理メソッドを含む簡単なユーティリティ ライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="48b39-109">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="48b39-110">それを[拡張メソッド](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)として実装し、<xref:System.String> クラスのメンバーと同じように呼び出すことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="48b39-110">You'll implement it as an [extension method](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="48b39-111">クラス ライブラリのソリューションを作成する</span><span class="sxs-lookup"><span data-stu-id="48b39-111">Creating a class library solution</span></span>

<span data-ttu-id="48b39-112">最初に、クラス ライブラリ プロジェクトとその関連プロジェクトのソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="48b39-112">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="48b39-113">1 つの Visual Studio のソリューションは、1 つまたは複数のプロジェクトのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="48b39-113">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="48b39-114">このソリューションは次のように作成します。</span><span class="sxs-lookup"><span data-stu-id="48b39-114">To create the solution:</span></span>

1. <span data-ttu-id="48b39-115">Visual Studio のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選びます。</span><span class="sxs-lookup"><span data-stu-id="48b39-115">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="48b39-116">**[新しいプロジェクト]** ダイアログの **[その他のプロジェクトの種類]** ノードを展開し、**[Visual Studio ソリューション]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="48b39-116">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="48b39-117">ソリューションの名前を "ClassLibraryProjects" にして、**[OK]** ボタンを選びます。</span><span class="sxs-lookup"><span data-stu-id="48b39-117">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![[新しいプロジェクト] ダイアログ](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="48b39-119">クラス ライブラリ プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="48b39-119">Creating the class library project</span></span>

<span data-ttu-id="48b39-120">クラス ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="48b39-120">Create your class library project:</span></span>

1. <span data-ttu-id="48b39-121">**ソリューション エクスプローラー**で **ClassLibraryProjects** ソリューション ファイルを右クリックし、コンテキスト メニューから **[追加]** > **[新しいプロジェクト]** の順に選びます。</span><span class="sxs-lookup"><span data-stu-id="48b39-121">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="48b39-122">**[新しいプロジェクトの追加]** ダイアログで、**[Visual Basic]** ノードを展開し、**[.NET Standard]** ノードを選択し、**[クラス ライブラリ (.NET Standard)]** プロジェクト テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="48b39-122">In the **Add New Project** dialog, expand the **Visual Basic** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="48b39-123">**[名前]** テキスト ボックスに、プロジェクト名として「StringLibrary」と入力します。</span><span class="sxs-lookup"><span data-stu-id="48b39-123">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="48b39-124">**[OK]** を選んでクラス ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="48b39-124">Select **OK** to create the class library project.</span></span>

   ![[新しいプロジェクトの追加] ダイアログ](./media/vb-library-with-visual-studio/libproject.png)

   <span data-ttu-id="48b39-126">Visual Studio 開発環境でコード ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="48b39-126">The code window then opens in the Visual Studio development environment.</span></span> 
 
   ![既定のクラス ライブラリ テンプレート コードが表示された Visual Studio アプリケーション ウィンドウ](./media/vb-library-with-visual-studio/stringlibrary.png)

1. <span data-ttu-id="48b39-128">ライブラリが正しいバージョンの .NET Standard をターゲットにしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="48b39-128">Check to make sure that the library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="48b39-129">**ソリューション エクスプローラー** ウィンドウで、ライブラリ プロジェクトを右クリックし、**[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="48b39-129">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="48b39-130">**[ターゲット フレームワーク]** テキスト ボックスに、.NET Standard 2.0 がターゲットになっていることが示されています。</span><span class="sxs-lookup"><span data-stu-id="48b39-130">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![クラス ライブラリのプロジェクト プロパティ](./media/library-with-visual-studio/properties.png)

1. <span data-ttu-id="48b39-132">また、**[プロパティ]** ダイアログで、**[ルート名前空間]** テキスト ボックス内のテキストをクリアします。</span><span class="sxs-lookup"><span data-stu-id="48b39-132">Also in the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="48b39-133">各プロジェクトに対し、Visual Basic はプロジェクト名に対応する名前空間を自動的に作成します。ソース コード ファイルで定義されているすべての名前空間は、その名前空間の親です。</span><span class="sxs-lookup"><span data-stu-id="48b39-133">For each project, Visual Basic automatically creates a namespace that corresponds to the project name, and any namespaces defined in source code files are parents of that namespace.</span></span> <span data-ttu-id="48b39-134">[`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) キーワードを使用して最上位レベルの名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="48b39-134">We want to define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword.</span></span>
  
1. <span data-ttu-id="48b39-135">コード ウィンドウ内のコードを次のコードに置き換えて、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="48b39-135">Replace the code in the code window with the following code and save the file:</span></span>

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="48b39-136">クラス ライブラリ `UtilityLibraries.StringLibrary` には `StartsWithUpper` という名前のメソッドが含まれており、これによって、現在の文字列のインスタンスが大文字で始まるかどうかを示す <xref:System.Boolean> 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="48b39-136">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="48b39-137">Unicode 規格では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="48b39-137">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="48b39-138"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> メソッドは文字が大文字の場合に `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="48b39-138">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="48b39-139">メニュー バーで **[ビルド]** > **[ソリューションのビルド]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="48b39-139">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="48b39-140">プロジェクトはエラーなしでコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="48b39-140">The project should compile without error.</span></span>

   ![ビルドが成功したことを示す出力ペイン](./media/library-with-visual-studio/buildsucceeds.png)



## <a name="next-step"></a><span data-ttu-id="48b39-142">次のステップ</span><span class="sxs-lookup"><span data-stu-id="48b39-142">Next step</span></span>

<span data-ttu-id="48b39-143">ライブラリを正常に作成できました。</span><span class="sxs-lookup"><span data-stu-id="48b39-143">You've successfully built the library.</span></span> <span data-ttu-id="48b39-144">そのメソッドの呼び出しをまだ行っていないので、期待どおりに動作するかわかりません。</span><span class="sxs-lookup"><span data-stu-id="48b39-144">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="48b39-145">ライブラリ開発の次のステップでは、[単体テスト プロジェクト](testing-library-with-visual-studio.md)を使ってライブラリをテストします。</span><span class="sxs-lookup"><span data-stu-id="48b39-145">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>
