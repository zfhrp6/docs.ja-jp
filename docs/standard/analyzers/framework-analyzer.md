---
title: .NET Security Analyzer - .NET
description: ".NET Framework Analyzer パッケージの .NET Security Analyzer を利用し、セキュリティ上のリスクを見つけ、対処する方法について説明します。"
keywords: .NET, .NET Core
author: billwagner
ms.author: billwagner
ms.date: 01/25/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.openlocfilehash: 06a387d72d06609182c8894dd874b241a5d7b69c
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/27/2018
---
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="01bd5-104">.NET Framework Analyzer</span><span class="sxs-lookup"><span data-stu-id="01bd5-104">The .NET Framework Analyzer</span></span>

<span data-ttu-id="01bd5-105">.NET Framework Analyzer を利用し、.NET Framework 基盤のアプリケーション コードに潜在する問題を発見できます。</span><span class="sxs-lookup"><span data-stu-id="01bd5-105">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="01bd5-106">このアナライザーは潜在的な問題を検出し、改善策を提案します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-106">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="01bd5-107">コードを書くとき、あるいは CI ビルドの一部として、このアナライザーは Visual Studio で対話的に動作します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-107">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="01bd5-108">開発のできるだけ早い段階で、プロジェクトにアナライザーを追加してください。</span><span class="sxs-lookup"><span data-stu-id="01bd5-108">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="01bd5-109">コードに潜む問題を見つけるのが早ければ早いほど、修正が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="01bd5-109">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="01bd5-110">ただし、開発サイクルのどの段階でも追加できます。</span><span class="sxs-lookup"><span data-stu-id="01bd5-110">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="01bd5-111">開発者は開発を続行しながら、アナライザーは既存コードの問題を見つけ、新しい問題に関する警告を出します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-111">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="01bd5-112">.NET Framework Analyzer をインストールし、構成する</span><span class="sxs-lookup"><span data-stu-id="01bd5-112">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="01bd5-113">.NET Security Analyzer は、それを実行するすべてのプロジェクトで、NuGet パッケージとしてインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="01bd5-113">The .NET Security Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="01bd5-114">1 人の開発者がそれをプロジェクトに追加すれば十分です。</span><span class="sxs-lookup"><span data-stu-id="01bd5-114">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="01bd5-115">アナライザー パッケージはプロジェクト依存関係であり、更新済みのソリューションが与えられると、あらゆる開発者のコンピューターで実行されます。</span><span class="sxs-lookup"><span data-stu-id="01bd5-115">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="01bd5-116">.NET Framework Analyzer は [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet パッケージで配布されます。</span><span class="sxs-lookup"><span data-stu-id="01bd5-116">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="01bd5-117">このパッケージは、.NET Framework に固有のアナライザーのみ提供します。これにはセキュリティ アナライザーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="01bd5-117">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="01bd5-118">多くの場合、[Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet パッケージが必要になります。</span><span class="sxs-lookup"><span data-stu-id="01bd5-118">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span> <span data-ttu-id="01bd5-119">FxCopAnalyzers 集合パッケージには、Framework.Analyzers パッケージに含まれているすべてのフレームワーク アナライザーと次のアナライザーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="01bd5-119">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>
- <span data-ttu-id="01bd5-120">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): .NET Standard API の一般的なガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-120">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="01bd5-121">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): アナライザー固有の .NET Core API を提供します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-121">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="01bd5-122">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): コメントなど、コードとして含まれているテキストのガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-122">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="01bd5-123">これをインストールするには、プロジェクトを右クリックし、"依存関係の管理" を選択します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-123">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="01bd5-124">NuGet エクスプローラーから、"NetFramework Analyzer" を探します。あるいは、"Fx Cop Analyzer" がよければそれを探します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-124">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="01bd5-125">ソリューションのすべてのプロジェクトで安定した最新のバージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="01bd5-125">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="01bd5-126">.NET Framework Analyzer を使用する</span><span class="sxs-lookup"><span data-stu-id="01bd5-126">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="01bd5-127">NuGet パッケージがインストールされたら、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="01bd5-127">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="01bd5-128">アナライザーは、コードベースで見つかった問題を報告します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-128">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="01bd5-129">問題は Visual Studio の [エラー一覧] ウィンドウに警告として表示されます。次の画像をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="01bd5-129">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![フレームワーク アナライザーによって報告される問題](./media/framework-analyzers-2.png)

<span data-ttu-id="01bd5-131">コードを記述しているとき、コードに潜在的な問題があれば、その部分に波線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="01bd5-131">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="01bd5-132">問題の上にカーソルを合わせると、問題の詳細と考えられる修正案が表示されます。次の画像をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="01bd5-132">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![フレームワーク アナライザーが見つけた問題の対話型報告](./media/framework-analyzers-1.png)

