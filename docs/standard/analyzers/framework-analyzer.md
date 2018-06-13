---
title: .NET Security Analyzer - .NET
description: .NET Framework Analyzer パッケージの .NET Security Analyzer を利用し、セキュリティ上のリスクを見つけ、対処する方法について説明します。
author: billwagner
ms.author: billwagner
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 904218c177ea45f82a73b4532ce3230af954aa85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574622"
---
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="72984-103">.NET Framework Analyzer</span><span class="sxs-lookup"><span data-stu-id="72984-103">The .NET Framework Analyzer</span></span>

<span data-ttu-id="72984-104">.NET Framework Analyzer を利用し、.NET Framework 基盤のアプリケーション コードに潜在する問題を発見できます。</span><span class="sxs-lookup"><span data-stu-id="72984-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="72984-105">このアナライザーは潜在的な問題を検出し、改善策を提案します。</span><span class="sxs-lookup"><span data-stu-id="72984-105">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="72984-106">コードを書くとき、あるいは CI ビルドの一部として、このアナライザーは Visual Studio で対話的に動作します。</span><span class="sxs-lookup"><span data-stu-id="72984-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="72984-107">開発のできるだけ早い段階で、プロジェクトにアナライザーを追加してください。</span><span class="sxs-lookup"><span data-stu-id="72984-107">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="72984-108">コードに潜む問題を見つけるのが早ければ早いほど、修正が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="72984-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="72984-109">ただし、開発サイクルのどの段階でも追加できます。</span><span class="sxs-lookup"><span data-stu-id="72984-109">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="72984-110">開発者は開発を続行しながら、アナライザーは既存コードの問題を見つけ、新しい問題に関する警告を出します。</span><span class="sxs-lookup"><span data-stu-id="72984-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="72984-111">.NET Framework Analyzer をインストールし、構成する</span><span class="sxs-lookup"><span data-stu-id="72984-111">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="72984-112">.NET Security Analyzer は、それを実行するすべてのプロジェクトで、NuGet パッケージとしてインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="72984-112">The .NET Security Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="72984-113">1 人の開発者がそれをプロジェクトに追加すれば十分です。</span><span class="sxs-lookup"><span data-stu-id="72984-113">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="72984-114">アナライザー パッケージはプロジェクト依存関係であり、更新済みのソリューションが与えられると、あらゆる開発者のコンピューターで実行されます。</span><span class="sxs-lookup"><span data-stu-id="72984-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="72984-115">.NET Framework Analyzer は [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet パッケージで配布されます。</span><span class="sxs-lookup"><span data-stu-id="72984-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="72984-116">このパッケージは、.NET Framework に固有のアナライザーのみ提供します。これにはセキュリティ アナライザーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="72984-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="72984-117">多くの場合、[Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet パッケージが必要になります。</span><span class="sxs-lookup"><span data-stu-id="72984-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span> <span data-ttu-id="72984-118">FxCopAnalyzers 集合パッケージには、Framework.Analyzers パッケージに含まれているすべてのフレームワーク アナライザーと次のアナライザーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="72984-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>
- <span data-ttu-id="72984-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): .NET Standard API の一般的なガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="72984-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="72984-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): アナライザー固有の .NET Core API を提供します。</span><span class="sxs-lookup"><span data-stu-id="72984-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="72984-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): コメントなど、コードとして含まれているテキストのガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="72984-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="72984-122">これをインストールするには、プロジェクトを右クリックし、"依存関係の管理" を選択します。</span><span class="sxs-lookup"><span data-stu-id="72984-122">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="72984-123">NuGet エクスプローラーから、"NetFramework Analyzer" を探します。あるいは、"Fx Cop Analyzer" がよければそれを探します。</span><span class="sxs-lookup"><span data-stu-id="72984-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="72984-124">ソリューションのすべてのプロジェクトで安定した最新のバージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="72984-124">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="72984-125">.NET Framework Analyzer を使用する</span><span class="sxs-lookup"><span data-stu-id="72984-125">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="72984-126">NuGet パッケージがインストールされたら、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="72984-126">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="72984-127">アナライザーは、コードベースで見つかった問題を報告します。</span><span class="sxs-lookup"><span data-stu-id="72984-127">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="72984-128">問題は Visual Studio の [エラー一覧] ウィンドウに警告として表示されます。次の画像をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="72984-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![フレームワーク アナライザーによって報告される問題](./media/framework-analyzers-2.png)

