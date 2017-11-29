---
title: "C# プログラムの構造 - C# 言語のツアー"
description: "C# プログラムの基本的な構造について説明します"
keywords: .NET .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 8d8f443f8458cd392c75e9787e612ca1cc3518c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="program-structure"></a><span data-ttu-id="80429-104">プログラムの構造</span><span class="sxs-lookup"><span data-stu-id="80429-104">Program Structure</span></span>

<span data-ttu-id="80429-105">C# における主要な組織的概念は、***プログラム***、***名前空間***、***型***、***メンバー***、および***アセンブリ***です。</span><span class="sxs-lookup"><span data-stu-id="80429-105">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="80429-106">C# プログラムは、1 つまたは複数のソース ファイルで構成されています。</span><span class="sxs-lookup"><span data-stu-id="80429-106">C# programs consist of one or more source files.</span></span> <span data-ttu-id="80429-107">プログラムは型を宣言します。型にはメンバーが含まれていて、複数の名前空間に編成することができます。</span><span class="sxs-lookup"><span data-stu-id="80429-107">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="80429-108">型の例には、クラスおよびインターフェイスがあります。</span><span class="sxs-lookup"><span data-stu-id="80429-108">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="80429-109">メンバーの例には、フィールド、メソッド、プロパティ、およびイベントがあります。</span><span class="sxs-lookup"><span data-stu-id="80429-109">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="80429-110">C# プログラムはコンパイルされると、物理的にアセンブリにパッケージ化されます。</span><span class="sxs-lookup"><span data-stu-id="80429-110">When C# programs are compiled, they are physically packaged into assemblies.</span></span> <span data-ttu-id="80429-111">アセンブリには通常、***アプリケーション***または***ライブラリ***のどちらかを実行するかに応じて、それぞれ `.exe` または `.dll` のファイル拡張子があります。</span><span class="sxs-lookup"><span data-stu-id="80429-111">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="80429-112">次の例では、`Acme.Collections` と呼ばれる名前空間で `Stack` と呼ばれるクラスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="80429-112">The example declares a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="80429-113">このクラスの完全修飾名は `Acme.Collections.Stack` です。</span><span class="sxs-lookup"><span data-stu-id="80429-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="80429-114">このクラスには複数のメンバーが含まれています: `top` という名前のフィールドが 1 つ、`Push` と `Pop` という名前のメソッドが合わせて 2 つ、そして `Entry` という名前の入れ子になったクラスです。</span><span class="sxs-lookup"><span data-stu-id="80429-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="80429-115">`Entry` クラスにはさらに、3 つのメンバーが含まれています: `next` という名前のフィールド、`data` という名前のフィールド、およびコンストラクターです。</span><span class="sxs-lookup"><span data-stu-id="80429-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="80429-116">例のソース コードが `acme.cs` のファイルに保存されていることを前提に、次のコマンド ラインをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="80429-116">Assuming that the source code of the example is stored in the file `acme.cs`, the command line</span></span>

```
csc /t:library acme.cs
```

<span data-ttu-id="80429-117">このコマンド ラインは例をライブラリ (`Main` エントリ ポイントがないコード) としてコンパイルし、`acme.dll` という名前のアセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="80429-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80429-118">上記の例では `csc` をコマンド ライン C# コンパイラとして使用します。</span><span class="sxs-lookup"><span data-stu-id="80429-118">The examples above use `csc` as the command line C# compiler.</span></span> <span data-ttu-id="80429-119">このコンパイラは Windows で実行可能です。</span><span class="sxs-lookup"><span data-stu-id="80429-119">This compiler is a windows executable.</span></span> <span data-ttu-id="80429-120">C# を他のプラットフォームでも使用するには、.NET Core のツールを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80429-120">To use C# across other platforms, you should use the tools for .NET Core.</span></span> <span data-ttu-id="80429-121">.NET Core エコシステムでは、`dotnet` CLI を使用してコマンド ラインのビルドを管理します。</span><span class="sxs-lookup"><span data-stu-id="80429-121">The .NET Core ecosystem uses the `dotnet` CLI to manage command line builds.</span></span> <span data-ttu-id="80429-122">これには、依存関係の管理、および C# コンパイラの呼び出しが含まれます。</span><span class="sxs-lookup"><span data-stu-id="80429-122">This includes managing dependencies, and invoking the C# compiler.</span></span> <span data-ttu-id="80429-123">.NET Core でサポートされているプラットフォームでのこれらのツールに関する完全な説明については、[こちらのチュートリアル](../../core/tutorials/using-with-xplat-cli.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80429-123">See [this tutorial](../../core/tutorials/using-with-xplat-cli.md) for a full description of those tools on the platforms supported by .NET Core.</span></span>

