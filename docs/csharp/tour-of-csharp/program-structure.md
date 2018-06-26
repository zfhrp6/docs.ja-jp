---
title: C# プログラムの構造 - C# 言語のツアー
description: C# プログラムの基本的な構造について説明します
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 9efd2542d449da5ddcd9d3170c2e598282a34c39
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34565752"
---
# <a name="program-structure"></a><span data-ttu-id="34d37-103">プログラムの構造</span><span class="sxs-lookup"><span data-stu-id="34d37-103">Program Structure</span></span>

<span data-ttu-id="34d37-104">C# における主要な組織的概念は、***プログラム***、***名前空間***、***型***、***メンバー***、および***アセンブリ***です。</span><span class="sxs-lookup"><span data-stu-id="34d37-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="34d37-105">C# プログラムは、1 つまたは複数のソース ファイルで構成されています。</span><span class="sxs-lookup"><span data-stu-id="34d37-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="34d37-106">プログラムは型を宣言します。型にはメンバーが含まれていて、複数の名前空間に編成することができます。</span><span class="sxs-lookup"><span data-stu-id="34d37-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="34d37-107">型の例には、クラスおよびインターフェイスがあります。</span><span class="sxs-lookup"><span data-stu-id="34d37-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="34d37-108">メンバーの例には、フィールド、メソッド、プロパティ、およびイベントがあります。</span><span class="sxs-lookup"><span data-stu-id="34d37-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="34d37-109">C# プログラムはコンパイルされると、物理的にアセンブリにパッケージ化されます。</span><span class="sxs-lookup"><span data-stu-id="34d37-109">When C# programs are compiled, they are physically packaged into assemblies.</span></span> <span data-ttu-id="34d37-110">アセンブリには通常、***アプリケーション***または***ライブラリ***のどちらかを実行するかに応じて、それぞれ `.exe` または `.dll` のファイル拡張子があります。</span><span class="sxs-lookup"><span data-stu-id="34d37-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="34d37-111">次の例では、`Acme.Collections` と呼ばれる名前空間で `Stack` と呼ばれるクラスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="34d37-111">The example declares a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="34d37-112">このクラスの完全修飾名は `Acme.Collections.Stack` です。</span><span class="sxs-lookup"><span data-stu-id="34d37-112">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="34d37-113">このクラスには複数のメンバーが含まれています: `top` という名前のフィールドが 1 つ、`Push` と `Pop` という名前のメソッドが合わせて 2 つ、そして `Entry` という名前の入れ子になったクラスです。</span><span class="sxs-lookup"><span data-stu-id="34d37-113">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="34d37-114">`Entry` クラスにはさらに、3 つのメンバーが含まれています: `next` という名前のフィールド、`data` という名前のフィールド、およびコンストラクターです。</span><span class="sxs-lookup"><span data-stu-id="34d37-114">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="34d37-115">例のソース コードが `acme.cs` のファイルに保存されていることを前提に、次のコマンド ラインをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="34d37-115">Assuming that the source code of the example is stored in the file `acme.cs`, the command line</span></span>

```
csc /t:library acme.cs
```

<span data-ttu-id="34d37-116">このコマンド ラインは例をライブラリ (`Main` エントリ ポイントがないコード) としてコンパイルし、`acme.dll` という名前のアセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="34d37-116">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34d37-117">上記の例では `csc` をコマンド ライン C# コンパイラとして使用します。</span><span class="sxs-lookup"><span data-stu-id="34d37-117">The examples above use `csc` as the command line C# compiler.</span></span> <span data-ttu-id="34d37-118">このコンパイラは Windows で実行可能です。</span><span class="sxs-lookup"><span data-stu-id="34d37-118">This compiler is a Windows executable.</span></span> <span data-ttu-id="34d37-119">C# を他のプラットフォームでも使用するには、.NET Core のツールを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34d37-119">To use C# across other platforms, you should use the tools for .NET Core.</span></span> <span data-ttu-id="34d37-120">.NET Core エコシステムでは、`dotnet` CLI を使用してコマンド ラインのビルドを管理します。</span><span class="sxs-lookup"><span data-stu-id="34d37-120">The .NET Core ecosystem uses the `dotnet` CLI to manage command line builds.</span></span> <span data-ttu-id="34d37-121">これには、依存関係の管理、および C# コンパイラの呼び出しが含まれます。</span><span class="sxs-lookup"><span data-stu-id="34d37-121">This includes managing dependencies, and invoking the C# compiler.</span></span> <span data-ttu-id="34d37-122">.NET Core でサポートされているプラットフォームでのこれらのツールに関する完全な説明については、[こちらのチュートリアル](../../core/tutorials/using-with-xplat-cli.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34d37-122">See [this tutorial](../../core/tutorials/using-with-xplat-cli.md) for a full description of those tools on the platforms supported by .NET Core.</span></span>

