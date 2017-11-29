---
title: "C# のバージョン管理 - C# ガイド"
description: "C# と .NET でのバージョン管理のしくみについて説明します"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.date: 01/08/2017
ms.topic: article
ms.prod: visual-studio-dev-14
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 0b671333019c00abafcfb72533e30936f8fc6ad7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="versioning-in-c"></a><span data-ttu-id="98b22-104">C# でのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="98b22-104">Versioning in C#</span></span> #

<span data-ttu-id="98b22-105">このチュートリアルでは、.NET でのバージョン管理のしくみについて学習します。</span><span class="sxs-lookup"><span data-stu-id="98b22-105">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="98b22-106">また、ライブラリのバージョン管理を行う際や、ライブラリを新しいバージョンにアップグレードする際の考慮事項についても学習します。</span><span class="sxs-lookup"><span data-stu-id="98b22-106">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of the a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="98b22-107">ライブラリの作成</span><span class="sxs-lookup"><span data-stu-id="98b22-107">Authoring Libraries</span></span>

<span data-ttu-id="98b22-108">一般用途向けの .NET ライブラリを作成したことがある開発者であれば、新しい更新プログラムをロールアウトする必要に迫られた経験もあることでしょう。</span><span class="sxs-lookup"><span data-stu-id="98b22-108">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="98b22-109">このプロセスのあり方によって、既存のコードを新バージョンのライブラリへとシームレスに移行できるかどうかは大きく左右されます。</span><span class="sxs-lookup"><span data-stu-id="98b22-109">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="98b22-110">ここでは、新しいリリースを作成する際に考慮すべき点について、いくつか説明します。</span><span class="sxs-lookup"><span data-stu-id="98b22-110">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="98b22-111">セマンティック バージョン管理</span><span class="sxs-lookup"><span data-stu-id="98b22-111">Semantic Versioning</span></span>