<span data-ttu-id="80429-124">アセンブリには実行可能なコードが中間言語 (IL) の形式で含まれていて、シンボル情報がメタデータの形式で含まれています。</span><span class="sxs-lookup"><span data-stu-id="80429-124">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="80429-125">アセンブリの IL コードは実行前に、.NET 共通言語ランタイムの Just-In-Time (JIT) コンパイラによって、プロセッサ固有のコードに自動的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="80429-125">Before it is executed, the IL code in an assembly is automatically converted to processor-specific code by the Just-In-Time (JIT) compiler of .NET Common Language Runtime.</span></span>

<span data-ttu-id="80429-126">アセンブリはコードとメタデータの両方を含む自己記述的な機能的単位であるため、`#include` ディレクティブおよびヘッダー ファイルが C# に含まれている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="80429-126">Because an assembly is a self-describing unit of functionality containing both code and metadata, there is no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="80429-127">特定のアセンブリに含まれているパブリックの型とメンバーは、単にプログラムのコンパイル中にそのアセンブリを参照することにより、C# プログラムで利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="80429-127">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="80429-128">たとえば、このプログラムでは `acme.dll` アセンブリの `Acme.Collections.Stack` クラスを使用しています。</span><span class="sxs-lookup"><span data-stu-id="80429-128">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="80429-129">プログラムが `example.cs` のファイルに格納されている場合、`example.cs` がコンパイルされると、acme.dll アセンブリはコンパイラの /r オプションを使用して参照できるようになります。</span><span class="sxs-lookup"><span data-stu-id="80429-129">If the program is stored in the file `example.cs`, when `example.cs` is compiled, the acme.dll assembly can be referenced using the compiler’s /r option:</span></span>

```
csc /r:acme.dll example.cs
```

<span data-ttu-id="80429-130">これにより `example.exe` という名前の実行可能なアセンブリが作成され、これが実行された場合に、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="80429-130">This creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```
100
10
1
```

<span data-ttu-id="80429-131">C# では、プログラムのソース テキストを複数のソース ファイルに保存することができます。</span><span class="sxs-lookup"><span data-stu-id="80429-131">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="80429-132">複数ファイルの C# プログラムがコンパイルされると、ソース ファイルはすべて同時に処理され、ソース ファイルは自由に相互を参照できるようになります。概念的には、ソース ファイルが処理される前に、すべて 1 つの大きいファイルに連結されるようなものです。</span><span class="sxs-lookup"><span data-stu-id="80429-132">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="80429-133">C# では事前宣言をする必要がありません。ごく一部の例外を除いて、宣言の順序は重要でないためです。</span><span class="sxs-lookup"><span data-stu-id="80429-133">Forward declarations are never needed in C# because, with very few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="80429-134">C# ではソース ファイルがパブリック型 1 つのみの宣言に制限されません。また、ソース ファイルの名前がソース ファイルで宣言された型に一致する必要もありません。</span><span class="sxs-lookup"><span data-stu-id="80429-134">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="80429-135">[前へ](index.md)
[次へ](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="80429-135">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