<span data-ttu-id="01bd5-134">アナライザーはソリューションのコードを調べ、問題があれば警告の一覧を出します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-134">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="01bd5-135">CA1058: 型は、一定の基本型を拡張することはできません</span><span class="sxs-lookup"><span data-stu-id="01bd5-135">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="01bd5-136">.NET Framework には、直接の派生元にしてはいけない型がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="01bd5-136">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span> 

<span data-ttu-id="01bd5-137">**カテゴリ:** デザイン</span><span class="sxs-lookup"><span data-stu-id="01bd5-137">**Category:** Design</span></span>

<span data-ttu-id="01bd5-138">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="01bd5-138">**Severity:** Warning</span></span>

<span data-ttu-id="01bd5-139">追加情報: [CA1058: 型は、一定の基本型を拡張することはできません](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="01bd5-139">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="01bd5-140">CA2153: 破損状態例外はキャッチしないでください</span><span class="sxs-lookup"><span data-stu-id="01bd5-140">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="01bd5-141">破損状態例外をキャッチすると、エラー (アクセス違反など) が隠され、結果的に実行状態に一貫性がなくなり、攻撃者にとってシステムが攻撃しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="01bd5-141">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="01bd5-142">その代わりに、より具体的な例外型セットをキャッチして処理するか、例外を再スローします。</span><span class="sxs-lookup"><span data-stu-id="01bd5-142">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="01bd5-143">**カテゴリ:** セキュリティ</span><span class="sxs-lookup"><span data-stu-id="01bd5-143">**Category:** Security</span></span>

<span data-ttu-id="01bd5-144">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="01bd5-144">**Severity:** Warning</span></span>

<span data-ttu-id="01bd5-145">追加情報: [## CA2153: 破損状態例外はキャッチしないでください](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="01bd5-145">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="01bd5-146">CA2229: シリアル化コンストラクターを実装します</span><span class="sxs-lookup"><span data-stu-id="01bd5-146">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="01bd5-147">アナライザーは、<xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装する型を作成すると、この警告を出します。ただし、必須のシリアル化コンストラクターを定義しません。</span><span class="sxs-lookup"><span data-stu-id="01bd5-147">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="01bd5-148">この規則違反を修正するには、シリアル化コンストラクターを実装します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-148">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="01bd5-149">シールされたクラスの場合、コンストラクターをプライベートにするか、プロテクトにします。</span><span class="sxs-lookup"><span data-stu-id="01bd5-149">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="01bd5-150">シリアル化コンストラクターには次のシグネチャがあります。</span><span class="sxs-lookup"><span data-stu-id="01bd5-150">The serialization constructor has the following signature:</span></span>

```csharp
public class MyItemType
{
    // The special constructor is used to deserialize values.
    public MyItemType(SerializationInfo info, StreamingContext context)
    {
        // implementation removed.
    }
}
```

<span data-ttu-id="01bd5-151">**カテゴリ:** 使用</span><span class="sxs-lookup"><span data-stu-id="01bd5-151">**Category:** Usage</span></span>

<span data-ttu-id="01bd5-152">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="01bd5-152">**Severity:** Warning</span></span>

<span data-ttu-id="01bd5-153">追加情報: [CA2229: シリアル化コンストラクターを実装します](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="01bd5-153">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="01bd5-154">CA2235: すべてのシリアル化不可能なフィールドを設定します</span><span class="sxs-lookup"><span data-stu-id="01bd5-154">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="01bd5-155">シリアル化できない型のインスタンス フィールドが、シリアル化できる型で宣言されています。</span><span class="sxs-lookup"><span data-stu-id="01bd5-155">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="01bd5-156">この警告を解決するには、そのフィールドを <xref:System.NonSerializedAttribute> で明示的にマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="01bd5-156">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="01bd5-157">**カテゴリ:** 使用</span><span class="sxs-lookup"><span data-stu-id="01bd5-157">**Category:** Usage</span></span>

<span data-ttu-id="01bd5-158">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="01bd5-158">**Severity:** Warning</span></span>

<span data-ttu-id="01bd5-159">追加情報: [CA2235: すべてのシリアル化不可能なフィールドを設定します](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="01bd5-159">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="01bd5-160">CA2237: ISerializable 型を Serializable に設定します</span><span class="sxs-lookup"><span data-stu-id="01bd5-160">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="01bd5-161">型が共通言語ランタイムでシリアル化できると認識されるようにするには、型を <xref:System.SerializableAttribute> 属性でマークする必要があります。型が <xref:System.Runtime.Serialization.ISerializable> インターフェイスの実装を通じてカスタムのシリアル化ルーチンを使用している場合でも、マークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="01bd5-161">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="01bd5-162">**カテゴリ:** 使用</span><span class="sxs-lookup"><span data-stu-id="01bd5-162">**Category:** Usage</span></span>

<span data-ttu-id="01bd5-163">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="01bd5-163">**Severity:** Warning</span></span>

<span data-ttu-id="01bd5-164">追加情報: [CA2237: ISerializable 型を Serializable に設定します](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="01bd5-164">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="01bd5-165">CA3075: XML の安全ではない DTD の処理</span><span class="sxs-lookup"><span data-stu-id="01bd5-165">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="01bd5-166">安全ではない <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> インスタンスを使用する場合、または外部エンティティ ソースを参照する場合、パーサーは信頼されていない入力を受け入れ、攻撃者に機密情報を漏えいしてしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="01bd5-166">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="01bd5-167">**カテゴリ:** セキュリティ</span><span class="sxs-lookup"><span data-stu-id="01bd5-167">**Category:** Security</span></span>

<span data-ttu-id="01bd5-168">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="01bd5-168">**Severity:** Warning</span></span>

<span data-ttu-id="01bd5-169">追加情報: [A3075: XML の安全ではない DTD 処理](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="01bd5-169">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>


### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="01bd5-170">CA5350: 脆弱な暗号アルゴリズムを使用しないでください</span><span class="sxs-lookup"><span data-stu-id="01bd5-170">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="01bd5-171">時間の経過と共に攻撃が高度になり、暗号アルゴリズムが弱体化します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-171">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="01bd5-172">この暗号アルゴリズムの型と用途によっては、暗号の力がさらに弱まり、攻撃者が暗号化メッセージを読んだり、改ざんしたり、電子署名を偽造したり、ハッシュしたコンテンツを改ざんしたり、その他の面でこのアルゴリズムを基礎とする暗号システムを攻撃したりすることを許します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-172">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="01bd5-173">暗号化には、AES アルゴリズムを利用します (AES-256、AES-192、AES-128 が許容されます)。キーの長さは 128 ビット以上にします。</span><span class="sxs-lookup"><span data-stu-id="01bd5-173">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="01bd5-174">ハッシュには、SHA-2 512、SHA-2 384、SHA-2 256 などの SHA-2 群のハッシュ関数を利用します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-174">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="01bd5-175">**カテゴリ:** セキュリティ</span><span class="sxs-lookup"><span data-stu-id="01bd5-175">**Category:** Security</span></span>

<span data-ttu-id="01bd5-176">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="01bd5-176">**Severity:** Warning</span></span>

<span data-ttu-id="01bd5-177">追加情報: [CA5350: 脆弱な暗号アルゴリズムを使用しないでください](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="01bd5-177">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="01bd5-178">CA5351 破られた暗号アルゴリズムを使用しないでください</span><span class="sxs-lookup"><span data-stu-id="01bd5-178">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="01bd5-179">コンピューターを利用してこのアルゴリズムを突破する攻撃が存在します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-179">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="01bd5-180">攻撃者は、本来守られるはずの暗号を突破できます。</span><span class="sxs-lookup"><span data-stu-id="01bd5-180">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="01bd5-181">この暗号アルゴリズムの型と用途によっては、攻撃者が暗号化メッセージを読んだり、改ざんしたり、電子署名を偽造したり、ハッシュしたコンテンツを改ざんしたり、その他の面でこのアルゴリズムを基礎とする暗号システムを攻撃したりすることを許します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-181">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="01bd5-182">暗号化には、AES アルゴリズムを利用します (AES-256、AES-192、AES-128 が許容されます)。キーの長さは 128 ビット以上にします。</span><span class="sxs-lookup"><span data-stu-id="01bd5-182">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="01bd5-183">ハッシュには、SHA512、SHA384、SHA256 などの SHA-2 群のハッシュ関数を利用します。</span><span class="sxs-lookup"><span data-stu-id="01bd5-183">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="01bd5-184">デジタル署名には、RSA か ECDSA を利用します。RSA の場合、キーの長さを 2048 ビット以上にします。ECDSA の場合、キーの長さを 256 ビット以上にします。</span><span class="sxs-lookup"><span data-stu-id="01bd5-184">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="01bd5-185">**カテゴリ:** セキュリティ</span><span class="sxs-lookup"><span data-stu-id="01bd5-185">**Category:** Security</span></span>

<span data-ttu-id="01bd5-186">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="01bd5-186">**Severity:** Warning</span></span>

<span data-ttu-id="01bd5-187">追加情報: [CA5351: 破られた暗号アルゴリズムを使用しないでください](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="01bd5-187">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span></span>


