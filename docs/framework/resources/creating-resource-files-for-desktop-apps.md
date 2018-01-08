---
title: "デスクトップ アプリケーションに対するリソース ファイルの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resources files
- .resources files
- application resources, creating files
- resource files, creating
ms.assetid: 6c5ad891-66a0-4e7a-adcf-f41863ba6d8d
caps.latest.revision: "25"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 555ef705dc485462dc209b090e5cdbee98983681
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-resource-files-for-desktop-apps"></a><span data-ttu-id="f1d19-102">デスクトップ アプリケーションに対するリソース ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="f1d19-102">Creating Resource Files for Desktop Apps</span></span>
<span data-ttu-id="f1d19-103">リソース ファイルにリソース (文字列、イメージ、オブジェクト データなど) を追加して、アプリケーションで簡単に使用できるようにすることが可能です。</span><span class="sxs-lookup"><span data-stu-id="f1d19-103">You can include resources, such as strings, images, or object data, in resources files to make them easily available to your application.</span></span> <span data-ttu-id="f1d19-104">.NET Framework では、次の 5 つの方法でリソース ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-104">The .NET Framework offers five ways to create resources files:</span></span>  
  
-   <span data-ttu-id="f1d19-105">文字列リソースを格納するテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-105">Create a text file that contains string resources.</span></span> <span data-ttu-id="f1d19-106">[リソース ファイル ジェネレーター (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) を使用すると、テキスト ファイルをバイナリ リソース (.resources) ファイルに変換できます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-106">You can use [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to convert the text file into a binary resource (.resources) file.</span></span> <span data-ttu-id="f1d19-107">次に、そのバイナリ リソース ファイルを、言語コンパイラを使用してアプリケーションの実行可能ファイルまたはアプリケーション ライブラリに埋め込むか、[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用してサテライト アセンブリに埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-107">You can then embed the binary resource file  in an application executable or an application library by using a language compiler, or you can embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="f1d19-108">詳細については、「[テキスト ファイル内のリソース](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#TextFiles)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1d19-108">For more information, see the [Resources in Text Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#TextFiles) section.</span></span>  
  
-   <span data-ttu-id="f1d19-109">文字列、イメージ、またはオブジェクト データを格納する XML リソース (.resx) ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-109">Create an XML resource (.resx) file that contains string, image, or object data.</span></span> <span data-ttu-id="f1d19-110">[リソース ファイル ジェネレーター (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) を使用すると、.resx ファイルをバイナリ リソース (.resources) ファイルに変換できます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-110">You can use [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to convert the .resx file into a binary resource (.resources) file.</span></span> <span data-ttu-id="f1d19-111">次に、そのバイナリ リソース ファイルを、言語コンパイラを使用してアプリケーションの実行可能ファイルまたはアプリケーション ライブラリに埋め込むか、[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用してサテライト アセンブリに埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-111">You can then embed the binary resource file in an application executable or an application library by using a language compiler, or you can embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="f1d19-112">詳細については、「[.resx ファイル内のリソース](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResxFiles)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1d19-112">For more information, see the [Resources in .resx Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResxFiles) section.</span></span>  
  
-   <span data-ttu-id="f1d19-113"><xref:System.Resources> 名前空間の型を使用して、XML リソース (.resx) ファイルをプログラムによって作成します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-113">Create an XML resource (.resx) file programmatically by using types in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="f1d19-114">.resx ファイルを作成し、そのリソースを列挙して、特定のリソースを名前で取得することができます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-114">You can create a .resx file, enumerate its resources, and retrieve specific resources by name.</span></span> <span data-ttu-id="f1d19-115">詳細については、「[プログラムによる .resx ファイルの使用](../../../docs/framework/resources/working-with-resx-files-programmatically.md)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1d19-115">For more information, see the topic [Working with .resx Files Programmatically](../../../docs/framework/resources/working-with-resx-files-programmatically.md).</span></span>  
  
-   <span data-ttu-id="f1d19-116">バイナリ リソース (.resources) ファイルをプログラムによって作成します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-116">Create a binary resource (.resources) file programmatically.</span></span> <span data-ttu-id="f1d19-117">次に、そのファイルを、言語コンパイラを使用してアプリケーションの実行可能ファイルまたはアプリケーション ライブラリに埋め込むか、[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用してサテライト アセンブリに埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-117">You can then embed the file in an application executable or an application library by using a language compiler, or you can embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="f1d19-118">詳細については、「[.resources ファイル内のリソース](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1d19-118">For more information, see the [Resources in .resources Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) section.</span></span>  
  
-   <span data-ttu-id="f1d19-119">Visual Studio を使用してリソース ファイルを作成し、そのファイルをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-119">Use Visual Studio to create a resource file and include it in your project.</span></span> <span data-ttu-id="f1d19-120">Visual Studio には、リソースを追加、削除、および変更するためのリソース エディターがあります。</span><span class="sxs-lookup"><span data-stu-id="f1d19-120">Visual Studio provides a resource editor that lets you add, delete, and modify resources.</span></span> <span data-ttu-id="f1d19-121">コンパイル時には、リソース ファイルが自動的にバイナリ .resources ファイルに変換されて、アプリケーション アセンブリまたはサテライト アセンブリに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-121">At compile time, the resource file is automatically converted to a binary .resources file and embedded in an application assembly or satellite assembly.</span></span> <span data-ttu-id="f1d19-122">詳細については、「[Visual Studio のリソース ファイル](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1d19-122">For more information, see the [Resource Files in Visual Studio](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) section.</span></span>  
  
<a name="TextFiles"></a>   
## <a name="resources-in-text-files"></a><span data-ttu-id="f1d19-123">テキスト ファイル内のリソース</span><span class="sxs-lookup"><span data-stu-id="f1d19-123">Resources in Text Files</span></span>  
 <span data-ttu-id="f1d19-124">テキスト (.txt または .restext) ファイルを使用すると、文字列リソースのみ格納できます。文字列以外のリソースの場合は、.resx ファイルを使用するか、.resx ファイルをプログラムによって作成します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-124">You can use text (.txt or .restext) files to store string resources only; for non-string resources, use .resx files or create them programmatically.</span></span> <span data-ttu-id="f1d19-125">文字列リソースを格納するテキスト ファイルの形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f1d19-125">Text files that contain string resources have the following format:</span></span>  
  
```  
# This is an optional comment.  
name = value  
  
; This is another optional comment.  
name = value  
  
; The following supports conditional compilation if X is defined.  
#ifdef X  
name1=value1  
name2=value2  
#endif  
  
# The following supports conditional compilation if Y is undefined.  
#if !Y  
name1=value1  
name2=value2  
#endif  
```  
  
 <span data-ttu-id="f1d19-126">.txt ファイルと .restext ファイルのリソース ファイル形式は同じです。</span><span class="sxs-lookup"><span data-stu-id="f1d19-126">The resource file format of .txt and .restext files is identical.</span></span> <span data-ttu-id="f1d19-127">.restext ファイル拡張子は、テキスト ファイルがテキスト ベースのリソース ファイルであることをすぐに識別するために使用します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-127">The .restext file extension merely serves to make text files immediately identifiable as text-based resource files.</span></span>  
  
 <span data-ttu-id="f1d19-128">文字列リソースは、*name/value* のペアとして表示されます。ここで、*name* はリソースを識別する文字列です。*value* は、リソース取得メソッド (<xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> など) に *name* を渡すときに返されるリソース文字列です。</span><span class="sxs-lookup"><span data-stu-id="f1d19-128">String resources appear as *name/value* pairs, where *name* is a string that identifies the resource, and *value* is the resource string that is returned when you pass *name* to a resource retrieval method such as <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f1d19-129">*name* と *value* は等号 (=) で区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1d19-129">*name* and *value* must be separated by an equal sign (=).</span></span> <span data-ttu-id="f1d19-130">例:</span><span class="sxs-lookup"><span data-stu-id="f1d19-130">For example:</span></span>  
  
```  
FileMenuName=File  
EditMenuName=Edit  
ViewMenuName=View  
HelpMenuName=Help  
```  
  
> [!CAUTION]
>  <span data-ttu-id="f1d19-131">パスワード、セキュリティの配慮が必要な情報、プライベートなデータなどの格納には、リソース ファイルを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f1d19-131">Do not use resource files to store passwords, security-sensitive information, or private data.</span></span>  
  
 <span data-ttu-id="f1d19-132">空の文字列 (つまり、値が <xref:System.String.Empty?displayProperty=nameWithType> であるリソース) はテキスト ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-132">Empty strings (that is, a resource whose value is <xref:System.String.Empty?displayProperty=nameWithType>) are permitted in text files.</span></span> <span data-ttu-id="f1d19-133">例:</span><span class="sxs-lookup"><span data-stu-id="f1d19-133">For example:</span></span>  
  
```  
EmptyString=  
```  
  
 <span data-ttu-id="f1d19-134">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、テキスト ファイルで、`#ifdef`*symbol*... `#endif` および `#if !`*symbol*... `#endif` コンストラクトを使用した条件付きコンパイルをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f1d19-134">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], text files support conditional compilation with the `#ifdef`*symbol*... `#endif` and `#if !`*symbol*... `#endif` constructs.</span></span> <span data-ttu-id="f1d19-135">次に、`/define` スイッチと[リソース ファイル ジェネレーター (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) を使用して、シンボルを定義できます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-135">You can then use the `/define` switch with [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to define symbols.</span></span> <span data-ttu-id="f1d19-136">各リソースには、独自の `#ifdef`*symbol*... `#endif` または `#if !`*symbol*... `#endif` コンストラクトが必要です。</span><span class="sxs-lookup"><span data-stu-id="f1d19-136">Each resource requires its own `#ifdef`*symbol*... `#endif` or `#if !`*symbol*... `#endif` construct.</span></span> <span data-ttu-id="f1d19-137">`#ifdef` ステートメントを使用した場合、*シンボル*を定義した場合に関連付けられたリソースが .resources ファイルに追加されます。定義していない場合は追加されません。</span><span class="sxs-lookup"><span data-stu-id="f1d19-137">If you use an `#ifdef` statement and *symbol* is defined, the associated resource is included in the .resources file; otherwise, it is not included.</span></span> <span data-ttu-id="f1d19-138">`#if !` ステートメントを使用した場合、*シンボル*を定義していない場合に関連付けられたリソースが .resources ファイルに追加されます。定義した場合は追加されません。</span><span class="sxs-lookup"><span data-stu-id="f1d19-138">If you use an `#if !` statement and *symbol* is not defined, the associated resource is included in the .resources file; otherwise, it is not included.</span></span>  
  
 <span data-ttu-id="f1d19-139">テキスト ファイルでは、コメントはオプションです。コメントの行頭にはセミコロン (;) またはシャープ記号 (#) が付きます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-139">Comments are optional in text files and are preceded either by a semicolon (;) or by a pound sign (#) at the beginning of a line.</span></span> <span data-ttu-id="f1d19-140">コメントの行はファイル内の任意の場所に配置できます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-140">Lines that contain comments can be placed anywhere in the file.</span></span> <span data-ttu-id="f1d19-141">[リソース ファイル ジェネレーター (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) を使用して作成されたコンパイル済みの .resources ファイルにはコメントが含まれません。</span><span class="sxs-lookup"><span data-stu-id="f1d19-141">Comments are not included in a compiled .resources file that is created by using [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).</span></span>  
  
 <span data-ttu-id="f1d19-142">テキスト ファイル内の空白行はすべて空白と見なされて無視されます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-142">Any blank lines in the text files are considered to be white space and are ignored.</span></span>  
  
 <span data-ttu-id="f1d19-143">次の例では、`OKButton` および `CancelButton` という名前の 2 つの文字列リソースを定義します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-143">The following example defines two string resources named `OKButton` and `CancelButton`.</span></span>  
  
```  
#Define resources for buttons in the user interface.  
OKButton=OK  
CancelButton=Cancel  
```  
  
 <span data-ttu-id="f1d19-144">テキスト ファイルに *name* が重複して出現する場合、[リソース ファイル ジェネレーター (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) によって警告が表示され、2 番目の名前が無視されます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-144">If the text file contains duplicate occurrences of *name*, [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) displays a warning and ignores the second name.</span></span>  
  
 <span data-ttu-id="f1d19-145">*value* に改行文字を含めることはできませんが、C 言語形式のエスケープ文字で、改行を表す `\n` やタブを表す `\t` は使用できます。エスケープする場合は、円記号を含めることができます (たとえば、"\\\\")。</span><span class="sxs-lookup"><span data-stu-id="f1d19-145">*value* cannot contain new line characters, but you can use C language-style escape characters such as `\n` to represent a new line and `\t` to represent a tab. You can also include a backslash character if it is escaped (for example, "\\\\").</span></span> <span data-ttu-id="f1d19-146">空の文字列を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-146">In addition, an empty string is permitted.</span></span>  
  
 <span data-ttu-id="f1d19-147">リトル エンディアンまたはビッグ エンディアンのバイト順の UTF-8 エンコーディングまたは UTF-16 エンコーディングを使用して、テキスト ファイル形式でリソースを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1d19-147">You should save resources in text file format by using UTF-8 encoding or UTF-16 encoding in either little-endian or big-endian byte order.</span></span> <span data-ttu-id="f1d19-148">ただし、.txt ファイルを .resources ファイルに変換する[リソース ファイル ジェネレーター (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) では、ファイルを既定では UTF-8 として扱います。</span><span class="sxs-lookup"><span data-stu-id="f1d19-148">However, [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), which converts a .txt file to a .resources file, treats files as UTF-8 by default.</span></span> <span data-ttu-id="f1d19-149">UTF-16 でエンコードされたファイルを Resgen.exe が認識できるようにする場合は、ファイルの先頭に Unicode バイト順マーク (U+FEFF) を置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1d19-149">If you want Resgen.exe to recognize a file that was encoded using UTF-16, you must include a Unicode byte order mark (U+FEFF) at the beginning of the file.</span></span>  
  
 <span data-ttu-id="f1d19-150">テキスト形式のリソース ファイルを .NET Framework アセンブリに埋め込むには、[リソース ファイル ジェネレーター (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) を使用してファイルをバイナリ リソース (.resources) ファイルに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1d19-150">To embed a resource file in text format into a .NET Framework assembly, you must convert the file to a binary resource (.resources) file by using [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).</span></span> <span data-ttu-id="f1d19-151">次に、その .resources ファイルを、言語コンパイラを使用して .NET Framework アセンブリに埋め込むか、[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用してサテライト アセンブリに埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-151">You can then embed the .resources file in a .NET Framework assembly by using a language compiler or embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
 <span data-ttu-id="f1d19-152">次の例では、単純な "Hello World" コンソール アプリケーションで、GreetingResources.txt という名前のテキスト形式のリソース ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-152">The following example uses a resource file in text format named GreetingResources.txt for a simple "Hello World" console application.</span></span> <span data-ttu-id="f1d19-153">このテキスト ファイルでは、ユーザーに名前の入力を求め、あいさつ文を表示する 2 つの文字列 (`prompt` および `greeting`) を定義します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-153">The text file defines two strings, `prompt` and `greeting`, that prompt the user to enter his or her name and display a greeting.</span></span>  
  
```  
# GreetingResources.txt   
# A resource file in text format for a "Hello World" application.  
#  
# Initial prompt to the user.  
prompt=Enter your name:   
# Format string to display the result.  
greeting=Hello, {0}!  
```  
  
 <span data-ttu-id="f1d19-154">このテキスト ファイルは、次のコマンドを使用して .resources ファイルに変換できます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-154">The text file is converted to a .resources file by using the following command:</span></span>  
  
 <span data-ttu-id="f1d19-155">**resgen GreetingResources.txt**</span><span class="sxs-lookup"><span data-stu-id="f1d19-155">**resgen GreetingResources.txt**</span></span>  
  
 <span data-ttu-id="f1d19-156">次の例は、.resources ファイルを使用してユーザーにメッセージを表示するコンソール アプリケーションのソース コードを示しています。</span><span class="sxs-lookup"><span data-stu-id="f1d19-156">The following example shows the source code for a console application that uses the .resources file to display messages to the user.</span></span>  
  
 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]  
  
 <span data-ttu-id="f1d19-157">Visual Basic を使用している場合、ソース コード ファイル名が Greeting.vb であれば、埋め込みの .resources ファイルを含む実行可能ファイルを次のコマンドによって作成します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-157">If you are using Visual Basic, and the source code file is named Greeting.vb, the following command creates an executable file that includes the embedded .resources file:</span></span>  
  
 <span data-ttu-id="f1d19-158">**vbc greeting.vb /resource:GreetingResources.resources**</span><span class="sxs-lookup"><span data-stu-id="f1d19-158">**vbc greeting.vb /resource:GreetingResources.resources**</span></span>  
  
 <span data-ttu-id="f1d19-159">C# を使用している場合、ソース コード ファイル名が Greeting.cs であれば、埋め込みの .resources ファイルを含む実行可能ファイルを次のコマンドによって作成します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-159">If you are using C#, and the source code file is named Greeting.cs, the following command creates an executable file that includes the embedded .resources file:</span></span>  
  
 <span data-ttu-id="f1d19-160">**csc greeting.cs /resource:GreetingResources.resources**</span><span class="sxs-lookup"><span data-stu-id="f1d19-160">**csc greeting.cs /resource:GreetingResources.resources**</span></span>  
  
<a name="ResxFiles"></a>   
## <a name="resources-in-resx-files"></a><span data-ttu-id="f1d19-161">.resx ファイル内のリソース</span><span class="sxs-lookup"><span data-stu-id="f1d19-161">Resources in .resx Files</span></span>  
 <span data-ttu-id="f1d19-162">文字列リソースのみの格納が可能なテキスト ファイルとは異なり、XML リソース (.resx) ファイルは文字列、バイナリ データ (イメージ、アイコン、オーディオ クリップなど)、およびプログラム オブジェクトを格納できます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-162">Unlike text files, which can only store string resources, XML resource (.resx) files can store strings, binary data such as images, icons, and audio clips, and programmatic objects.</span></span> <span data-ttu-id="f1d19-163">.resx ファイルには、リソース エントリの形式を説明し、データの解析に使用する XML のバージョン管理情報を示す標準ヘッダーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-163">A .resx file contains a standard header, which describes the format of the resource entries and specifies the versioning information for the XML that is used to parse the data.</span></span> <span data-ttu-id="f1d19-164">XML ヘッダーの後に、リソース ファイル データが続きます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-164">The resource file data follows the XML header.</span></span> <span data-ttu-id="f1d19-165">各データ項目は、`data` タグに含まれる名前と値のペアで構成されます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-165">Each data item consists of a name/value pair that is contained in a `data` tag.</span></span> <span data-ttu-id="f1d19-166">`name` 属性ではリソース名を定義し、入れ子になった `value` タグにはリソースの値を格納します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-166">Its `name` attribute defines the resource name, and the nested `value` tag contains the resource value.</span></span> <span data-ttu-id="f1d19-167">文字列データの場合は、`value` タグに文字列が格納されます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-167">For string data, the `value` tag contains the string.</span></span>  
  
 <span data-ttu-id="f1d19-168">たとえば、次の `data` タグでは、`prompt` という名前の文字列リソースを定義します。このリソースの値は "Enter your name:" です。</span><span class="sxs-lookup"><span data-stu-id="f1d19-168">For example, the following `data` tag defines a string resource named `prompt` whose value is "Enter your name:".</span></span>  
  
```xml  
<data name="prompt" xml:space="preserve">  
  <value>Enter your name:</value>  
</data>  
```  
  
> [!WARNING]
>  <span data-ttu-id="f1d19-169">パスワード、セキュリティの配慮が必要な情報、プライベートなデータなどの格納には、リソース ファイルを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f1d19-169">Do not use resource files to store passwords, security-sensitive information, or private data.</span></span>  
  
 <span data-ttu-id="f1d19-170">リソース オブジェクトの場合は、リソースのデータ型を示す `type` 属性が **data** タグに含まれます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-170">For resource objects, the **data** tag includes a `type` attribute that indicates the data type of the resource.</span></span> <span data-ttu-id="f1d19-171">バイナリ データで構成されるオブジェクトの場合、`data` タグには、バイナリ データの `mimetype` 型を示す `base64` 属性も含まれます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-171">For objects that consist of binary data, the `data` tag also includes a `mimetype` attribute, which indicates the `base64` type of the binary data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1d19-172">すべての .resx ファイルは、指定された型のバイナリ データを生成し解析するために、バイナリのシリアル化フォーマッタを使用します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-172">All .resx files use a binary serialization formatter to generate and parse the binary data for a specified type.</span></span> <span data-ttu-id="f1d19-173">このため、オブジェクトのバイナリ シリアル化形式が互換性のない形式に変更されると、.resx ファイルは無効になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f1d19-173">As a result, a .resx file can become invalid if the binary serialization format for an object changes in an incompatible way.</span></span>  
  
 <span data-ttu-id="f1d19-174">次の例は、<xref:System.Int32> リソースおよびビットマップ イメージを含む .resx ファイルの一部を示しています。</span><span class="sxs-lookup"><span data-stu-id="f1d19-174">The following example shows a portion of a .resx file that includes an <xref:System.Int32> resource and a bitmap image.</span></span>  
  
```xml  
<data name="i1" type="System.Int32, mscorlib">  
  <value>20</value>  
</data>  
  
<data name="flag" type="System.Drawing.Bitmap, System.Drawing,     
    Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"   
    mimetype="application/x-microsoft.net.object.bytearray.base64">  
  <value>  
    AAEAAAD/////AQAAAAAAAAAMAgAAADtTeX…  
  </value>  
</data>  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="f1d19-175">.resx ファイルは定義されている形式の整形式 XML で構成する必要があるため、特に文字列以外のリソースが .resx ファイルに格納されている場合に、.resx ファイルを手動で操作することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="f1d19-175">Because .resx files must consist of well-formed XML in a predefined format, we do not recommend working with .resx files manually, particularly when the .resx files contain resources other than strings.</span></span> <span data-ttu-id="f1d19-176">その代わりに、Visual Studio には、.resx ファイルを作成および操作するための透過的なインターフェイスが用意されています。詳細については、「[Visual Studio のリソース ファイル](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1d19-176">Instead, Visual Studio provides a transparent interface for creating and manipulating .resx files; for more information, see the [Resource Files in Visual Studio](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) section.</span></span> <span data-ttu-id="f1d19-177">.resx ファイルは、プログラムによって作成および操作することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-177">You can also create and manipulate .resx files programmatically.</span></span> <span data-ttu-id="f1d19-178">詳細については、「[プログラムによる .resx ファイルの使用](../../../docs/framework/resources/working-with-resx-files-programmatically.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1d19-178">For more information, see [Working with .resx Files Programmatically](../../../docs/framework/resources/working-with-resx-files-programmatically.md).</span></span>  
  
<a name="ResourcesFiles"></a>   
## <a name="resources-in-resources-files"></a><span data-ttu-id="f1d19-179">.resources ファイル内のリソース</span><span class="sxs-lookup"><span data-stu-id="f1d19-179">Resources in .resources Files</span></span>  
 <span data-ttu-id="f1d19-180"><xref:System.Resources.ResourceWriter?displayProperty=nameWithType> クラスを使用すると、プログラムによってコードから直接、バイナリ リソース (.resources) ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-180">You can use the <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> class to programmatically create a binary resource (.resources) file directly from code.</span></span> <span data-ttu-id="f1d19-181">また、[リソース ファイル ジェネレーター (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) を使用して、テキスト ファイルまたは .resx ファイルから .resources ファイルを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-181">You can also use [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to create a .resources file from a text file or a .resx file.</span></span> <span data-ttu-id="f1d19-182">.resources ファイルには、文字列データに加えて、バイナリ データ (バイト配列) およびオブジェクト データを格納できます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-182">The .resources file can contain binary data (byte arrays) and object data in addition to string data.</span></span> <span data-ttu-id="f1d19-183">.resources ファイルをプログラムによって作成するには、次の手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="f1d19-183">Programmatically creating a .resources file requires the following steps:</span></span>  
  
1.  <span data-ttu-id="f1d19-184">一意のファイル名を付けて <xref:System.Resources.ResourceWriter> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-184">Create a <xref:System.Resources.ResourceWriter> object with a unique file name.</span></span> <span data-ttu-id="f1d19-185">そのためには、ファイル名またはファイル ストリームを <xref:System.Resources.ResourceWriter> クラス コンストラクターに指定します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-185">You can do this by specifying either a file name or a file stream to a <xref:System.Resources.ResourceWriter> class constructor.</span></span>  
  
2.  <span data-ttu-id="f1d19-186">ファイルに追加する名前付きリソースごとに <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> メソッドのオーバーロードの 1 つを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-186">Call one of the overloads of the <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> method for each named resource to add to the file.</span></span> <span data-ttu-id="f1d19-187">リソースには、文字列、オブジェクト、またはバイナリ データのコレクション (バイト配列) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-187">The resource can be a string, an object, or a collection of binary data (a byte array).</span></span>  
  
3.  <span data-ttu-id="f1d19-188"><xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> メソッドを呼び出してファイルにリソースを書き込み、<xref:System.Resources.ResourceWriter> オブジェクトを閉じます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-188">Call the <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> method to write the resources to the file and to close the <xref:System.Resources.ResourceWriter> object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1d19-189">パスワード、セキュリティの配慮が必要な情報、プライベートなデータなどの格納には、リソース ファイルを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f1d19-189">Do not use resource files to store passwords, security-sensitive information, or private data.</span></span>  
  
 <span data-ttu-id="f1d19-190">次の例では、6 つの文字列、1 つのアイコン、2 つのアプリケーション定義オブジェクト (2 つの `Automobile` オブジェクト) を格納する、CarResources.resources という名前の .resources ファイルをプログラムによって作成します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-190">The following example programmatically creates a .resources file named CarResources.resources that stores six strings, an icon, and two application-defined objects (two `Automobile` objects).</span></span> <span data-ttu-id="f1d19-191">この例で定義およびインスタンス化される `Automobile` クラスは、<xref:System.SerializableAttribute> 属性でタグ付けされます。これにより、バイナリのシリアル化フォーマッタによってクラスを永続化できます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-191">Note that the `Automobile` class, which is defined and instantiated in the example, is tagged with the <xref:System.SerializableAttribute> attribute, which allows it to be persisted by the binary serialization formatter.</span></span>  
  
 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]  
  
 <span data-ttu-id="f1d19-192">作成した .resources ファイルは、言語コンパイラの `/resource` スイッチを追加してランタイム実行可能ファイルまたはライブラリに埋め込むか、[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用してサテライト アセンブリに埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-192">After you create the .resources file, you can embed it in a run-time executable or library by including the language compiler's `/resource` switch, or embed it in a satellite assembly by using [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
<a name="VSResFiles"></a>   
## <a name="resource-files-in-visual-studio"></a><span data-ttu-id="f1d19-193">Visual Studio のリソース ファイル</span><span class="sxs-lookup"><span data-stu-id="f1d19-193">Resource Files in Visual Studio</span></span>  
 <span data-ttu-id="f1d19-194">Visual Studio プロジェクトにリソース ファイルを追加すると、Visual Studio のプロジェクト ディレクトリに .resx ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-194">When you add a resource file to your Visual Studio project, Visual Studio creates a .resx file in the project directory.</span></span> <span data-ttu-id="f1d19-195">Visual Studio には、文字列、イメージ、およびバイナリ オブジェクトを追加するためのリソース エディターがあります。</span><span class="sxs-lookup"><span data-stu-id="f1d19-195">Visual Studio provides resource editors that enable you to add strings, images, and binary objects.</span></span> <span data-ttu-id="f1d19-196">このエディターは静的データのみを処理するように設計されているので、プログラム オブジェクトを格納するために使用することはできません。オブジェクト データは、.resx ファイルまたは .resources ファイルにプログラムによって書き込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1d19-196">Because the editors are designed to handle static data only, they cannot be used to store programmatic objects; you must write object data to either a .resx file or to a .resources file programmatically.</span></span> <span data-ttu-id="f1d19-197">詳細については、「[プログラムによる .resx ファイルの使用](../../../docs/framework/resources/working-with-resx-files-programmatically.md)」のトピックおよび「[.resources ファイル内のリソース](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1d19-197">See the [Working with .resx Files Programmatically](../../../docs/framework/resources/working-with-resx-files-programmatically.md) topic and the [Resources in .resources Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) section for more information.</span></span>  
  
 <span data-ttu-id="f1d19-198">ローカライズされたリソースを追加する場合は、メイン リソース ファイルと同じルート ファイル名をそれらのリソースに指定し、ファイル名にリソースのカルチャを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1d19-198">If you are adding localized resources, you should give them the same root file name as the main resource file, and you should also designate their culture in the file name.</span></span> <span data-ttu-id="f1d19-199">たとえば、Resources.resx という名前のリソース ファイルを追加する場合に、英語 (米国) とフランス語 (フランス) の各カルチャ用にローカライズされたリソースを保持するには、Resources.en-US.resx および Resources.fr-FR.resx という名前のリソース ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-199">For example, if you add a resource file named Resources.resx, you might also create resource files named Resources.en-US.resx and Resources.fr-FR.resx to hold localized resources for the English (United States) and French (France) cultures, respectively.</span></span> <span data-ttu-id="f1d19-200">また、アプリケーションの既定のカルチャも指定しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1d19-200">You should also designate your application's default culture.</span></span> <span data-ttu-id="f1d19-201">この情報は、特定のカルチャ用にローカライズされたリソースが見つからない場合に、どのカルチャのリソースを使用するか決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-201">This is the culture whose resources are used if no localized resources for a particular culture can be found.</span></span> <span data-ttu-id="f1d19-202">既定のカルチャを指定するには、Visual Studio のソリューション エクスプローラーで、プロジェクト名を右クリックし、[アプリケーション] をポイントして、**[アセンブリ情報]** をクリックします。次に、**[ニュートラル言語]** ボックスの一覧で適切な言語/カルチャをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1d19-202">To specify the default culture, in Solution Explorer in Visual Studio, right-click the project name, point to Application, click **Assembly Information**, and select the appropriate language/culture in the **Neutral language** list.</span></span>  
  
 <span data-ttu-id="f1d19-203">コンパイル時に、Visual Studio ではまずプロジェクト内の .resx ファイルをバイナリ リソース (.resources) ファイルに変換して、プロジェクトの obj ディレクトリのサブディレクトリに格納します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-203">At compile time, Visual Studio first converts the .resx files in a project to binary resource (.resources) files and stores them in a subdirectory of the project's obj directory.</span></span> <span data-ttu-id="f1d19-204">ローカライズされたリソースが格納されていないリソース ファイルは、プロジェクトで生成されたメイン アセンブリに埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-204">Visual Studio embeds any resource files that do not contain localized resources in the main assembly that is generated by the project.</span></span> <span data-ttu-id="f1d19-205">ローカライズされたリソースがリソース ファイルに格納されている場合、Visual Studio では、各ローカライズ カルチャの個別のサテライト アセンブリにそのファイルを埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-205">If any resource files contain localized resources, Visual Studio embeds them in separate satellite assemblies for each localized culture.</span></span> <span data-ttu-id="f1d19-206">各サテライト アセンブリは、ローカライズ カルチャに対応する名前のディレクトリに格納します。</span><span class="sxs-lookup"><span data-stu-id="f1d19-206">It then stores each satellite assembly in a directory whose name corresponds to thelocalized culture.</span></span> <span data-ttu-id="f1d19-207">たとえば、ローカライズされた英語 (米国) リソースは、en-US サブディレクトリ内のサテライト アセンブリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f1d19-207">For example, localized English (United States) resources are stored in a satellite assembly in the en-US subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1d19-208">参照</span><span class="sxs-lookup"><span data-stu-id="f1d19-208">See Also</span></span>  
 <xref:System.Resources>  
 [<span data-ttu-id="f1d19-209">デスクトップ アプリケーションのリソース</span><span class="sxs-lookup"><span data-stu-id="f1d19-209">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)  
 [<span data-ttu-id="f1d19-210">リソースのパッケージ化と配置</span><span class="sxs-lookup"><span data-stu-id="f1d19-210">Packaging and Deploying Resources</span></span>](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
