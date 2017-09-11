---
title: "-doc (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- FileProperties.BuildAction
- /doc
dev_langs:
- CSharp
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 58608c1301b2df3286c1f8a1de189f6256b19052
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="doc-c-compiler-options"></a><span data-ttu-id="78717-102">/doc (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="78717-102">/doc (C# Compiler Options)</span></span>
<span data-ttu-id="78717-103">**/doc** オプションを使用すると、XML ファイル内にドキュメント コメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="78717-103">The **/doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78717-104">構文</span><span class="sxs-lookup"><span data-stu-id="78717-104">Syntax</span></span>  
  
```console  
/doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="78717-105">引数</span><span class="sxs-lookup"><span data-stu-id="78717-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="78717-106">XML の出力ファイル。コンパイルのソース コード ファイルのコメントが入力されます。</span><span class="sxs-lookup"><span data-stu-id="78717-106">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78717-107">コメント</span><span class="sxs-lookup"><span data-stu-id="78717-107">Remarks</span></span>  
 <span data-ttu-id="78717-108">ソース コード ファイルで、次の項目の前にあるドキュメント コメントを処理し、XML ファイルに追加できます。</span><span class="sxs-lookup"><span data-stu-id="78717-108">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
-   <span data-ttu-id="78717-109">[クラス](../../../csharp/language-reference/keywords/class.md)、[デリゲート](../../../csharp/language-reference/keywords/delegate.md)、[インターフェイス](../../../csharp/language-reference/keywords/interface.md)などのユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="78717-109">Such user-defined types as a [class](../../../csharp/language-reference/keywords/class.md), [delegate](../../../csharp/language-reference/keywords/delegate.md), or [interface](../../../csharp/language-reference/keywords/interface.md)</span></span>  
  
-   <span data-ttu-id="78717-110">フィールド、[イベント](../../../csharp/language-reference/keywords/event.md)、[プロパティ](../../../csharp/programming-guide/classes-and-structs/using-properties.md)、メソッドなどのメンバー</span><span class="sxs-lookup"><span data-stu-id="78717-110">Such members as a field, [event](../../../csharp/language-reference/keywords/event.md), [property](../../../csharp/programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="78717-111">Main を含むソース コード ファイルが最初に XML に出力されます。</span><span class="sxs-lookup"><span data-stu-id="78717-111">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="78717-112">生成された .xml ファイルで [IntelliSense](/visualstudio/ide/using-intellisense) 機能を使用するには、サポートするアセンブリの名前と .xml ファイル名を同じにして、その .xml ファイルをアセンブリと同じディレクトリに置きます。</span><span class="sxs-lookup"><span data-stu-id="78717-112">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="78717-113">これで、アセンブリが Visual Studio プロジェクトで参照されると、.xml ファイルも同様に検出されます。</span><span class="sxs-lookup"><span data-stu-id="78717-113">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="78717-114">詳細については、[コード コメントの追加](/visualstudio/ide/supplying-xml-code-comments)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="78717-114">See [Supplying Code Comments](/visualstudio/ide/supplying-xml-code-comments) and for more information.</span></span>  
  
 <span data-ttu-id="78717-115">[/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) でコンパイルしない限り、`file` には \<assembly>\</assembly> タグが追加されます。コンパイルの出力ファイルのアセンブリ マニフェストを含むファイルの名前が指定されます。</span><span class="sxs-lookup"><span data-stu-id="78717-115">Unless you compile with [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78717-116">/doc オプションは、すべての入力ファイル (プロジェクトの設定で設定された場合、そのプロジェクト内のすべてのファイル) に適用されます。</span><span class="sxs-lookup"><span data-stu-id="78717-116">The /doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="78717-117">特定のファイルまたはコードの特定のセクションについて、ドキュメントのコメントに関する警告を無効にするには、[#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="78717-117">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="78717-118">コードのコメントからドキュメントを生成する方法については、「[ドキュメント コメント用の推奨タグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78717-118">See [Recommended Tags for Documentation Comments](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="78717-119">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="78717-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="78717-120">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="78717-120">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="78717-121">**[ビルド]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="78717-121">Click the **Build** tab.</span></span>  
  
3.  <span data-ttu-id="78717-122">**[XML ドキュメント ファイル]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="78717-122">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="78717-123">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="78717-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78717-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="78717-124">See Also</span></span>  
 <span data-ttu-id="78717-125">[C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="78717-125">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="78717-126">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="78717-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