<span data-ttu-id="98b22-112">[セマンティック バージョン管理](http://semver.org/) (略して SemVer) は、特定のマイルス トーン イベントを示すためにライブラリの各バージョンに適用される命名規則です。</span><span class="sxs-lookup"><span data-stu-id="98b22-112">[Semantic versioning](http://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="98b22-113">うまく管理すれば、ライブラリに適用されたバージョン情報によって、同じライブラリの旧バージョンを使用したプロジェクトとの互換性を開発者が確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="98b22-113">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="98b22-114">SemVer に対する最も基本的なアプローチは、3 コンポーネント形式 `MAJOR.MINOR.PATCH` です。</span><span class="sxs-lookup"><span data-stu-id="98b22-114">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>
 
* <span data-ttu-id="98b22-115">`MAJOR` は、互換性のない API 変更を加えたときにインクリメントされます</span><span class="sxs-lookup"><span data-stu-id="98b22-115">`MAJOR` is incremented when you make incompatible API changes</span></span>
* <span data-ttu-id="98b22-116">`MINOR` は、下位互換性のある方法で機能を追加したときにインクリメントされます</span><span class="sxs-lookup"><span data-stu-id="98b22-116">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
* <span data-ttu-id="98b22-117">`PATCH` は、下位互換性のあるバグ修正を行ったときにインクリメントされます</span><span class="sxs-lookup"><span data-stu-id="98b22-117">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="98b22-118">.NET ライブラリにバージョン情報を適用する際には、他のシナリオ (プレリリース バージョンなど) を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="98b22-118">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="98b22-119">下位互換性</span><span class="sxs-lookup"><span data-stu-id="98b22-119">Backwards Compatibility</span></span>

<span data-ttu-id="98b22-120">ライブラリの新バージョンをリリースする際、特に大きな懸念事項となるのが、旧バージョンとの互換性です。</span><span class="sxs-lookup"><span data-stu-id="98b22-120">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="98b22-121">旧バージョンに依存するコードが再コンパイル後に新バージョンで機能する場合、ライブラリの新バージョンは旧バージョンに対してソース互換性があるということになります。</span><span class="sxs-lookup"><span data-stu-id="98b22-121">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span> <span data-ttu-id="98b22-122">旧バージョンに依存するアプリケーションが再コンパイルを経ずに新バージョンで機能する場合、ライブラリの新バージョンはバイナリ互換性があるということになります。</span><span class="sxs-lookup"><span data-stu-id="98b22-122">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="98b22-123">次に示すのは、旧バージョンのライブラリとの下位互換性を維持するうえでの考慮事項です。</span><span class="sxs-lookup"><span data-stu-id="98b22-123">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

* <span data-ttu-id="98b22-124">仮想メソッド: 新バージョンで仮想メソッド非仮想にした場合は、そのメソッドをオーバーライドするプロジェクトを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98b22-124">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="98b22-125">これはきわめて重大な変更であり、極力回避することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="98b22-125">This is a huge breaking change and is strongly discouraged.</span></span>
* <span data-ttu-id="98b22-126">メソッドのシグネチャ: メソッドの動作を更新するためにそのシグネチャも変更する必要がある場合は、代わりにオーバー ロードを作成して、そのメソッドに対するコード呼び出しがその後も機能するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="98b22-126">Method signatures: When updating a method behaviour requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="98b22-127">旧メソッドのシグネチャは、新しいメソッド シグネチャを呼び出すようにいつでも操作して、実装の整合性を維持できます。</span><span class="sxs-lookup"><span data-stu-id="98b22-127">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
* <span data-ttu-id="98b22-128">[Obsolete 属性](programming-guide/concepts/attributes/common-attributes.md#Obsolete): この属性をコード内で使用すると、現在非推奨に指定されていて、今後のバージョンで削除される可能性が高いクラスやクラス メンバーを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="98b22-128">[Obsolete attribute](programming-guide/concepts/attributes/common-attributes.md#Obsolete): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span>
<span data-ttu-id="98b22-129">これにより、ライブラリを使用している開発者が、今後の重大な変更に余裕を持って準備できるようになります。</span><span class="sxs-lookup"><span data-stu-id="98b22-129">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
* <span data-ttu-id="98b22-130">省略可能なメソッド引数: これまで省略可能であったメソッド引数を必須にしたり、それらの既定値を変更する場合は、それらの引数が指定されていないすべてのコードを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98b22-130">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>
> [!NOTE]
> <span data-ttu-id="98b22-131">必須の引数を省略可能にしても、メソッドの動作が変更されない限り、影響はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="98b22-131">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behaviour.</span></span>

<span data-ttu-id="98b22-132">新バージョンのライブラリへの更新を行いやすくすれば、その分、ユーザーがアップグレードを早く完了できるようになります。</span><span class="sxs-lookup"><span data-stu-id="98b22-132">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="98b22-133">アプリケーション構成ファイル</span><span class="sxs-lookup"><span data-stu-id="98b22-133">Application Configuration File</span></span>

<span data-ttu-id="98b22-134">.NET 開発者の皆さんは、ほとんどのタイプのプロジェクトで [`app.config` ファイル](https://msdn.microsoft.com/en-us/library/1fk1t1t0(v=vs.110).aspx)を使用しているのではないでしょうか。</span><span class="sxs-lookup"><span data-stu-id="98b22-134">As a .NET developer there's a very high chance you've encountered [the `app.config` file](https://msdn.microsoft.com/en-us/library/1fk1t1t0(v=vs.110).aspx) present in most project types.</span></span>
<span data-ttu-id="98b22-135">このシンプルな構成ファイルは、新しい更新プログラムのロールアウトをスムーズにするうえで大いに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="98b22-135">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="98b22-136">通常、ライブラリを設計する際には、定期的に変更される可能性が高い情報を `app.config` ファイルに保存します。そうすれば、それらの情報が更新された際にも、ライブラリの再コンパイルを行うことなく、旧バージョンの構成ファイルを新しいバージョンに置き換えるだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="98b22-136">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="98b22-137">ライブラリの使用</span><span class="sxs-lookup"><span data-stu-id="98b22-137">Consuming Libraries</span></span>

<span data-ttu-id="98b22-138">他の開発者によって作成された .NET ライブラリを使用する場合には、新バージョンのライブラリが自分のプロジェクトに対して完全互換ではない場合が多く、それらの変更にうまく対応するために、コードを更新しなければならないことも少なくありません。</span><span class="sxs-lookup"><span data-stu-id="98b22-138">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="98b22-139">幸いなことに、C# と .NET エコシステムでは、重大な変更をもたらす可能性がある新バージョンのライブラリと正常に連携できるよう、アプリを簡単に更新するための機能や技術が提供されています。</span><span class="sxs-lookup"><span data-stu-id="98b22-139">Lucky for you C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="98b22-140">アセンブリ バインド リダイレクト</span><span class="sxs-lookup"><span data-stu-id="98b22-140">Assembly Binding Redirection</span></span>

<span data-ttu-id="98b22-141">`app.config` ファイルを使用して、アプリで使用するライブラリのバージョンを更新できます。</span><span class="sxs-lookup"><span data-stu-id="98b22-141">You can use the `app.config` file to update the version of a library your app uses.</span></span> <span data-ttu-id="98b22-142">[*バインド リダイレクト*](https://msdn.microsoft.com/en-us/library/7wd6ex19(v=vs.110).aspx)というものを追加することで、 アプリを再コンパイルしなくても、新しいライブラリ バージョンを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="98b22-142">By adding what is called a [*binding redirect*](https://msdn.microsoft.com/en-us/library/7wd6ex19(v=vs.110).aspx) your can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="98b22-143">次の例は、アプリの `app.config` ファイルを更新して、当初のコンパイルに使用された `1.0.0` バージョンではなく、`1.0.1` パッチ バージョンの `ReferencedLibrary` が使用されるようにする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="98b22-143">The following example shows how you would update your app's `app.config` file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="98b22-144">このアプローチは、新バージョンの `ReferencedLibrary` がアプリに対してバイナリ互換性を持っている場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="98b22-144">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="98b22-145">互換性を判断するときに注意すべき変更点については、上記の「[下位互換性](#backwards-compatibility)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="98b22-145">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="98b22-146">new</span><span class="sxs-lookup"><span data-stu-id="98b22-146">new</span></span>

<span data-ttu-id="98b22-147">`new` 修飾子を使用して、基底クラスの継承メンバーを非表示にできます。</span><span class="sxs-lookup"><span data-stu-id="98b22-147">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="98b22-148">これは、派生クラスが基底クラスの更新に対応できるようにするための 1 つの手段です。</span><span class="sxs-lookup"><span data-stu-id="98b22-148">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="98b22-149">次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98b22-149">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="98b22-150">**出力**</span><span class="sxs-lookup"><span data-stu-id="98b22-150">**Output**</span></span>

```
A base method
A derived method
```

<span data-ttu-id="98b22-151">上記の例では、`DerivedClass` によって `BaseClass` 内の `MyMethod` メソッドを非表示にしています。</span><span class="sxs-lookup"><span data-stu-id="98b22-151">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="98b22-152">つまり、派生クラス内に既に存在しているメンバーが新バージョンのライブラリ内の基底クラスによって追加された場合には、派生クラスのメンバーに `new` 修飾子を使用するだけで、基底クラスのメンバーを非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="98b22-152">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="98b22-153">`new` 修飾子が指定されなかった場合、派生クラスは既定で基底クラスの競合メンバーを非表示にします。コンパイラの警告が生成されますが、コードはコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="98b22-153">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="98b22-154">つまり、既存のクラスに新しいメンバーを追加するだけで、新バージョンのライブラリは依存先のコードに対して、ソースとバイナリの両方の互換性を持つことになります。</span><span class="sxs-lookup"><span data-stu-id="98b22-154">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="98b22-155">override</span><span class="sxs-lookup"><span data-stu-id="98b22-155">override</span></span>

<span data-ttu-id="98b22-156">`override` 修飾子を使用した場合、派生実装は基底クラス メンバーの実装を非表示にはせず、そのメンバーを拡張します。</span><span class="sxs-lookup"><span data-stu-id="98b22-156">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="98b22-157">基底クラスのメンバーには、`virtual` 修飾子が適用されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="98b22-157">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="98b22-158">**出力**</span><span class="sxs-lookup"><span data-stu-id="98b22-158">**Output**</span></span>

```
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="98b22-159">`override` 修飾子はコンパイル時に評価され、オーバーライドする仮想メンバーが見つからない場合には、コンパイラがエラーをスローします。</span><span class="sxs-lookup"><span data-stu-id="98b22-159">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="98b22-160">ここで説明したテクニックを身につけ、それらをいつ使用すればよいかを理解すれば、ライブラリ バージョン間の移行を大幅に容易にすることができます。</span><span class="sxs-lookup"><span data-stu-id="98b22-160">Your knowledge of the discussed techniques as well as your understanding of what situations to use them will go a long way to boost the ease of transition between versions of a library.</span></span>