<span data-ttu-id="34d37-123">アセンブリには実行可能なコードが中間言語 (IL) の形式で含まれていて、シンボル情報がメタデータの形式で含まれています。</span><span class="sxs-lookup"><span data-stu-id="34d37-123">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="34d37-124">アセンブリの IL コードは実行前に、.NET 共通言語ランタイムの Just-In-Time (JIT) コンパイラによって、プロセッサ固有のコードに自動的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="34d37-124">Before it is executed, the IL code in an assembly is automatically converted to processor-specific code by the Just-In-Time (JIT) compiler of .NET Common Language Runtime.</span></span>

<span data-ttu-id="34d37-125">アセンブリはコードとメタデータの両方を含む自己記述的な機能的単位であるため、`#include` ディレクティブおよびヘッダー ファイルが C# に含まれている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="34d37-125">Because an assembly is a self-describing unit of functionality containing both code and metadata, there is no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="34d37-126">特定のアセンブリに含まれているパブリックの型とメンバーは、単にプログラムのコンパイル中にそのアセンブリを参照することにより、C# プログラムで利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="34d37-126">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="34d37-127">たとえば、このプログラムでは `acme.dll` アセンブリの `Acme.Collections.Stack` クラスを使用しています。</span><span class="sxs-lookup"><span data-stu-id="34d37-127">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="34d37-128">プログラムが `example.cs` のファイルに格納されている場合、`example.cs` がコンパイルされると、acme.dll アセンブリはコンパイラの /r オプションを使用して参照できるようになります。</span><span class="sxs-lookup"><span data-stu-id="34d37-128">If the program is stored in the file `example.cs`, when `example.cs` is compiled, the acme.dll assembly can be referenced using the compiler’s /r option:</span></span>

```
csc /r:acme.dll example.cs
```

<span data-ttu-id="34d37-129">これにより `example.exe` という名前の実行可能なアセンブリが作成され、これが実行された場合に、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="34d37-129">This creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```
100
10
1
```

<span data-ttu-id="34d37-130">C# では、プログラムのソース テキストを複数のソース ファイルに保存することができます。</span><span class="sxs-lookup"><span data-stu-id="34d37-130">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="34d37-131">複数ファイルの C# プログラムがコンパイルされると、ソース ファイルはすべて同時に処理され、ソース ファイルは自由に相互を参照できるようになります。概念的には、ソース ファイルが処理される前に、すべて 1 つの大きいファイルに連結されるようなものです。</span><span class="sxs-lookup"><span data-stu-id="34d37-131">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="34d37-132">C# では事前宣言をする必要がありません。ごく一部の例外を除いて、宣言の順序は重要でないためです。</span><span class="sxs-lookup"><span data-stu-id="34d37-132">Forward declarations are never needed in C# because, with very few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="34d37-133">C# ではソース ファイルがパブリック型 1 つのみの宣言に制限されません。また、ソース ファイルの名前がソース ファイルで宣言された型に一致する必要もありません。</span><span class="sxs-lookup"><span data-stu-id="34d37-133">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="34d37-134">[前へ](index.md)
[次へ](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="34d37-134">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
