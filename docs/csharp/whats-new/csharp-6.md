---
title: C# 6 の新機能 - C# ガイド
description: C# バージョン 6 の新機能について説明します
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: c23d4f45441451fbf8a2ad2f939bdb1ed6144154
ms.sourcegitcommit: b7763f3435635850a76d4cbcf09bdce6c019208a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
ms.locfileid: "34483490"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="bb9b3-103">C# 6 の新機能</span><span class="sxs-lookup"><span data-stu-id="bb9b3-103">What's New in C# 6</span></span>

<span data-ttu-id="bb9b3-104">C# の 6.0 リリースには、開発者の生産性を向上させる多くの機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="bb9b3-105">このリリースの新機能には、次の機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-105">Features in this release include:</span></span>

* <span data-ttu-id="bb9b3-106">[読み取り専用の自動プロパティ](#read-only-auto-properties):</span><span class="sxs-lookup"><span data-stu-id="bb9b3-106">[Read-only Auto-properties](#read-only-auto-properties):</span></span>
    - <span data-ttu-id="bb9b3-107">コンス トラクターでのみ設定できる、読み取り専用の自動プロパティ を作成できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-107">You can create read-only auto-properties that can be set only in constructors.</span></span>
* <span data-ttu-id="bb9b3-108">[自動プロパティの初期化子](#auto-property-initializers):</span><span class="sxs-lookup"><span data-stu-id="bb9b3-108">[Auto-Property Initializers](#auto-property-initializers):</span></span>
    - <span data-ttu-id="bb9b3-109">自動プロパティの初期値を設定する初期化式を記述できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-109">You can write initialization expressions to set the initial value of an auto-property.</span></span>
* <span data-ttu-id="bb9b3-110">[式形式の関数メンバー](#expression-bodied-function-members):</span><span class="sxs-lookup"><span data-stu-id="bb9b3-110">[Expression-bodied function members](#expression-bodied-function-members):</span></span>
    - <span data-ttu-id="bb9b3-111">ラムダ式を使用して、1 行のメソッドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-111">You can author one-line methods using lambda expressions.</span></span>
* <span data-ttu-id="bb9b3-112">[using static](#using-static):</span><span class="sxs-lookup"><span data-stu-id="bb9b3-112">[using static](#using-static):</span></span>
    - <span data-ttu-id="bb9b3-113">1 つのクラスのすべてのメソッドを、現在の名前空間にインポートできます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-113">You can import all the methods of a single class into the current namespace.</span></span>
* <span data-ttu-id="bb9b3-114">[null 条件演算子](#null-conditional-operators):</span><span class="sxs-lookup"><span data-stu-id="bb9b3-114">[Null - conditional operators](#null-conditional-operators):</span></span>
    - <span data-ttu-id="bb9b3-115">null 条件演算子で null をチェックしながら、オブジェクトのメンバーに簡潔かつ安全にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-115">You can concisely and safely access members of an object while still checking for null with the null conditional operator.</span></span>
* <span data-ttu-id="bb9b3-116">[文字列補間](#string-interpolation):</span><span class="sxs-lookup"><span data-stu-id="bb9b3-116">[String Interpolation](#string-interpolation):</span></span>
    - <span data-ttu-id="bb9b3-117">位置指定引数の代わりに、インライン式を使用して書式設定文字列式をを記述できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-117">You can write string formatting expressions using inline expressions instead of positional arguments.</span></span>
* <span data-ttu-id="bb9b3-118">[例外フィルター](#exception-filters):</span><span class="sxs-lookup"><span data-stu-id="bb9b3-118">[Exception filters](#exception-filters):</span></span>
    - <span data-ttu-id="bb9b3-119">例外のプロパティやその他のプログラム状態に基づいて、式をキャッチできます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-119">You can catch expressions based on properties of the exception or other program state.</span></span> 
* <span data-ttu-id="bb9b3-120">[nameof 式](#nameof-expressions):</span><span class="sxs-lookup"><span data-stu-id="bb9b3-120">[nameof Expressions](#nameof-expressions):</span></span>
    - <span data-ttu-id="bb9b3-121">コンパイラで記号の文字列表現を生成できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-121">You can let the compiler generate string representations of symbols.</span></span>
* <span data-ttu-id="bb9b3-122">[Catch ブロックと Finally ブロックでの Await](#await-in-catch-and-finally-blocks):</span><span class="sxs-lookup"><span data-stu-id="bb9b3-122">[await in catch and finally blocks](#await-in-catch-and-finally-blocks):</span></span>
    - <span data-ttu-id="bb9b3-123">以前は許可されなかった場所で `await` 式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-123">You can use `await` expressions in locations that previously disallowed them.</span></span>
* <span data-ttu-id="bb9b3-124">[インデックス初期化子](#index-initializers):</span><span class="sxs-lookup"><span data-stu-id="bb9b3-124">[index initializers](#index-initializers):</span></span>
    - <span data-ttu-id="bb9b3-125">シーケンス コンテナーだけでなく、連想コンテナーの初期化式も作成できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-125">You can author initialization expressions for associative containers as well as sequence containers.</span></span>
* <span data-ttu-id="bb9b3-126">[コレクション初期化子の拡張メソッド](#extension-add-methods-in-collection-initializers):</span><span class="sxs-lookup"><span data-stu-id="bb9b3-126">[Extension methods for collection initializers](#extension-add-methods-in-collection-initializers):</span></span>
    - <span data-ttu-id="bb9b3-127">コレクション初期化子に、メンバー メソッドだけでなく、使いやすい拡張メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-127">Collection initializers can rely on accessible extension methods, in addition to member methods.</span></span>
* <span data-ttu-id="bb9b3-128">[オーバーロード解決の改善](#improved-overload-resolution):</span><span class="sxs-lookup"><span data-stu-id="bb9b3-128">[Improved overload resolution](#improved-overload-resolution):</span></span>
    - <span data-ttu-id="bb9b3-129">以前はあいまいなメソッド呼び出しを生成していた一部のコンストラクトを、正しく解決できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-129">Some constructs that previously generated ambiguous method calls now resolve correctly.</span></span>

<span data-ttu-id="bb9b3-130">これらの機能がもたらす全体的な効果として、より読みやすく簡潔なコードを記述できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-130">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="bb9b3-131">一般的なベスト プラクティスを多数反映することで、構文に使用される形式的な記述が減っています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-131">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="bb9b3-132">形式的な記述が減ったことで、設計の意図が理解しやすくなっています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-132">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="bb9b3-133">これらの機能を十分に学習すれば、生産性が高まり、より読みやすいコードを記述できるようになります。また、言語の構造がわかりやすくなる分、コア機能の作業に専念できるようになります。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-133">Learn these features well, and you'll be more productive, write more readable code, and concentrate more on your core features than on the constructs of the language.</span></span>

<span data-ttu-id="bb9b3-134">このトピックでは、これらの各機能について詳しく説明していきます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-134">The remainder of this topic provides details on each of these features.</span></span>

## <a name="auto-property-enhancements"></a><span data-ttu-id="bb9b3-135">自動プロパティの機能強化</span><span class="sxs-lookup"><span data-stu-id="bb9b3-135">Auto-Property enhancements</span></span> 

<span data-ttu-id="bb9b3-136">自動的に実装されるプロパティ (通常、"自動プロパティ" と呼ばれる) の構文は、get と set のシンプルなアクセサーを使ったプロパティの作成を簡単にしました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-136">The syntax for automatically implemented properties (usually referred to as 'auto-properties') made it very easy to create properties that had simple get and set accessors:</span></span>

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

<span data-ttu-id="bb9b3-137">ただし、このシンプルな構文では、自動プロパティを使ってサポートできる設計の種類に制限がありました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-137">However, this simple syntax limited the kinds of designs you could support using auto-properties.</span></span> <span data-ttu-id="bb9b3-138">C# 6 では、自動プロパティの機能が強化され、より多くのシナリオで自動プロパティを使用できるようなりました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-138">C# 6 improves the auto-properties capabilities so that you can use them in more scenarios.</span></span> <span data-ttu-id="bb9b3-139">これにより、冗長な構文を宣言したり、バッキング フィールドを手動で操作する労力が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-139">You won't need to fall back on the more verbose syntax of declaring and manipulating the backing field by hand so often.</span></span>

<span data-ttu-id="bb9b3-140">新しい構文は、読み取り専用のプロパティを扱うシナリオや、自動プロパティの背後での変数格納を初期化するシナリオに対応しています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-140">The new syntax addresses scenarios for read-only properties, and for initializing the variable storage behind an auto-property.</span></span>

### <a name="read-only-auto-properties"></a><span data-ttu-id="bb9b3-141">読み取り専用の自動プロパティ</span><span class="sxs-lookup"><span data-stu-id="bb9b3-141">Read-only auto-properties</span></span>

<span data-ttu-id="bb9b3-142">*読み取り専用の自動プロパティ*を使用すると、より簡潔な構文で不変型を作成できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-142">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="bb9b3-143">以前のバージョンの C# では、不変型を作成するための最も簡単な方法は、プライベート セッターを宣言する方法でした。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-143">The closest you could get to immutable types in earlier versions of C# was to declare private setters:</span></span>

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
<span data-ttu-id="bb9b3-144">この構文を使用した場合、コンパイラは型が本当に変更不可であることを保証できません。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-144">Using this syntax, the compiler doesn't ensure that the type really is immutable.</span></span> <span data-ttu-id="bb9b3-145">`FirstName` プロパティと `LastName` プロパティが、クラス外部のコードから変更されないようにするだけです。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-145">It only enforces that the `FirstName` and `LastName` properties are not modified from any code outside the class.</span></span>

<span data-ttu-id="bb9b3-146">読み取り専用の自動プロパティを使用すれば、真の読み取り専用動作を実現できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-146">Read-only auto-properties enable true read-only behavior.</span></span> <span data-ttu-id="bb9b3-147">自動プロパティは、get アクセサーのみを使用して宣言します。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-147">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="bb9b3-148">`FirstName` プロパティと `LastName` プロパティは、コンス トラクターの本体でのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-148">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="bb9b3-149">別のメソッドで `LastName` を設定しようとすると、コンパイル エラー `CS0200` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-149">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

<span data-ttu-id="bb9b3-150">この機能を使用すれば、不変型を作成したり、より簡潔で便利な自動プロパティ構文を使用するための、本格的な言語サポートを実現できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-150">This feature enables true language support for creating immutable types and using the more concise and convenient auto-property syntax.</span></span>

### <a name="auto-property-initializers"></a><span data-ttu-id="bb9b3-151">自動プロパティ初期化子</span><span class="sxs-lookup"><span data-stu-id="bb9b3-151">Auto-Property Initializers</span></span>

<span data-ttu-id="bb9b3-152">*自動プロパティ初期化子*を使用すると、プロパティ宣言の一部として自動プロパティの初期値を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-152">*Auto-Property Initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>  <span data-ttu-id="bb9b3-153">以前のバージョンでは、これらのプロパティにはセッターが必要でした。そのセッターを使用して、バッキング フィールドによって使用されるデータ ストレージを初期化する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-153">In earlier versions, these properties would need to have setters and you would need to use that setter to initialize the data storage used by the backing field.</span></span> <span data-ttu-id="bb9b3-154">たとえば、生徒の名前と成績を含んだ、生徒用のクラスがあるとします。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-154">Consider this class for a student that contains the name and a list of the student's grades:</span></span>

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
<span data-ttu-id="bb9b3-155">このクラスが大きくなってくると、他のコンス トラクターが追加されることもあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-155">As this class grows, you may include other constructors.</span></span> <span data-ttu-id="bb9b3-156">各コンス トラクターでは、このフィールドを初期化する必要があります。そうしないとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-156">Each constructor needs to initialize this field, or you'll introduce errors.</span></span>

<span data-ttu-id="bb9b3-157">C# 6 では、自動プロパティ宣言で自動プロパティによって使用されるストレージの初期値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-157">C# 6 enables you to assign an initial value for the storage used by an auto-property in the auto-property declaration:</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="bb9b3-158">`Grades` メンバーは宣言された場所で初期化されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-158">The `Grades` member is initialized where it is declared.</span></span> <span data-ttu-id="bb9b3-159">これにより、初期化を厳密に 1 回だけ実行しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-159">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="bb9b3-160">初期化がプロパティ宣言の一部になることで、ストレージ割り当てが `Student` オブジェクトのパブリック インターフェイスと同じであることを示しやすくなっています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-160">The initialization is part of the property declaration, making it easier to equate the storage allocation with public interface for `Student` objects.</span></span>

<span data-ttu-id="bb9b3-161">次のように、プロパティ初期化子は読み取り専用プロパティだけでなく、読み取り/書き込みプロパティにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-161">Property Initializers can be used with read/write properties as well as read-only properties, as shown here.</span></span>

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a><span data-ttu-id="bb9b3-162">式形式の関数メンバー</span><span class="sxs-lookup"><span data-stu-id="bb9b3-162">Expression-bodied function members</span></span>

<span data-ttu-id="bb9b3-163">開発者が記述する多くのメンバーの本文は、式として表すことができる 1 つのステートメントだけで構成されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-163">The body of a lot of members that we write consist of only one statement that can be represented as an expression.</span></span> <span data-ttu-id="bb9b3-164">これに代えて式形式のメンバーを記述すれば、その構文を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-164">You can reduce that syntax by writing an expression-bodied member instead.</span></span> <span data-ttu-id="bb9b3-165">この方法は、メソッドと読み取り専用プロパティに有効です。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-165">It works for methods and read-only properties.</span></span> <span data-ttu-id="bb9b3-166">たとえば、`ToString()` のオーバーライドはその好例です。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-166">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="bb9b3-167">式形式のメンバーは、読み取り専用のプロパティにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-167">You can also use expression-bodied members in read-only properties as well:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

## <a name="using-static"></a><span data-ttu-id="bb9b3-168">using static</span><span class="sxs-lookup"><span data-stu-id="bb9b3-168">using static</span></span>

<span data-ttu-id="bb9b3-169">*using static* 拡張機能を使用すると、1 つのクラスの静的メソッドをインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-169">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="bb9b3-170">これまで、`using` ステートメントは名前空間内のすべての型をインポートしていました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-170">Previously, the `using` statement imported all types in a namespace.</span></span> 

<span data-ttu-id="bb9b3-171">開発者はクラスの静的メソッドをコード内の随所で使用することがよくありますが、</span><span class="sxs-lookup"><span data-stu-id="bb9b3-171">Often we use a class' static methods throughout our code.</span></span> <span data-ttu-id="bb9b3-172">クラス名を繰り返し入力すると、コードの意味がわかりにくくなることもあります。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-172">Repeatedly typing the class name can obscure the meaning of your code.</span></span> <span data-ttu-id="bb9b3-173">一般的な例としては、多数の数値計算を実行するクラスが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-173">A common example is when you write classes that perform many numeric calculations.</span></span>
<span data-ttu-id="bb9b3-174">このようなクラスでは、<xref:System.Math> クラス内の異なるメソッドに対する <xref:System.Math.Sin%2A>、<xref:System.Math.Sqrt%2A>、およびその他の呼び出しがコード内に散在することになります。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-174">Your code will be littered with <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> and other calls to different methods in the <xref:System.Math> class.</span></span> <span data-ttu-id="bb9b3-175">新しい `using static` 構文では、これらのクラスを大幅に簡潔化し、読みやすくすることができます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-175">The new `using static` syntax can make these classes much cleaner to read.</span></span> <span data-ttu-id="bb9b3-176">具体的には、使用するクラスを次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-176">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="bb9b3-177">これで、<xref:System.Math> クラスを修飾しなくても、<xref:System.Math> クラス内の任意の静的メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-177">And now, you can use any static method in the <xref:System.Math> class without qualifying the <xref:System.Math> class.</span></span> <span data-ttu-id="bb9b3-178"><xref:System.Math> クラスにはインスタンス メソッドが含まれていないので、この機能が特に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-178">The <xref:System.Math> class is a great use case for this feature because it does not contain any instance methods.</span></span> <span data-ttu-id="bb9b3-179">また `using static` は、静的メソッドとインスタンス メソッドの両方を持つクラスの静的クラスをインポートするためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-179">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="bb9b3-180">特に便利な例の 1 つが <xref:System.String> です。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-180">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="bb9b3-181">static using ステートメントでは、完全修飾クラス名 (`System.String`) 使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-181">You must use the fully qualified class name, `System.String` in a static using statement.</span></span> <span data-ttu-id="bb9b3-182">代わりに `string` キーワードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-182">You cannot use the `string` keyword instead.</span></span> 

<span data-ttu-id="bb9b3-183">これで、<xref:System.String> クラス内で定義された静的メソッドを、そのクラスのメンバーとして修飾しなくても呼び出せるようになります。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-183">You can now call static methods defined in the <xref:System.String> class without qualifying those methods as members of that class:</span></span>

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

<span data-ttu-id="bb9b3-184">`static using` 機能と拡張メソッドは興味深い方法で相互作用し、言語設計には、それらの相互作用に具体的に対応するいくつかのルールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-184">The `static using` feature and extension methods interact in interesting ways, and the language design included some rules that specifically address those interactions.</span></span> <span data-ttu-id="bb9b3-185">その目的は、既存のコードベース (ユーザーのコードを含む) に重大な変更が生じる可能性を最小限に減らすことです。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-185">The goal is to minimize any chances of breaking changes in existing codebases, including yours.</span></span>

<span data-ttu-id="bb9b3-186">拡張メソッドは、拡張メソッドの呼び出し構文を使用して呼び出された場合にのみ、スコープ内に含められます。静的メソッドとして呼び出された場合には含められません。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-186">Extension methods are only in scope when called using the extension method invocation syntax, not when called as a static method.</span></span>
<span data-ttu-id="bb9b3-187">これは、LINQ クエリで多く見受けられることになるでしょう。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-187">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="bb9b3-188">LINQ パターンは、<xref:System.Linq.Enumerable> をインポートすることによってインポートできます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-188">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="bb9b3-189">このコードは、<xref:System.Linq.Enumerable> クラス内のすべてのメソッドをインポートします。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-189">This imports all the methods in the <xref:System.Linq.Enumerable> class.</span></span>
<span data-ttu-id="bb9b3-190">ただし拡張メソッドは、拡張メソッドとして呼び出された場合にしかスコープ内に含められません。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-190">However, the extension methods are only in scope when called as extension methods.</span></span> <span data-ttu-id="bb9b3-191">静的メソッドの構文を使用して呼び出された場合には、スコープに含められません。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-191">They are not in scope if they are called using the static method syntax:</span></span>

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

<span data-ttu-id="bb9b3-192">このような仕様になったのは、拡張メソッドが通常、拡張メソッドの呼び出し式を使用して呼び出されるためです。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-192">This decision is because extension methods are typically called using extension method invocation expressions.</span></span> <span data-ttu-id="bb9b3-193">まれに、静的メソッドの呼び出し構文を使用して呼び出される場合もありますが、それはあいまいさを解決するためです。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-193">In the rare case where they are called using the static method call syntax it is to resolve ambiguity.</span></span>
<span data-ttu-id="bb9b3-194">呼び出しには必ずクラス名を含めるようにするのが賢明と言えるでしょう。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-194">Requiring the class name as part of the invocation seems wise.</span></span>

<span data-ttu-id="bb9b3-195">最後に、`static using` の機能がもう1 つあります。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-195">There's one last feature of `static using`.</span></span> <span data-ttu-id="bb9b3-196">`static using` ディレクティブは、入れ子にされた型もインポートします。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-196">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="bb9b3-197">これにより、入れ子になった型を修飾なしで参照できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-197">That enables you to reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="bb9b3-198">Null 条件演算子</span><span class="sxs-lookup"><span data-stu-id="bb9b3-198">Null-conditional operators</span></span>

<span data-ttu-id="bb9b3-199">Null 値はコードを複雑にします。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-199">Null values complicate code.</span></span> <span data-ttu-id="bb9b3-200">開発者は変数のアクセスをすべてチェックして、`null` を逆参照していないことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-200">You need to check every access of variables to ensure you are not dereferencing `null`.</span></span> <span data-ttu-id="bb9b3-201">*Null 条件演算子*を使用すれば、これらのチェックをより簡単で円滑なものにすることができます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-201">The *null conditional operator* makes those checks much easier and fluid.</span></span>

<span data-ttu-id="bb9b3-202">やり方は、メンバー アクセス `.` を `?.` 置き換えるだけです。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-202">Simply replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="bb9b3-203">上記の例では、person オブジェクトが `null` の場合に、変数 `first` に `null` が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-203">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="bb9b3-204">その他の場合には、`FirstName` プロパティの値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-204">Otherwise, it gets assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="bb9b3-205">特に重要なのは、`?.` を使用した場合、変数 `person` が `null` であっても、このコード行では `NullReferenceException` が生成されないということです。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-205">Most importantly, the `?.` means that this line of code does not generate a `NullReferenceException` when the `person` variable is `null`.</span></span> <span data-ttu-id="bb9b3-206">代わりに、処理がショートサーキットされ、`null` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-206">Instead, it short-circuits and produces `null`.</span></span>

<span data-ttu-id="bb9b3-207">また、この式は `string` の値に関係なく、`person` を返します。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-207">Also, note that this expression returns a `string`, regardless of the value of `person`.</span></span>
<span data-ttu-id="bb9b3-208">処理がショート サーキットされた場合は、返された `null` 値が式全体に一致するように入力されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-208">In the case of short circuiting, the `null` value returned is typed to match the full expression.</span></span>

<span data-ttu-id="bb9b3-209">*null 結合*演算子を使用したこのコンストラクトは、いずれかのプロパティが `null` の場合に既定値を割り当てる目的で使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-209">You can often use this construct with the *null coalescing* operator to assign default values when one of the properties are `null`:</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="bb9b3-210">`?.` 演算子の右側のオペランドは、プロパティやフィールドに制限されません。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-210">The right hand side operand of the `?.` operator is not limited to properties or fields.</span></span>
<span data-ttu-id="bb9b3-211">メソッドを条件付きで呼び出すためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-211">You can also use it to conditionally invoke methods.</span></span> <span data-ttu-id="bb9b3-212">Null 条件演算子を使用したメンバー関数の最も一般的な用途は、`null` である可能性があるデリゲート (またはイベント ハンドラー) を安全に呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-212">The most common use of member functions with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="bb9b3-213">これを行うには、`?.` 演算子を使用してデリゲートの `Invoke` メソッドを呼び出し、メンバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-213">You'll do this by calling the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="bb9b3-214">この例は、</span><span class="sxs-lookup"><span data-stu-id="bb9b3-214">You can see an example in the</span></span>  
<span data-ttu-id="bb9b3-215">[デリゲート パターン](../delegates-patterns.md#handling-null-delegates)に関するトピックに記載されています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-215">[delegate patterns](../delegates-patterns.md#handling-null-delegates) topic.</span></span>

<span data-ttu-id="bb9b3-216">`?.` 演算子のルールでは、、演算子の左側が 1 回だけ評価されることが保証されています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-216">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="bb9b3-217">これは重要なことであり、これによって多くの表現方法が可能になります (イベント ハンドラーを使用した例を含む)。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-217">This is important and enables many idioms, including the example using event handlers.</span></span> <span data-ttu-id="bb9b3-218">まずは、イベント ハンドラーを使用した例から見ていきましょう。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-218">Let's start with the event handler usage.</span></span> <span data-ttu-id="bb9b3-219">以前のバージョンの C# では、コードを次のように記述することが推奨されていました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-219">In previous versions of C#, you were encouraged to write code like this:</span></span>

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

<span data-ttu-id="bb9b3-220">これは、次のような単純な構文よりも推奨されていました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-220">This was preferred over a simpler syntax:</span></span>

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> <span data-ttu-id="bb9b3-221">上記の例では、競合状態が発生しています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-221">The preceding example introduces a race condition.</span></span> <span data-ttu-id="bb9b3-222">`SomethingHappened` イベントは、`null` に対してチェックされた時点ではサブスクライバーが存在する可能性がありますが、それらのサブスクライバーは、イベントが生成する前に削除される可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-222">The `SomethingHappened` event may have subscribers when checked against `null`, and those subscribers may have been removed before the event is raised.</span></span> <span data-ttu-id="bb9b3-223">その場合、<xref:System.NullReferenceException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-223">That would cause a <xref:System.NullReferenceException> to be thrown.</span></span>

<span data-ttu-id="bb9b3-224">この 2 つ目のバージョンでは、`SomethingHappened` イベント ハンドラーがテスト時に Null 以外である可能性もありますが、その他のコードによってハンドラーが削除された場合には、イベント ハンドラーの呼び出し時に Null になっている可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-224">In this second version, the `SomethingHappened` event handler might be non-null when tested, but if other code removes a handler, it could still be null when the event handler was called.</span></span>

<span data-ttu-id="bb9b3-225">`?.` 演算子に対してコンパイラが生成するコードでは、`?.` 式の左側 (`this.SomethingHappened`) が 1 回だけ評価され、その結果がキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-225">The compiler generates code for the `?.` operator that ensures the left side (`this.SomethingHappened`) of the `?.` expression is evaluated once, and the result is cached:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="bb9b3-226">左側が 1 回しか評価されないことが確実であるということは、`?.` の左側で任意の式 (メソッド呼び出しを含む) を使用できるということでもあります。それらに副作用があったとしても、1 回しか評価されないので、副作用も 1 回しか発生しません。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-226">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.` Even if these have side-effects, they are evaluated once, so the side effects occur only once.</span></span> <span data-ttu-id="bb9b3-227">この例は、[イベント](../events-overview.md#language-support-for-events)に関するコンテンツで参照できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-227">You can see an example in our content on [events](../events-overview.md#language-support-for-events).</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="bb9b3-228">文字列補間</span><span class="sxs-lookup"><span data-stu-id="bb9b3-228">String Interpolation</span></span>

<span data-ttu-id="bb9b3-229">C# 6 で導入された新しい構文では、書式文字列と、その他の文字列値を生成するために評価される式から、文字列を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-229">C# 6 contains new syntax for composing strings from a format string and expressions that are evaluated to produce other string values.</span></span>

<span data-ttu-id="bb9b3-230">これまでは、`string.Format` などのメソッドで位置指定パラメーターを使用する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-230">Traditionally, you needed to use positional parameters in a method like `string.Format`:</span></span>

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

<span data-ttu-id="bb9b3-231">C# 6 では、新しい[文字列補間](../language-reference/tokens/interpolated.md)機能を使用して、書式文字列に式を埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-231">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed the expressions in the format string.</span></span> <span data-ttu-id="bb9b3-232">方法は、文字列の前に `$` を付けるだけです。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-232">Simply preface the string with `$`:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="bb9b3-233">この最初の例では、置換される式にプロパティ式を使用しています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-233">This initial example uses property expressions for the substituted expressions.</span></span> <span data-ttu-id="bb9b3-234">この構文を拡張することで、任意の式を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-234">You can expand on this syntax to use any expression.</span></span> <span data-ttu-id="bb9b3-235">たとえば、補間の一部として生徒の評価点の平均を計算することもできます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-235">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

<span data-ttu-id="bb9b3-236">上記の例を実行すると、`Grades.Average()` の出力に含まれる小数点以下の桁数が、開発者の意図よりも多くなる場合があることに気付くでしょう。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-236">Running the preceding example, you would find that the output for `Grades.Average()` might have more decimal places than you would like.</span></span> <span data-ttu-id="bb9b3-237">文字列補間の構文では、これまでの書式設定メソッドを通じて利用できるすべての書式がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-237">The string interpolation syntax supports all the format strings available using earlier formatting methods.</span></span> <span data-ttu-id="bb9b3-238">中かっこ内に書式文字列を追加し、</span><span class="sxs-lookup"><span data-stu-id="bb9b3-238">You add the format strings inside the braces.</span></span> <span data-ttu-id="bb9b3-239">書式設定する式 の後に、`:` を追加します。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-239">Add a `:` following the expression to format:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="bb9b3-240">上記のコード行では、`Grades.Average()` の値が、小数点以下 2 桁の浮動小数点数として書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-240">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="bb9b3-241">`:` は常に、書式設定される式と書式文字列との間の区切り記号として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-241">The `:` is always interpreted as the separator between the expression being formatted and the format string.</span></span> <span data-ttu-id="bb9b3-242">そのため、`:` が式内で別の目的 (条件演算子など) に使用されている場合には、問題が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-242">This can introduce problems when your expression uses a `:` in another way, such as a conditional operator:</span></span>

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

<span data-ttu-id="bb9b3-243">上記の例では、`:` は条件演算子の一部ではなく、書式文字列の開始点として解析されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-243">In the preceding example, the `:` is parsed as the beginning of the format string, not part of the conditional operator.</span></span> <span data-ttu-id="bb9b3-244">このような場合には、式を中かっこで囲むことで、コンパイラに正しく式を解釈させることができます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-244">In all cases where this happens, you can surround the expression with parentheses to force the compiler to interpret the expression as you intend:</span></span>

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

<span data-ttu-id="bb9b3-245">中かっこの間に配置できる式に制限はありません。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-245">There aren't any limitations on the expressions you can place between the braces.</span></span> <span data-ttu-id="bb9b3-246">補間文字列内で複雑な LINQ クエリを実行して計算を実行し、結果を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-246">You can execute a complex LINQ query inside an interpolated string to perform computations and display the result:</span></span>

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

<span data-ttu-id="bb9b3-247">この例のように、文字列補間式の内部で、別の文字列補間式を入れ子にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-247">You can see from this sample that you can even nest a string interpolation expression inside another string interpolation expression.</span></span> <span data-ttu-id="bb9b3-248">この例は開発者が運用コードで使用するものよりも複雑である可能性が高いですが、</span><span class="sxs-lookup"><span data-stu-id="bb9b3-248">This example is very likely more complex than you would want in production code.</span></span>
<span data-ttu-id="bb9b3-249">この機能の対応範囲を説明するためにあえて示しました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-249">Rather, it is illustrative of the breadth of the feature.</span></span> <span data-ttu-id="bb9b3-250">補間文字列の中かっこの間には、任意の C# 式を配置できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-250">Any C# expression can be placed between the curly braces of an interpolated string.</span></span>

### <a name="string-interpolation-and-specific-cultures"></a><span data-ttu-id="bb9b3-251">文字列補間と特定のカルチャ</span><span class="sxs-lookup"><span data-stu-id="bb9b3-251">String interpolation and specific cultures</span></span>

<span data-ttu-id="bb9b3-252">前のセクションで示した例はいずれも、コードが実行されるマシンの現在のカルチャと言語を使用して文字列を書式設定するものでした。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-252">All the examples shown in the preceding section format the strings using the current culture and language on the machine where the code executes.</span></span> <span data-ttu-id="bb9b3-253">しかし場合によっては、生成された文字列を特定のカルチャで書式設定する必要が生じる場合もあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-253">Often you may need to format the string produced using a specific culture.</span></span>
<span data-ttu-id="bb9b3-254">これを行うには、文字列補間によって生成されたオブジェクトは暗黙的に <xref:System.FormattableString> に変換できることを利用します。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-254">To do that use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString>.</span></span>

<span data-ttu-id="bb9b3-255"><xref:System.FormattableString> インスタンスには、書式文字列と、それらを文字列に変換する前の式評価の結果が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-255">The <xref:System.FormattableString> instance contains the format string, and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="bb9b3-256"><xref:System.FormattableString> のパブリック メソッドを使用すれば、文字列の書式設定時にカルチャを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-256">You can use public methods of <xref:System.FormattableString> to specify the culture when formatting a string.</span></span> <span data-ttu-id="bb9b3-257">たとえば、次の例は、ドイツのカルチャを使用して文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-257">For example, the following example produces a string using German culture.</span></span> <span data-ttu-id="bb9b3-258">(小数点区切り文字に ',' 文字が使用され、桁区切り記号に '.' 文字が使用されます。)</span><span class="sxs-lookup"><span data-stu-id="bb9b3-258">(It uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="bb9b3-259">詳細については、[文字列補間](../language-reference/tokens/interpolated.md)に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-259">For more information, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="bb9b3-260">例外フィルター</span><span class="sxs-lookup"><span data-stu-id="bb9b3-260">Exception Filters</span></span>

<span data-ttu-id="bb9b3-261">C# 6 では、*例外フィルター*という新機能も追加されています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-261">Another new feature in C# 6 is *exception filters*.</span></span> <span data-ttu-id="bb9b3-262">例外フィルターは、特定の catch 句がいつ適用されるのかを決定する句です。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-262">Exception Filters are clauses that determine when a given catch clause should be applied.</span></span>
<span data-ttu-id="bb9b3-263">例外フィルターに使用されている式が `true` と評価された場合、catch 句は例外に対して通常の処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-263">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="bb9b3-264">式が `false` と評価された場合、`catch` 句はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-264">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span>

<span data-ttu-id="bb9b3-265">用途としては、例外に関する情報を調べて、`catch` 句で例外を処理できるかどうかを確認するという使い方があります。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-265">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

<span data-ttu-id="bb9b3-266">例外フィルターによって生成されたコードには、スローされ、処理されていない例外についての詳細な情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-266">The code generated by exception filters provides better information about an exception that is thrown and not processed.</span></span> <span data-ttu-id="bb9b3-267">例外フィルターがこの言語に追加される以前は、次のようなコードを作成する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-267">Before exception filters were added to the language, you would need to create code like the following:</span></span>

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

<span data-ttu-id="bb9b3-268">これら 2 つの例では、例外がスローされるポイントが異なります。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-268">The point where the exception is thrown changes between these two examples.</span></span>
<span data-ttu-id="bb9b3-269">旧来のコード (`throw` 句を使用したコード) では、スタック トレースの分析やクラッシュ ダンプの調査を実行した場合、catch 句内の `throw` ステートメントから例外がスローされたと示されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-269">In the previous code, where a `throw` clause is used, any stack trace analysis or examination of crash dumps will show that the exception was thrown from the `throw` statement in your catch clause.</span></span> <span data-ttu-id="bb9b3-270">実際の例外オブジェクトには元の呼び出し履歴が含まれますが、このスロー ポイントと元のスロー ポイントとの間での呼び出し履歴内にあるその他の変数情報はすべて失われます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-270">The actual exception object will contain the original call stack, but all other information about any variables in the call stack between this throw point and the location of the original throw point has been lost.</span></span> 

<span data-ttu-id="bb9b3-271">これに対し、例外フィルターを使用したコードはどのように処理されるかというと、例外フィルター式が `false` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-271">Contrast that with how the code using an exception filter is processed: the exception filter expression evaluates to `false`.</span></span> <span data-ttu-id="bb9b3-272">そのため、`catch` 句が実行されることはありません。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-272">Therefore, execution never enters the `catch` clause.</span></span> <span data-ttu-id="bb9b3-273">`catch` 句が実行されないので、スタックのアンワインドは行われません。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-273">Because the `catch` clause does not execute, no stack unwinding takes place.</span></span> <span data-ttu-id="bb9b3-274">つまり、以降に発生するいずれのデバッグ活動においても、元のスロー場所が保持されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-274">That means the original throw location is preserved for any debugging activities that would take place later.</span></span>

<span data-ttu-id="bb9b3-275">例外の種類のみを使用するのではなく、例外のフィールドやプロパティも評価する必要がある場合には、必ず例外フィルターを使用して、デバッグの詳細を保持するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-275">Whenever you need to evaluate fields or properties of an exception, instead of relying solely on the exception type, use an exception filter to preserve more debugging information.</span></span>

<span data-ttu-id="bb9b3-276">例外フィルターを使用するもう 1 つの推奨パターンとして、ルーチンのロギングがあります。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-276">Another recommended pattern with exception filters is to use them for logging routines.</span></span> <span data-ttu-id="bb9b3-277">例外フィルターが `false` と評価された場合に例外のスロー ポイントが保持されるという動作は、この用途でも役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-277">This usage also leverages the manner in which the exception throw point is preserved when an exception filter evaluates to `false`.</span></span>

<span data-ttu-id="bb9b3-278">次の例では、無条件に `false` を返す例外を、ロギング メソッドの引数にしています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-278">A logging method would be a method whose argument is the exception that unconditionally returns `false`:</span></span>

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

<span data-ttu-id="bb9b3-279">例外をログに記録する必要がある場合には、catch 句を追加し、このメソッドを例外フィルターとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-279">Whenever you want to log an exception, you can add a catch clause, and use this method as the exception filter:</span></span>

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

<span data-ttu-id="bb9b3-280">`LogException` メソッドは常に `false` を返するため、例外はキャッチされません。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-280">The exceptions are never caught, because the `LogException` method always returns `false`.</span></span> <span data-ttu-id="bb9b3-281">常に false となるこの例外フィルターを使用すれば、このロギング ハンドラーを、他のどの例外ハンドラーよりも前に配置することができます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-281">That always false exception filter means that you can place this logging handler before any other exception handlers:</span></span>

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

<span data-ttu-id="bb9b3-282">上記の例は、例外フィルターの非常に重要な特徴を示しています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-282">The preceding example highlights a very important facet of exception filters.</span></span>
<span data-ttu-id="bb9b3-283">それは、例外フィルターを使用すれば、詳細な例外 catch 句よりも前に、より一般的な例外 catch 句が配置されるシナリオにも対応できるということです。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-283">The exception filters enable scenarios where a more general exception catch clause may appear before a more specific one.</span></span> <span data-ttu-id="bb9b3-284">また、複数の catch 句に同じ種類の例外を配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-284">It's also possible to have the same exception type appear in multiple catch clauses:</span></span>

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

<span data-ttu-id="bb9b3-285">もう 1 つの推奨パターンとして、デバッガーがアタッチされている場合には catch 句で例外を処理しないようにする用途もあります。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-285">Another recommended pattern helps prevent catch clauses from processing exceptions when a debugger is attached.</span></span> <span data-ttu-id="bb9b3-286">この手法を使用すれば、デバッガーを使ってアプリケーションを実行し、例外がスローされた場合には実行を停止することができます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-286">This technique enables you to run an application with the debugger, and stop execution when an exception is thrown.</span></span>

<span data-ttu-id="bb9b3-287">具体的には、コードに例外フィルターを追加して、デバッガーがアタッチされていない場合にのみ、修復コードが実行されるようにします。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-287">In your code, add an exception filter so that any recovery code executes only when a debugger is not attached:</span></span>

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

<span data-ttu-id="bb9b3-288">この記述をコードに追加した後、すべての未処理例外に対して処理を中断するようにデバッガーを設定します。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-288">After adding this in code, you set your debugger to break on all unhandled exceptions.</span></span> <span data-ttu-id="bb9b3-289">その後デバッガーを使用してプログラムを実行すると、デバッガーは `PerformFailingOperation()` が `RecoverableException` をスローするたびに処理を中断します。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-289">Run the program under the debugger, and the debugger breaks whenever `PerformFailingOperation()` throws a `RecoverableException`.</span></span>
<span data-ttu-id="bb9b3-290">false を返す例外フィルターがあるため catch 句は実行されず、デバッガーがプログラムを中断します。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-290">The debugger breaks your program, because the catch clause won't be executed due to the false-returning exception filter.</span></span>

## <a name="nameof-expressions"></a><span data-ttu-id="bb9b3-291">`nameof` 式</span><span class="sxs-lookup"><span data-stu-id="bb9b3-291">`nameof` Expressions</span></span>

<span data-ttu-id="bb9b3-292">`nameof` 式はシンボルの名前を評価します。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-292">The `nameof` expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="bb9b3-293">この式は、変数、プロパティ、またはメンバー フィールドの名前が必要なときに便利です。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-293">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span>

<span data-ttu-id="bb9b3-294">`nameof` の用途として特に一般的なものの 1 つは、例外の原因となったシンボルの名前を取得することです。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-294">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="bb9b3-295">また、`INotifyPropertyChanged` インターフェイスを実装する XAML ベースのアプリケーションでも使用されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-295">Another use is with XAML based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

<span data-ttu-id="bb9b3-296">`nameof` 演算子が定数文字列よりも便利な点は、ツールがシンボルを把握できるという点です。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-296">The advantage of using the `nameof` operator over a constant string is that tools can understand the symbol.</span></span> <span data-ttu-id="bb9b3-297">リファクタリング ツールを使用してシンボルの名前を変更すると、その名前が `nameof` 式で変更されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-297">If you use refactoring tools to rename the symbol, it will rename it in the `nameof` expression.</span></span> <span data-ttu-id="bb9b3-298">これは、定数文字列にはない利点です。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-298">Constant strings don't have that advantage.</span></span> <span data-ttu-id="bb9b3-299">好みのエディターを使用して変数の名前を変更すれば、`nameof` 式も更新されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-299">Try it yourself in your favorite editor: rename a variable, and any `nameof` expressions will update as well.</span></span>

<span data-ttu-id="bb9b3-300">`nameof` 式は、開発者が引数の完全修飾名を使用した場合でも、引数の非修飾名 (上記の例では `LastName`) を生成します。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-300">The `nameof` expression produces the unqualified name of its argument (`LastName` in the previous examples) even if you use the fully qualified name for the argument:</span></span>

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

<span data-ttu-id="bb9b3-301">この `nameof` 式では、`UXComponents.ViewModel.FirstName` ではなく、`FirstName` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-301">This `nameof` expression produces `FirstName`, not `UXComponents.ViewModel.FirstName`.</span></span>

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="bb9b3-302">Catch ブロックと Finally ブロックでの Await</span><span class="sxs-lookup"><span data-stu-id="bb9b3-302">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="bb9b3-303">C# 5 では、`await` 式を配置できる位置について、いくつかの制限がありました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-303">C# 5 had several limitations around where you could place `await` expressions.</span></span>
<span data-ttu-id="bb9b3-304">C# 6 では、そのうちの 1 つが解消され、</span><span class="sxs-lookup"><span data-stu-id="bb9b3-304">One of those has been removed in C# 6.</span></span> <span data-ttu-id="bb9b3-305">`await` を `catch` 式や `finally` 式で使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-305">You can now use `await` in `catch` or `finally` expressions.</span></span> 

<span data-ttu-id="bb9b3-306">catch や finally のブロックに await を追加すると、それらの処理方法が複雑になるように思えるかもしれないので、</span><span class="sxs-lookup"><span data-stu-id="bb9b3-306">The addition of await expressions in catch and finally blocks may appear to complicate how those are processed.</span></span> <span data-ttu-id="bb9b3-307">コード例で説明していきましょう。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-307">Let's add an example to discuss how this appears.</span></span> <span data-ttu-id="bb9b3-308">非同期メソッドでは、finally 句で await 式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-308">In any async method, you can use an await expression in a finally clause.</span></span>

<span data-ttu-id="bb9b3-309">C# 6 では、catch 式でも await を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-309">With C# 6, you can also await in catch expressions.</span></span> <span data-ttu-id="bb9b3-310">次に示すのは、ロギングのシナリオで特によく使用されるコードです。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-310">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="bb9b3-311">`catch` 句と `finally` 句の内部に `await` のサポートを追加するための実装詳細では、その動作と、同期コードの動作との整合性が保証されています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-311">The implementation details for adding `await` support inside `catch` and `finally` clauses ensures that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="bb9b3-312">`catch` または `finally` 句で実行されたコードがエラーをスローした場合、プログラムは次の包含ブロック内から適切な `catch` 句を検索します。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-312">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="bb9b3-313">現行の例外があった場合、その例外は失われます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-313">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="bb9b3-314">`catch` 句や `finally` 句で待機中の式についても、これと同じことが起こります。つまり、適切な `catch` が検索され、現行の例外がある場合は、その例外が失われます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-314">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="bb9b3-315">この動作を理由に、`catch` 句と `finally` 句は慎重に記述することが推奨されています (新しい例外が導入されないようにしてください)。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-315">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="index-initializers"></a><span data-ttu-id="bb9b3-316">インデックス初期化子</span><span class="sxs-lookup"><span data-stu-id="bb9b3-316">Index Initializers</span></span>

<span data-ttu-id="bb9b3-317">*インデックス初期化子*は、インデックスの使用によってコレクション初期化子の一貫性を高める 2 つの機能のうちの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-317">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="bb9b3-318">C# の以前のリリースでは、キーと値のペアを中かっこで囲むことで <xref:System.Collections.Generic.Dictionary%602> を含めたシーケンス スタイルのコレクションでのみ*コレクション初期化子*を使用できました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-318">In earlier releases of C#, you could use *collection initializers* only with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602> by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

<span data-ttu-id="bb9b3-319">C# 6 では、<xref:System.Collections.Generic.Dictionary%602> コレクションや、それと同様の型でも使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-319">Now, you can use them with <xref:System.Collections.Generic.Dictionary%602> collections and similar types.</span></span> <span data-ttu-id="bb9b3-320">新しい構文は、インデックスを使用したコレクションへの割り当てをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-320">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="bb9b3-321">この機能が加わったことにより、いくつかのバージョンでシーケンス コンテナーに使用されていたものと同様の構文を使用して、連想コンテナーを初期化できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-321">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="bb9b3-322">コレクション初期化子内の拡張 `Add` メソッド</span><span class="sxs-lookup"><span data-stu-id="bb9b3-322">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="bb9b3-323">コレクション初期化を使いやすくするもう 1 つの機能として、 *メソッドの*拡張メソッド`Add`を使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-323">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="bb9b3-324">この機能は、Visual Basic との同等性を確保するために追加されました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-324">This feature was added for parity with Visual Basic.</span></span> 

<span data-ttu-id="bb9b3-325">この機能は、新しい項目を意味的に追加するために、カスタム コレクション クラスで別の名前のメソッドを使用している場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-325">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

<span data-ttu-id="bb9b3-326">たとえば、次のような生徒のコレクションがあるとします。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-326">For example, consider a collection of students like this:</span></span>

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

<span data-ttu-id="bb9b3-327">`Enroll` メソッドは生徒を追加しますが、</span><span class="sxs-lookup"><span data-stu-id="bb9b3-327">The `Enroll` method adds a student.</span></span> <span data-ttu-id="bb9b3-328">`Add` パターンには従いません。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-328">But it doesn't follow the `Add` pattern.</span></span>
<span data-ttu-id="bb9b3-329">C# の以前のバージョンでは、コレクション初期化子は `Enrollment` オブジェクトには使用できませんした。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-329">In previous versions of C#, you could not use collection initializers with an `Enrollment` object:</span></span>

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

<span data-ttu-id="bb9b3-330">C# 6 ではこれが可能になりましたが、`Add` を `Enroll` にマップする拡張メソッドを作成した場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-330">Now you can, but only if you create an extension method that maps `Add` to `Enroll`:</span></span>

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

<span data-ttu-id="bb9b3-331">この機能を使用してできることは、拡張メソッドを作成することによって、コレクションに項目を追加する任意のメソッドを、`Add` という名前のメソッドにマップするということです。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-331">What you are doing with this feature is to map whatever method adds items to a collection to a method named `Add` by creating an extension method.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="bb9b3-332">オーバーロード解決の改善</span><span class="sxs-lookup"><span data-stu-id="bb9b3-332">Improved overload resolution</span></span>

<span data-ttu-id="bb9b3-333">最後に説明するのは、言われなければ気付かないかもしれない機能です。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-333">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="bb9b3-334">以前のバージョンの C# コンパイラでは、ラムダ式を使用した一部のメソッド呼び出しがあいまいと判断されるコンストラクトがありました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-334">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="bb9b3-335">たとえば、次のメソッドがあったとします。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-335">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="bb9b3-336">以前のバージョンの C# では、メソッド グループ構文を使用してこのメソッドを呼び出すと、エラーが発生していました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-336">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
<span data-ttu-id="bb9b3-337">以前のコンパイラでは、`Task.Run(Action)` と `Task.Run(Func<Task>())` を正しく区別することができませんでした。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-337">The earlier compiler could not distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="bb9b3-338">以前のバージョンでは、引数としてラムダ式を使用する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-338">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="bb9b3-339">C# 6 の コンパイラは、`Task.Run(Func<Task>())` のほうが適切であるということを正しく判断できます。</span><span class="sxs-lookup"><span data-stu-id="bb9b3-339">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>
