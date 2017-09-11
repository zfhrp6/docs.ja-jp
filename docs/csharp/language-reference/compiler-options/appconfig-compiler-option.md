---
title: "-appconfig (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /appconfig
dev_langs:
- CSharp
helpviewer_keywords:
- /appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: 26
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
ms.openlocfilehash: 2aede966f92af3c94f4591b68732dbdbf5a4c5c9
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="appconfig-c-compiler-options"></a><span data-ttu-id="e02a6-102">/appconfig (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="e02a6-102">/appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="e02a6-103">**/appconfig** コンパイラ オプションを利用すると、C# アプリケーションで、アセンブリのバインド時に共通言語ランタイム (CLR) にアセンブリのアプリケーション構成 (app.config) ファイルの場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e02a6-103">The **/appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e02a6-104">構文</span><span class="sxs-lookup"><span data-stu-id="e02a6-104">Syntax</span></span>  
  
```console  
/appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="e02a6-105">引数</span><span class="sxs-lookup"><span data-stu-id="e02a6-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="e02a6-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="e02a6-106">Required.</span></span> <span data-ttu-id="e02a6-107">アセンブリ バインド設定を含むアプリケーション構成ファイル。</span><span class="sxs-lookup"><span data-stu-id="e02a6-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e02a6-108">コメント</span><span class="sxs-lookup"><span data-stu-id="e02a6-108">Remarks</span></span>  
 <span data-ttu-id="e02a6-109">**/appconfig** の用途の 1 つは、1 つのアセンブリが特定の参照アセンブリの .NET Framework バージョンと .NET Framework for Silverlight バージョンの両方を同時に参照する必要がある高度なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="e02a6-109">One use of **/appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="e02a6-110">たとえば、WPF (Windows Presentation Foundation) で作成された XAML デザイナーにおいて、デザイナーのユーザー インターフェイスとして WPF デスクトップを参照すると共に、Silverlight に組み込まれている WPF のサブセットも参照する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="e02a6-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="e02a6-111">同じデザイナー アセンブリで両方のアセンブリにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e02a6-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="e02a6-112">既定では、この 2 つのアセンブリはアセンブリ バインディングで同等と見なされるため、別々に参照するとコンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e02a6-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="e02a6-113">**/appconfig** コンパイラ オプションを利用すると、`<supportPortability>` タグを利用して既定の動作を無効にする app.config ファイルの場所を指定できます。次の例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e02a6-113">The **/appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="e02a6-114">このコンパイラは、CLR のアセンブリ バインド ロジックにファイルの場所を渡します。</span><span class="sxs-lookup"><span data-stu-id="e02a6-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e02a6-115">Microsoft Build Engine (MSBuild) を利用してアプリケーションを構築する場合、プロパティ タグを .csproj ファイルに追加し、**/appconfig** コンパイラ オプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="e02a6-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **/appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="e02a6-116">プロジェクトに既に設定されている app.config ファイルを使用するには、プロパティ タグ `<UseAppConfigForCompiler>` を .csproj ファイルに追加し、その値を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="e02a6-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="e02a6-117">異なる app.config ファイルを指定するには、プロパティ タグ `<AppConfigForCompiler>` を追加し、その値をファイルの場所に設定します。</span><span class="sxs-lookup"><span data-stu-id="e02a6-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e02a6-118">例</span><span class="sxs-lookup"><span data-stu-id="e02a6-118">Example</span></span>  
 <span data-ttu-id="e02a6-119">.NET Framework と .NET Framework for Silverlight の両方の実装に存在する .NET Framework アセンブリについて、その両方の実装をアプリケーションで参照できるようにする app.config ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e02a6-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="e02a6-120">**/appconfig** コンパイラ オプションにより、この app.config ファイルの場所が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e02a6-120">The **/appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e02a6-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="e02a6-121">See Also</span></span>  
 <span data-ttu-id="e02a6-122">[.NET Framework アセンブリ統合の概要](http://msdn.microsoft.com/en-us/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48) </span><span class="sxs-lookup"><span data-stu-id="e02a6-122">[.NET Framework Assembly Unification Overview](http://msdn.microsoft.com/en-us/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48) </span></span>  
 <span data-ttu-id="e02a6-123">[\<supportPortability> 要素](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md) </span><span class="sxs-lookup"><span data-stu-id="e02a6-123">[\<supportPortability> Element](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md) </span></span>  
 [<span data-ttu-id="e02a6-124">アルファベット順の C# コンパイラ オプションの一覧</span><span class="sxs-lookup"><span data-stu-id="e02a6-124">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)