<span data-ttu-id="72984-130">コードを記述しているとき、コードに潜在的な問題があれば、その部分に波線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="72984-130">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="72984-131">問題の上にカーソルを合わせると、問題の詳細と考えられる修正案が表示されます。次の画像をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="72984-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![フレームワーク アナライザーが見つけた問題の対話型報告](./media/framework-analyzers-1.png)

<span data-ttu-id="72984-133">アナライザーはソリューションのコードを調べ、問題があれば警告の一覧を出します。</span><span class="sxs-lookup"><span data-stu-id="72984-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="72984-134">CA1058: 型は、一定の基本型を拡張することはできません</span><span class="sxs-lookup"><span data-stu-id="72984-134">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="72984-135">.NET Framework には、直接の派生元にしてはいけない型がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="72984-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span> 

<span data-ttu-id="72984-136">**カテゴリ:** デザイン</span><span class="sxs-lookup"><span data-stu-id="72984-136">**Category:** Design</span></span>

<span data-ttu-id="72984-137">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="72984-137">**Severity:** Warning</span></span>

<span data-ttu-id="72984-138">追加情報: [CA1058: 型は、一定の基本型を拡張することはできません](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="72984-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="72984-139">CA2153: 破損状態例外はキャッチしないでください</span><span class="sxs-lookup"><span data-stu-id="72984-139">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="72984-140">破損状態例外をキャッチすると、エラー (アクセス違反など) が隠され、結果的に実行状態に一貫性がなくなり、攻撃者にとってシステムが攻撃しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="72984-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="72984-141">その代わりに、より具体的な例外型セットをキャッチして処理するか、例外を再スローします。</span><span class="sxs-lookup"><span data-stu-id="72984-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="72984-142">**カテゴリ:** セキュリティ</span><span class="sxs-lookup"><span data-stu-id="72984-142">**Category:** Security</span></span>

<span data-ttu-id="72984-143">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="72984-143">**Severity:** Warning</span></span>

<span data-ttu-id="72984-144">追加情報: [## CA2153: 破損状態例外はキャッチしないでください](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="72984-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="72984-145">CA2229: シリアル化コンストラクターを実装します</span><span class="sxs-lookup"><span data-stu-id="72984-145">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="72984-146">アナライザーは、<xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装する型を作成すると、この警告を出します。ただし、必須のシリアル化コンストラクターを定義しません。</span><span class="sxs-lookup"><span data-stu-id="72984-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="72984-147">この規則違反を修正するには、シリアル化コンストラクターを実装します。</span><span class="sxs-lookup"><span data-stu-id="72984-147">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="72984-148">シールされたクラスの場合、コンストラクターをプライベートにするか、プロテクトにします。</span><span class="sxs-lookup"><span data-stu-id="72984-148">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="72984-149">シリアル化コンストラクターには次のシグネチャがあります。</span><span class="sxs-lookup"><span data-stu-id="72984-149">The serialization constructor has the following signature:</span></span>

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

<span data-ttu-id="72984-150">**カテゴリ:** 使用</span><span class="sxs-lookup"><span data-stu-id="72984-150">**Category:** Usage</span></span>

<span data-ttu-id="72984-151">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="72984-151">**Severity:** Warning</span></span>

<span data-ttu-id="72984-152">追加情報: [CA2229: シリアル化コンストラクターを実装します](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="72984-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="72984-153">CA2235: すべてのシリアル化不可能なフィールドを設定します</span><span class="sxs-lookup"><span data-stu-id="72984-153">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="72984-154">シリアル化できない型のインスタンス フィールドが、シリアル化できる型で宣言されています。</span><span class="sxs-lookup"><span data-stu-id="72984-154">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="72984-155">この警告を解決するには、そのフィールドを <xref:System.NonSerializedAttribute> で明示的にマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="72984-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="72984-156">**カテゴリ:** 使用</span><span class="sxs-lookup"><span data-stu-id="72984-156">**Category:** Usage</span></span>

<span data-ttu-id="72984-157">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="72984-157">**Severity:** Warning</span></span>

<span data-ttu-id="72984-158">追加情報: [CA2235: すべてのシリアル化不可能なフィールドを設定します](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="72984-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="72984-159">CA2237: ISerializable 型を Serializable に設定します</span><span class="sxs-lookup"><span data-stu-id="72984-159">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="72984-160">型が共通言語ランタイムでシリアル化できると認識されるようにするには、型を <xref:System.SerializableAttribute> 属性でマークする必要があります。型が <xref:System.Runtime.Serialization.ISerializable> インターフェイスの実装を通じてカスタムのシリアル化ルーチンを使用している場合でも、マークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="72984-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="72984-161">**カテゴリ:** 使用</span><span class="sxs-lookup"><span data-stu-id="72984-161">**Category:** Usage</span></span>

<span data-ttu-id="72984-162">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="72984-162">**Severity:** Warning</span></span>

<span data-ttu-id="72984-163">追加情報: [CA2237: ISerializable 型を Serializable に設定します](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="72984-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="72984-164">CA3075: XML の安全ではない DTD の処理</span><span class="sxs-lookup"><span data-stu-id="72984-164">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="72984-165">安全ではない <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> インスタンスを使用する場合、または外部エンティティ ソースを参照する場合、パーサーは信頼されていない入力を受け入れ、攻撃者に機密情報を漏えいしてしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="72984-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="72984-166">**カテゴリ:** セキュリティ</span><span class="sxs-lookup"><span data-stu-id="72984-166">**Category:** Security</span></span>

<span data-ttu-id="72984-167">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="72984-167">**Severity:** Warning</span></span>

<span data-ttu-id="72984-168">追加情報: [A3075: XML の安全ではない DTD 処理](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="72984-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>


### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="72984-169">CA5350: 脆弱な暗号アルゴリズムを使用しないでください</span><span class="sxs-lookup"><span data-stu-id="72984-169">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="72984-170">時間の経過と共に攻撃が高度になり、暗号アルゴリズムが弱体化します。</span><span class="sxs-lookup"><span data-stu-id="72984-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="72984-171">この暗号アルゴリズムの型と用途によっては、暗号の力がさらに弱まり、攻撃者が暗号化メッセージを読んだり、改ざんしたり、電子署名を偽造したり、ハッシュしたコンテンツを改ざんしたり、その他の面でこのアルゴリズムを基礎とする暗号システムを攻撃したりすることを許します。</span><span class="sxs-lookup"><span data-stu-id="72984-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="72984-172">暗号化には、AES アルゴリズムを利用します (AES-256、AES-192、AES-128 が許容されます)。キーの長さは 128 ビット以上にします。</span><span class="sxs-lookup"><span data-stu-id="72984-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="72984-173">ハッシュには、SHA-2 512、SHA-2 384、SHA-2 256 などの SHA-2 群のハッシュ関数を利用します。</span><span class="sxs-lookup"><span data-stu-id="72984-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="72984-174">**カテゴリ:** セキュリティ</span><span class="sxs-lookup"><span data-stu-id="72984-174">**Category:** Security</span></span>

<span data-ttu-id="72984-175">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="72984-175">**Severity:** Warning</span></span>

<span data-ttu-id="72984-176">追加情報: [CA5350: 脆弱な暗号アルゴリズムを使用しないでください](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="72984-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="72984-177">CA5351 破られた暗号アルゴリズムを使用しないでください</span><span class="sxs-lookup"><span data-stu-id="72984-177">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="72984-178">コンピューターを利用してこのアルゴリズムを突破する攻撃が存在します。</span><span class="sxs-lookup"><span data-stu-id="72984-178">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="72984-179">攻撃者は、本来守られるはずの暗号を突破できます。</span><span class="sxs-lookup"><span data-stu-id="72984-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="72984-180">この暗号アルゴリズムの型と用途によっては、攻撃者が暗号化メッセージを読んだり、改ざんしたり、電子署名を偽造したり、ハッシュしたコンテンツを改ざんしたり、その他の面でこのアルゴリズムを基礎とする暗号システムを攻撃したりすることを許します。</span><span class="sxs-lookup"><span data-stu-id="72984-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="72984-181">暗号化には、AES アルゴリズムを利用します (AES-256、AES-192、AES-128 が許容されます)。キーの長さは 128 ビット以上にします。</span><span class="sxs-lookup"><span data-stu-id="72984-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="72984-182">ハッシュには、SHA512、SHA384、SHA256 などの SHA-2 群のハッシュ関数を利用します。</span><span class="sxs-lookup"><span data-stu-id="72984-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="72984-183">デジタル署名には、RSA か ECDSA を利用します。RSA の場合、キーの長さを 2048 ビット以上にします。ECDSA の場合、キーの長さを 256 ビット以上にします。</span><span class="sxs-lookup"><span data-stu-id="72984-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="72984-184">**カテゴリ:** セキュリティ</span><span class="sxs-lookup"><span data-stu-id="72984-184">**Category:** Security</span></span>

<span data-ttu-id="72984-185">**重要度:** 警告</span><span class="sxs-lookup"><span data-stu-id="72984-185">**Severity:** Warning</span></span>

<span data-ttu-id="72984-186">追加情報: [CA5351: 破られた暗号アルゴリズムを使用しないでください](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="72984-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span></span>


